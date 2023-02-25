# Introdução
Este doc é a versão em Português Brasileiro do Rust Book, por conveniência este doc não está ao pé da letra, portanto espere alguns tópicos eliminados ou transcritos para dentro de outros, além de dicas e exemplos extras. <br><br>Com tudo isso em mente podemos começar a navegar pelo mundo Rust!

# 1.0 - Início
Como havia dito acima, alguns tópicos foram arrancados por conveniência e um deles é o "Como instalar" que ficaria bem aqui. 
Se você ainda não tem o Rust instalado por favor visite este tópico antes de continuar: https://doc.rust-lang.org/book/ch01-01-installation.html
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
