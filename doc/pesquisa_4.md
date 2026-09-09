PDO em PHP
Introdução
PDO, que significa PHP Data Objects, é uma extensão do PHP utilizada para realizar a comunicação entre uma aplicação e um banco de dados. Com ela, é possível executar comandos para inserir, consultar, alterar e excluir informações armazenadas no banco.
O PDO é bastante utilizado em sistemas desenvolvidos com PHP porque facilita a conexão com diferentes bancos de dados e também oferece recursos para deixar as aplicações mais seguras.
O que é PDO?
PDO é uma interface de acesso a bancos de dados disponível no PHP. Ela permite que o programador utilize uma estrutura semelhante para trabalhar com diferentes sistemas de banco de dados, como MySQL, PostgreSQL, SQLite e outros.
Uma das principais vantagens é que o código pode ser organizado de forma mais padronizada, facilitando o desenvolvimento e a manutenção do sistema.
Para que serve o PDO?
O PDO pode ser utilizado para diversas operações em um banco de dados, como:
Criar uma conexão com o banco de dados;
Inserir novos registros;
Consultar informações;
Atualizar registros existentes;
Excluir informações;
Executar comandos SQL;
Utilizar consultas preparadas para aumentar a segurança do sistema.
Conexão com o banco de dados
Para utilizar PDO, primeiro é necessário criar uma conexão com o banco de dados. Um exemplo utilizando MySQL é:
<?php

$host = "localhost";
$db = "escola";
$user = "root";
$pass = "";

try {
    $pdo = new PDO("mysql:host=$host;dbname=$db;charset=utf8", $user, $pass);

    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    echo "Conectado com sucesso!";

} catch (PDOException $e) {
    echo "Erro na conexão: " . $e->getMessage();
}

?>

Nesse exemplo, o PDO cria a conexão com o banco de dados. O try tenta realizar a conexão e o catch identifica possíveis erros.
Prepared Statements
Uma das principais características do PDO são os Prepared Statements, também chamados de consultas preparadas.
Eles permitem separar os comandos SQL dos dados enviados pelo usuário. Isso ajuda a evitar problemas de segurança, principalmente ataques conhecidos como SQL Injection.
Exemplo:
$sql = "INSERT INTO usuarios (nome, email) VALUES (:nome, :email)";

$stmt = $pdo->prepare($sql);

$stmt->execute([
    ":nome" => "João",
    ":email" => "joao@email.com"
]);

Nesse caso, os valores são enviados separadamente do comando SQL, tornando a operação mais segura.
Principais métodos do PDO
O PDO possui vários métodos importantes. Alguns dos mais utilizados são:
prepare()
Prepara uma instrução SQL antes de sua execução.
execute()
Executa uma instrução que foi preparada.
query()
Executa diretamente uma consulta SQL.
fetch()
Obtém um registro do resultado de uma consulta.
fetchAll()
Obtém todos os registros retornados por uma consulta.
Vantagens do PDO
Entre as principais vantagens do PDO estão:
Maior segurança: permite utilizar consultas preparadas contra SQL Injection.
Compatibilidade: pode trabalhar com diferentes bancos de dados.
Organização: facilita a estruturação do código responsável pelo banco.
Tratamento de erros: permite identificar erros através de exceções.
Facilidade de manutenção: o código fica mais organizado e pode ser reutilizado.
PDO em um CRUD
O PDO também é muito utilizado em sistemas CRUD. CRUD representa quatro operações básicas:
Create: criar ou inserir dados;
Read: consultar dados;
Update: atualizar dados;
Delete: excluir dados.
Por exemplo, em um sistema de cadastro de livros, o PDO pode ser utilizado para inserir um livro no banco, consultar os livros cadastrados, alterar suas informações ou excluir um livro.
Diferença entre PDO e MySQLi
O PHP possui principalmente duas formas tradicionais de trabalhar com bancos MySQL: PDO e MySQLi.
O MySQLi é voltado para bancos MySQL, enquanto o PDO possui suporte a diferentes tipos de bancos de dados por meio de drivers.
Além disso, ambos permitem utilizar consultas preparadas, que são importantes para aumentar a segurança das aplicações.
Conclusão
O PDO é uma ferramenta importante para o desenvolvimento de sistemas em PHP que precisam trabalhar com bancos de dados. Ele permite realizar operações como cadastro, consulta, alteração e exclusão de informações.
Além de facilitar a comunicação entre o PHP e o banco de dados, o PDO oferece recursos de segurança, principalmente através das consultas preparadas. Por isso, ele é bastante utilizado em aplicações que precisam trabalhar com informações armazenadas em bancos de dados de forma organizada e mais segura.
Referências
PHP. PDO – PHP Data Objects. Documentação oficial do PHP.
PHP. PDO::prepare. Documentação oficial do PHP.
PHP. PDO::execute. Documentação oficial do PHP.

