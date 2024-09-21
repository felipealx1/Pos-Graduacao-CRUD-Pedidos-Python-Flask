# Pos-Graduacao-CRUD-Pedidos-Python-Flask
<body>

<h1>CRUD de Pedidos - Flask + MongoDB</h1>

<p>Este é um projeto da Pós-Graduação de Desenvolvimento Web FullStack, da Disciplina de Banco de Dados, que tem como objetivo criar um CRUD (Create, Read, Update, Delete) usando a linguagem Python, o framework Flask e o banco de dados MongoDB. O sistema gerencia informações de clientes, produtos e pedidos, realizando operações básicas de manipulação dos dados.</p>

<h2>Tecnologias Utilizadas</h2>
<ul>
    <li><strong>Linguagem</strong>: Python</li>
    <li><strong>Framework</strong>: Flask</li>
    <li><strong>Banco de Dados</strong>: MongoDB</li>
    <li><strong>Bibliotecas</strong>: Flask, pymongo, bson</li>
</ul>

<h2>Funcionalidades</h2>

<p>O sistema CRUD oferece as seguintes funcionalidades para três entidades principais: <code>Clientes</code>, <code>Produtos</code> e <code>Pedidos</code>.</p>

<h3>Clientes</h3>
<ul>
    <li><strong>Listar Clientes</strong>: Retorna todos os clientes cadastrados no banco de dados.</li>
    <li><strong>Adicionar Cliente</strong>: Insere um novo cliente no banco de dados.</li>
    <li><strong>Alterar Cliente</strong>: Atualiza os dados de um cliente existente.</li>
    <li><strong>Excluir Cliente</strong>: Remove um cliente do banco de dados.</li>
</ul>

<h3>Produtos</h3>
<ul>
    <li><strong>Listar Produtos</strong>: Retorna todos os produtos cadastrados no banco de dados.</li>
    <li><strong>Adicionar Produto</strong>: Insere um novo produto no banco de dados.</li>
    <li><strong>Alterar Produto</strong>: Atualiza os dados de um produto existente.</li>
    <li><strong>Excluir Produto</strong>: Remove um produto do banco de dados.</li>
</ul>

<h3>Pedidos</h3>
<ul>
    <li><strong>Listar Pedidos</strong>: Retorna todos os pedidos cadastrados no banco de dados.</li>
    <li><strong>Adicionar Pedido</strong>: Insere um novo pedido no banco de dados, verificando se o cliente e o produto existem.</li>
    <li><strong>Alterar Pedido</strong>: Atualiza os dados de um pedido existente.</li>
    <li><strong>Excluir Pedido</strong>: Remove um pedido do banco de dados.</li>
</ul>

<h2>Requisitos de Instalação</h2>

<h3>Pré-requisitos</h3>
<p>Antes de começar, você vai precisar ter instalado em sua máquina:</p>
<ul>
    <li><a href="https://www.python.org/">Python</a></li>
    <li><a href="https://www.mongodb.com/try/download/community">MongoDB</a></li>
    <li><a href="https://pypi.org/project/virtualenv/">Virtualenv</a></li>
</ul>

<h3>Instalando o Projeto</h3>

<ol>
    <li><strong>Clone o repositório</strong>:
        <pre><code>git clone https://github.com/felipealx1/Pos-Graduacao-CRUD-Pedidos-Python-Flask</code></pre>
    </li>
    <li><strong>Entre no diretório do projeto</strong>:
        <pre><code>cd crud-pedidos-flask</code></pre>
    </li>
    <li><strong>Crie um ambiente virtual</strong>:
        <pre><code>python -m venv venv</code></pre>
    </li>
    <li><strong>Ative o ambiente virtual</strong>:
        <ul>
            <li>No Windows:
                <pre><code>venv\Scripts\activate</code></pre>
            </li>
        </ul>
    </li>
    <li><strong>Configure a conexão com o MongoDB</strong>:
        <p>No arquivo <code>config.py</code>, adicione as credenciais do seu MongoDB:</p>
        <pre><code>from pymongo import MongoClient

client = MongoClient("mongodb://localhost:27017/")
bd = client["nome_do_banco"]
pedidos_collection = bd["pedidos"]
produtos_collection = bd["produtos"]
clientes_collection = bd["clientes"]
        </code></pre>
    </li>
    <li><strong>Execute a aplicação</strong>:
        <pre><code>flask run</code></pre>
    </li>
</ol>

<h2>Endpoints</h2>

<h3>Clientes</h3>
<ul>
    <li><strong>GET /clientes</strong> - Lista todos os clientes.</li>
    <li><strong>POST /inserirCliente</strong> - Insere um novo cliente.
        <pre><code>{
  "id_cliente": 123,
  "nome": "João",
  "email": "joao@email.com",
  "cpf": "000.000.000-00",
  "data_nascimento": "1990-01-01"
}
        </code></pre>
    </li>
    <li><strong>PUT /alteraCliente/{id_cliente}</strong> - Altera os dados de um cliente.
        <pre><code>{
  "nome": "João Silva",
  "email": "joao@email.com"
}
        </code></pre>
    </li>
    <li><strong>DELETE /excluirCliente/{id_cliente}</strong> - Exclui um cliente.</li>
</ul>

<h3>Produtos</h3>
<ul>
    <li><strong>GET /produtos</strong> - Lista todos os produtos.</li>
    <li><strong>POST /inserirProduto</strong> - Insere um novo produto.
        <pre><code>{
  "id_produto": 123,
  "nome": "Notebook",
  "descricao": "Notebook Dell",
  "preco": 3500,
  "categoria": "Eletrônicos"
}
        </code></pre>
    </li>
    <li><strong>PUT /alteraProduto/{id_produto}</strong> - Altera os dados de um produto.
        <pre><code>{
  "nome": "Notebook Dell Inspiron",
  "preco": 3700
}
        </code></pre>
    </li>
    <li><strong>DELETE /excluirProduto/{id_produto}</strong> - Exclui um produto.</li>
</ul>

<h3>Pedidos</h3>
<ul>
    <li><strong>GET /pedidos</strong> - Lista todos os pedidos.</li>
    <li><strong>POST /pedidos</strong> - Insere um novo pedido.
        <pre><code>{
  "id_cliente": 123,
  "id_produto": 456
}
        </code></pre>
    </li>
    <li><strong>PUT /alteraPedido/{id_pedido}</strong> - Altera os dados de um pedido.
        <pre><code>{
  "id_produto": 789
}
        </code></pre>
    </li>
    <li><strong>DELETE /excluirPedido/{id_pedido}</strong> - Exclui um pedido.</li>
</ul>

<h2>Estrutura do Projeto</h2>

<pre><code>crud-pedidos-flask/
│
├── app.py                # Arquivo principal da aplicação Flask
├── config.py             # Configurações da conexão MongoDB
├── venv/                 # Ambiente virtual
</code></pre>

<h2>Executando os Testes</h2>
<p>Caso queira realizar testes na API, utilize ferramentas como <a href="https://www.postman.com/">Postman</a> ou <code>curl</code> no terminal para enviar requisições para os endpoints disponíveis.</p>

<h2>Autor</h2>

<p>Desenvolvido por <strong>José Felipe Alexandre Martins</strong> 


</body>
</html>
