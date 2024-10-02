+++
title = "fazendo o jogo da cobrinha."
date = 2023-06-06
+++

conforme eu fui aprendendo a programar em rust, eu senti vontade de abranger meus conhecimentos para diversas áreas relacionadas à programação. uma delas foi o desenvolvimento de jogos. por mais que existam diversas engines para montar um jogo e eu tenha uma vontade enorme de experimentar o [gdextension](https://godotengine.org/article/introducing-gd-extensions/) do godot, eu decidi programar meu jogo nativamente usando a biblioteca [sdl2](https://www.libsdl.org/).

é importante ressaltar: eu não tenho experiência alguma com desenvolvimento e design de jogos. por causa disso, eu decidi que deveria começar com algo simples. e qual jogo pode ser mais simples do que o jogo da cobrinha?
# organizando o estado
todos os dados do jogo serão definidos em um objeto. porém, antes de descrevê-lo, é necessário entender como o ambiente do jogo será distribuído: uma grade. cada espaço da grade é definido por duas coordenadas, e pode ser ocupado por apenas um elemento.

o tamanho da grade será definido como 40 de largura por 30 de altura.

```rust
const SIZE: (u32, u32) = (40, 30);
```

na prática, teremos três elementos, cada um sendo abstraído no contexto do jogo: o ponto de origem que será controlado — a cabeça da cobra; um objetivo — sua comida; e os segmentos que aumentam, atrás dela, conforme os pontos são obtidos — seu corpo.

temos a seguinte definição:

```rust
struct Snake {
    head: (u32, u32),
    body: Vec<(u32, u32)>,
    food: (u32, u32),
}
```

para o jogo atualizar seu estado, é necessário que ele combine seu estado atual com uma entrada para gerar o estado seguinte. isso é chamado de loop de jogo.

nesse caso: se a cobrinha receber um comando de movimento, o próximo estado utilizará a posição atual para calcular a posição seguinte, lidando com quaisquer consequências que surgirão. se a cabeça da cobra encontrar sua comida, ela aumentará de tamanho. se a cabeça da cobra colidir com seu corpo, o jogo acabará.
# a lógica e o loop
a primeira etapa de um loop é decidir o intervalo de tempo entre os estados. nesse caso, o intervalo diminuirá para o jogo acelerar conforme a pontuação. para isso, eu usei uma função afim que utiliza como entrada a área da grade, o tamanho da cobrinha e duas constantes: o intervalo máximo e mínimo, em milissegundos.

```rust
const TIME: (i32, i32) = (500, 200);
```

```rust
fn update_time(&mut self) {
    let time  = ((TIME.1 - TIME.0) * self.body.len() as i32 / (SIZE.0 * SIZE.1) as i32) + TIME.0;
    self.wait_time = time as u64;
}
```

no final do loop, essa função espera a passagem do tempo:

```rust
std::thread::sleep(Duration::from_millis(game.wait_time));
```

a outra dependência utilizada no projeto é a biblioteca [nanorand](https://crates.io/crates/nanorand), que me permite gerar números aleatórios. isso é importante porque as comidinhas devem aparecer em lugares aleatórios. assim, eu pude escrever um método para determinar um espaço aleatório na grade e outro para tentar posicionar uma comidinha. o método só terá sucesso caso o espaço esteja vazio.

```rust
fn gen_pos() -> (u32, u32) {
    let mut rng = WyRand::new();
    let x = rng.generate_range(0..SIZE.0);
    let y = rng.generate_range(0..SIZE.1);
    (x, y)
}
fn spawn_food(&mut self) {
    let mut food;
    loop {
        food = Snake::gen_pos();
        if !self.body.contains(&food) && food != self.head {
            break
        }
    }
    self.food = food;
}
```
# entrada de comandos
uma das partes mais importantes do loop do jogo é a entrada de comandos. no caso desse jogo, é necessário controlar a direção na qual a cobrinha se direciona. isso será feito com as setinhas do teclado.

para organizar a variação de direção da cobrinha, será criado um `enum`. assim podemos salvar sua direção:

```rust
enum Direction {
    Up,
    Down,
    Left,
    Right,
}
```

```rust
struct Snake {
    head: (u32, u32),
    body: Vec<(u32, u32)>,
    food: (u32, u32),
    direction: Direction,
}
```

a biblioteca sdl2 possui um objeto que, na minha implementação, salvará a última tecla pressionada. essa será mapeada à nova direção da cobrinha apenas se não for oposta à direção anterior. além disso, o evento de terminar o jogo deve ser adicionado caso o jogador feche a janela.

```rust
loop {
    let mut direction = None;
    for event in event_pump.poll_iter() {
        match event {
            Event::KeyDown {
                keycode: Some(Keycode::Up),
                ..
            } => {
                if game.direction != Direction::Down {
                    direction = Some(Direction::Up);
                }
            }
            Event::KeyDown {
                keycode: Some(Keycode::Down),
                ..
            } => {
                if game.direction != Direction::Up {
                    direction = Some(Direction::Down);
                }
            }
            Event::KeyDown {
                keycode: Some(Keycode::Left),
                ..
            } => {
                if game.direction != Direction::Right {
                    direction = Some(Direction::Left);
                }
            }
            Event::KeyDown {
                keycode: Some(Keycode::Right),
                ..
            } => {
                if game.direction != Direction::Left {
                    direction = Some(Direction::Right);
                }
            }
            Event::Quit { .. } => return,
            _ => {}
        }
    }
    
    if let Some(value) = direction {
        game.direction = value;
    }
}
```

e em seguida essa entrada será traduzida em movimento, porém antes é necessário que todo o corpo se locomova na direção da cabeça. isso é feito removendo seu último segmento e criando outro na nova posição:

```rust
if game.body.last().is_some() {
    game.body.pop();
    game.body.insert(0, game.head)
}

match game.direction {
    Direction::Up => {
        if game.head.1 == 0 {
            game.head = (game.head.0, SIZE.1 - 1)
        } else {
            game.head = (game.head.0, game.head.1 - 1)
        };
    }
    Direction::Down => {
        if game.head.1 == SIZE.1 - 1 {
            game.head = (game.head.0, 0)
        } else {
            game.head = (game.head.0, game.head.1 + 1)
        };
    }
    Direction::Left => {
        if game.head.0 == 0 {
            game.head = (SIZE.0 - 1, game.head.1)
        } else {
            game.head = (game.head.0 - 1, game.head.1)
        };
    }
    Direction::Right => {
        if game.head.0 == SIZE.0 - 1 {
            game.head = (0, game.head.1)
        } else {
            game.head = (game.head.0 + 1, game.head.1)
        };
    }
}
```

após calcular esse movimento, podemos, finalmente, concluir o loop:

```rust
if game.body.contains(&game.head) {
    return
}

if game.head == game.food {
    game.body.push(game.head);
    game.update_time();
    game.spawn_food();
}
```
# exibindo os gráficos
agora pode-se escrever a função principal. usando a biblioteca, deve-se criar uma tela que deve ser atualizada para exibir os gráficos do jogo:

```rust
fn main() {
    let sdl_context = sdl2::init().unwrap();
    let video = sdl_context.video().unwrap();

    let window = video
        .window("minhoca", SIZE.0 * 20, SIZE.1 * 20)
        .position_centered()
        .build()
        .unwrap();

    let mut canvas = window.into_canvas().present_vsync().build().unwrap();

    let mut event_pump = sdl_context.event_pump().unwrap();

    let mut game = Snake::new();

    loop {
        // ...
    }
}
```

em seguida, pode-se adicionar ao loop do jogo uma sequência de preenchimento de todos os elementos na grade. é importante lembrar de limpar a tela:

```rust
canvas.set_draw_color(Color::GRAY);
canvas.clear();

canvas.set_draw_color(Color::GREEN);
canvas.fill_rect(rect_from_pos(game.head)).unwrap();

for x in &game.body {
    canvas.fill_rect(rect_from_pos(*x)).unwrap();
}

canvas.set_draw_color(Color::RED);
canvas.fill_rect(rect_from_pos(game.food)).unwrap();

canvas.present();
```

aqui entra uma função auxiliar que transforma as posições dadas em retângulos na tela:

```rust
fn rect_from_pos(x: (u32, u32)) -> Rect {
    Rect::new(x.0 as i32 * 20, x.1 as i32 * 20, 20, 20)
}
```

{{ picture( name="screenshot", alt="captura de tela do jogo: alguns quadrados verdes na horizontal curvando-se em direção a um quadrado vermelho. representam a cobrinha indo à comidinha." ) }}

o código do projeto está disponível [aqui](https://github.com/derspyy/snake).

e para quem leu até o fim, um bônus: [nimhoca](https://github.com/derspyy/nimhoca); o projeto inteiro reescrito em nim.
