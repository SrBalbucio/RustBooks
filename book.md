# Introdução
Este doc é a versão em Português Brasileiro do Rust Book, por conveniência este doc não está ao pé da letra, portanto espere alguns tópicos eliminados ou transcritos para dentro de outros, além de dicas e exemplos extras. <br><br>Com tudo isso em mente podemos começar a navegar pelo mundo Rust!

# 1.0 - Início
Como havia dito acima, alguns tópicos foram arrancados por conveniência e um deles é o "Como instalar" que ficaria bem aqui. 
Se você ainda não tem o Rust instalado por favor visite este [tópico](https://doc.rust-lang.org/book/ch01-01-installation.html) 
## 1.1 - Hello World
Com Rust instalado é hora de criarmos nosso primeiro programa, o famoso "Hello World", tradicional passo inicial ao aprender uma nova linguagem de programação.
<br>
### Criando o diretório do Projeto:
Para começarmos a criar os arquivos do projeto precisamos primeiro criar a pasta onde eles serão armazenados.<br>
Para armazenar todos os projetos deste doc criaremos uma pasta chamada ``RustProjects``, porém cada projeto terá usa pasta separada dentro do ``RustProjects``.
<br>
<br>
Abra o CMD e digite:
```
mkdir ~/RustProjects
cd ~/RustProjects
```
Com a pasta ``RustProjects`` criada já podemos criar uma nova pasta dentro dela para o nosso primeiro projeto HelloWorld. Usaremos justamente o nome do projeto na pasta.
<br><br>
Abra o CMD e digite:
```
mkdir hello_world
cd hello_world
```
### Escrevendo e executando um programa:
Todos os arquivos Rust terminam em ``.rs``, ou seja, tem como extensão ``.rs``, ao criar um arquivo Rust se atente para não criar arquivos com nome contendo pulos/spaces (exemplo: hello world.rs, substitua por hello_world.rs).
Com isso em mente vamos criar o nosso primeiro arquivo Rust, o ``main.rs`` e dentro dele vamos adicionar o seguinte código:
```rust
fn main(){
    println!("Hello, world!");
}
```
Salve o arquivo com o código e vamos rodar para ver o que aparece.
No CMD digite:
```
rustc main.rs
./main
Hello, world!
```
Parabéns, você criou com sucesso o seu primeiro programa em Rust, mas você entendeu o que aconteceu aqui?
### Anatomia de programas em Rust
Quebrando esse código em partes temos a primeira peça do quebra cabeça, a função ``main``:
```rust
fn main(){
}
```
A função main é especial, é nela que o primeiro código é executado em um programa Rust. Neste caso a função main não tem parametros e nem retornos. Caso a função tivesse parametros eles entrariam no ``()``.
O corpo da função é definido pela ``{}``, portanto todo código dessa função deve estar dentro das chaves.
<br>
No corpo da nossa função ``main`` tinha o seguinte código:
```rust
println!("Hello, world!");
```
Esta linha de código faz todo trabalho do nosso programa HelloWorld: Ela imprime um texto na tela.
<br>
Há alguns detalhes importantes a se prestar atenção aqui:
- O estilo do Rust é recuar quatros espaços invés de uma guia tradicional.
- O ``println!`` é uma macro do Rust, se fosse uma função não teria o ``!``, mas falaremos de macros mais pra frente. Apenas lembre-se que isto é uma macro.
- Passamos uma String (texto) como parametro para o ``println!`` e por isso ele imprimiu ``Hello, world!``.
- Ao fim da linha adicionamos ``;`` para dizer que a nossa linha/expressão acabou e está pronta para vir outra. A maioria das linhas em Rust terminam em ``;``.
### Executar e compilar são passos diferentes
Antes de executar um programa é necessário compilar ele. A máquina não entende o código visual que programamos, por isso compilamos ele para transformá-lo em código binário executável para máquina.
<br>
O comando para fazer isso é o ``rustc``. Para compilar um arquivo Rust basta informar o seu nome de origem no command line e executar, como demonstrado abaixo:
```
rustc main.rs
```
Se tiver conhecimento de C/C++ deve ter percebido que é bem parecido ao ``clang`` e o ``gcc``.
<br>
Se você executar ``ls`` em Linux ou Mac você verá o arquivo original .rs e o arquivo executável sem extensão.
<br>
Se você executar ``dir /B`` em Windows você verá o arquivo original .rs, o arquivo executável com extensão .exe e o arquivo de depuração finalizado em .pdb.
<br>
<br>
Na próxima etapa aprenderemos a usar o Cargo.
## 1.2 - Seja bem-vindo, Cargo!
O Cargo é o gerenciador de dependências e builder do Rust. Ele é a ferramenta que nos ajuda a gerenciar o projeto, baixando e construindo bibliotecas e código.
<br>
Por enquanto não foi necessário o uso de bibliotecas, porém quando avançarmos nos projetos precisaremos usar algumas.
<br>
Como praticamente todos os projetos em Rust usam o Cargo, vou assumir que você também tem o Cargo instalado. Se você instalou o Rust por meios oficiais ele já deve vir instalado.
<br>
Para saber se o Cargo está instalado e ver a versão do mesmo digite no CMD o seguinte comando:
```
cargo --version
```
Se uma mensagem informando a versão for exibida estamos prontos para continuar, se não retorne a instalação.
### Criando um projeto com o Cargo
Criar projetos com o Cargo é consideravelmente simples e rápido. Vá para o seu diretório de Projetos e use o comando abaixo para dar progresso a nossos estudos:
```
cargo new hello_cargo
cd hello_cargo
```
O Cargo automaticamente cria a pasta e os arquivos necessários para o projeto.
<br>
Além disso o Cargo também já cria um repositório Git para você, caso ele já não exista, facilitando ainda mais a criação de projetos em Rust.
> Nota: Se você preferir adicionar um repositório Git mesmo que já haja um no diretório de origem use ``cargo new --vcs=git``!

> Importante: O Git é um sistema de controle de versão muito comum, mas você também pode substituir ele ou remover a funcionalidade usando o subcomando ``--vcs`` no ``cargo new``!

> Importante: Usando o comando ``cargo new --help`` você vê mais informações sobre o comando e suas opções.

Um dos arquivos criados pelo Cargo é o ``Cargo.toml``, abra ele no seu editor preferido e vamos conferir o que temos nele.
<br>

Ao abrir o arquivo você deve ver algo parecido com:

```
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

O arquivo contém seções de configuração do seu pacote. Cada seção é determinada por um cabeçalho, como ocorre na primeira linha ``[package]``, a seção que configura o pacote/projeto atual.
As próximas trés linhas após o cabeçalho ``[package]`` define o nome, versão e edição do Rust do pacote.
<br><br>
A próxima seção é a de dependências, com cabeçalho ``[dependencies]``, em Rust as depedências são referidas como ``crates``. Neste projeto não precisaremos mexer nesta seção.
<br><br>
Agora que você viu o arquivo de configuração do Cargo, vamos ver o nosso código fonte gerado.
Abra o arquivo gerado pelo Cargo em ``src/main.rs``:
```rust
fn main() {
    println!("Hello, world!");
}
```
E temos aqui o nosso Hello World gerado pelo Cargo automaticamente.
<br><br>
O Cargo assume que todos seus arquivos ``.rs`` estão dentro da pasta ``src``, afim de melhorar a organização do projeto. Fora dele, dentro do diretório origem deve ficar apenas arquivos README, licenças, arquivos de configuração (como o ``Cargo.toml``) e afins.

> Nota: É possível converter um projeto sem o Cargo para um com, basta criar uma pasta ``src``, mover todos os arquivos de código para dentro e criar um ``Cargo.toml`` adequado para o seu pacote.

### Compilando e executando com Cargo
Compilar com cargo também é uma tarefa simples. No CMD digite o seguinte comando para compilar o projeto:
```
cargo build
```
Este comando invés de jogar o arquivo executável no diretório de origem ele move o arquivo para ``target/debug/hello_cargo``.
Portanto para executar basta usar o seguinte comando em Linux e Mac: ``/target/debug/hello_cargo`` e em Windows: ``.\target\debug\hello_cargo.exe``
<br><br>
Na primeira vez que executar o ``cargo build`` no projeto, será gerado um arquivo chamado ``cargo.lock`` que não precisa ser editado manualmente.
<br><br>
Você também pode pedir para o cargo compilar e executar automaticamente, usando o comando ``cargo run``.
<br><br>
Para finalizarmos os comandos principais, temos também o ``cargo check`` que verifica rapidamente seu código garantindo que ele é compilável. Este nem executa nem compila, ele apenas verifica que tudo está correto.

### Lançando uma versão estável
Quando seu projeto estiver pronto para ser distribuído você pode executar o comando ``cargo build --release`` gerando um executável com otimizações. Dessa vez seu executável irá para pasta ``target/release``.

# 2.0 - Criando um joguinho de adivinhação
Você está indo bem, vamos juntos criar um projeto prático usando Rust! Nesta parte do doc, aprenderemos conceitos importantes do Rust.
<br><br>
Implementaremos um problema clássico de programação para iniciantes: um jogo de adivinhação. 
<br>
Aqui está como funciona: o programa gerará um número inteiro aleatório entre 1 e 100 e solicitará que o jogador digite um palpite. Depois que um palpite é inserido, o o programa indicará se o palpite é muito baixo ou muito alto. Se o palpite for correto, o jogo imprimirá uma mensagem de felicitações e sairá.
### Criando um novo projeto com Cargo
Como aprendemos anteriormente, vamos criar um novo projeto usando o comando ``cargo new guessing_game``.<br>
O Cargo gerará toda estrutura padrão de projetos em Rust, se tiver alguma dúvida volte para parte inicial do doc.<br>
Para checar se está tudo certo e o ``Hello World`` padrão será executado use o comando ``cargo run``.

### Processo de adivinhar!
Para começar vamos pedir para que o usuário insira um palpite, abra o seu arquivo ``src/main.rs`` e vamos editá-lo:

> Tradução: Aqui os textos estão em português, no documento original eles estão em inglês. E há adição de código extra.``

```rust
use std::io;

fn main() {
    println!("Adivinhe o número!");

    println!("Por favor, insira um palpite:");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Falha ao ler o palpite!");

    println!("Você disse: {guess}");
}
```
