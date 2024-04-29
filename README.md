# Dev environment:
▪ python >= 3.6.* {flask depends on it}
▪ visual code {IDE for development}
▪ python microsoft extension for visual code

# python download:
https://www.python.org/downloads/

## python installation:
![image](https://github.com/adintelti/mypythonprojects/assets/155258727/e622e251-ddeb-4ff2-af12-01f2c3846fc1)
![image](https://github.com/adintelti/mypythonprojects/assets/155258727/9e8c3c6c-5c1a-452c-aec5-37def64c9341)

## python extension for vscode:
![image](https://github.com/adintelti/mypythonprojects/assets/155258727/2fa6191d-840a-4f58-8ee8-696023cc3af7)

### command to check installed python version:
python --version

# setup for a new flask project(run the following commands)
c:\> mkdir {new project name}
c:\>cd {new project name}

# creates a virtual environment on windows
c:\{new project name}> py -3 –m venv venv

# activate the virtual environment
c:\{new project name}> venv\Scripts\activate
(venv) c:\{new project name}>

# installing flask
c:\> pip install Flask

# Coding:

## using flask:
from flask import Flask

templates | placeholders
▪ {% ... %} declares commands
▪ {{ ... }} shows variable's contents or expressions
▪ {# ... #} non rendered comments

rendering a template:

using templates ->
from flask import Flask, render_template

render_template(‘template.html’, [placeholder = valor, ...])
                  1              2
                  
1- nome do template. Por
padrão o jinja procura-o
na pasta /templates

2- nome da variável no template
(placeholder) e o seu valor no contexto da
função tratadora. Diversos pares
(placeholder-valor) podem ser passados
na função render_template.

### templates | filtro
modifica o conteúdo de uma variável no
template, aplicado após o nome da
variável com o caractere “|”

### templates | filtros
nome descrição
capitalize - converte o primeiro caractere para letra maiúscula.
lower - converte todas as letras para minúsculas.
upper - converte todas as letras para maiúsculas.
trim - remove espaços em branco no início e no final do valor.
striptags -  remove qualquer tag HTML do valor.
fonte: https://jinja.palletsprojects.com/en/3.0.x/templates/#builtin-filters

## exemplo
templates | filtros
### templates/user.html
<h2>{{ name|upper }}</h2>

### templates | estruturas de controle

instruções que alteram o fluxo de
execução

### templates | estrutura de controle if
{% if expressão lógica %}
...
{% else %}
...
{% endif %}

### templates | estrutura de controle if
{% if expressão lógica %}
...
{% else %}
...
{% endif %}

### exemplo

### templates/user.html
{% if name %}
<h2>{{ name|upper }}</h2>
{% else %}
<h2>Anônimo!</h2>
{% endif %}

### templates | dry | blocos

sintaxe: 
{% block {blockname} %}
{% endblock %}
*os caracteres "{}" não constam na sintaxe


### bootstrap | integração com o flask
pip install flask-bootstrap

### importa a classe Bootstrap em um arquivo Python.

#### app.py
from flask_bootstrap import Bootstrap
app = Flask(__name__)
boostrap = Boostrap(app)

#### inicie a página da application com isso
{% extends “boostrap/base.html %}”

## banco de dados | sqlalchemy
## banco de dados | flask-sqlalchemy
  wrapper para o sqlalchemy
### banco de dados | string de conexão
engine url
mysql mysql://username:password@hostname/database
postgres postgresql://username:password@hostname/database
sqlite (linux, osx) sqlite:///absolute/path/to/database
sqLite (windows) sqlite:///absolute\path\to\database
fonte: https://flask-sqlalchemy.palletsprojects.com/en/2.x/config/

## Configuração

### banco de dados | configuração
##### importa os pacotes necessários.
import os
from flask_sqlalchemy import SQLAlchemy
banco de dados | configuração
##### importa os pacotes necessários.
import os
from flask_sqlalchemy import SQLAlchemy
##### pega o diretório base da aplicação a partir da
##### constante __file__.
basedir = os.path.dirname(__file__)
banco de dados | configuração
##### importa os pacotes necessários.
import os
from flask_sqlalchemy import SQLAlchemy
##### pega o diretório base da aplicação a partir da
##### constante __file__.
basedir = os.path.abspath(os.path.dirname(__file__)
##### define a URI de conexão para o banco de dados.
app = Flask(__name__)
app.config[‘SQLALCHEMY_DATABASE_URI’] =\
‘sqlite:///’ + os.path.join(basedir, ‘database.sqlite’)
banco de dados | configuração
##### importa os pacotes necessário.
import os
from flask_sqlalchemy import SQLAlchemy
##### define a URI de conexão para o banco de dados.
app = Flask(__name__)
app.config[‘SQLALCHEMY_DATABASE_URI’] =\
‘sqlite:///’ + os.path.join(basedir, ‘database.sqlite’)
##### pega o diretório base da aplicação a partir da
##### constante __file__.
basedir = os.path.abspath(os.path.dirname(__file__)
##### instancia o objeto SQLAlchemy para representar o banco de dados.
db = SQLAlchemy(app)

## banco de dados | modelo
manipula os dados, a lógica
e as regras de negócios da
aplicação
banco de dados | modelo
#### definição da classe do modelo Post.
class Post (db.Model):
__tablename__ = ‘posts’
banco de dados | modelo
#### definição da classe modelo Post.
class Post (db.Model):
__tablename__ = ‘posts’
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
title = db.Column(db.String(256), nullable=False)
body = db.Column(db.String(1024), nullable=False)
banco de dados | modelo
#### definição da classe modelo Post.
class Post (db.Model):
__tablename__ = ‘posts’
#### representa um objeto como string.
def __repr__(self):
return f”Post #{self.id}: {self.title}”
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
title = db.Column(db.String(256), nullable=False)
body = db.Column(db.String(1024), nullable=False)
modelo | opções de colunas
opção descrição
primary_key = True, a coluna será chave primária da tabela.
unique = True, não permitirá valores duplicados na coluna.
index = True, um índice será criado para a coluna.
nullable = False, não permitirá valores nulos para a coluna.
default = valor, define um valor padrão para a coluna.
fonte: https://docs.sqlalchemy.org/en/14/

## modelo | opções de relacionamentos
opção descrição
backref adiciona uma referência para trás no outro modelo de
relacionamento.
primaryjoin especifica a condição de junção entre dois modelos
explicitamente. É necessários em relacionamentos ambíguos.
order_by especifica a ordem usada para os itens no relacionamento.
fonte: https://docs.sqlalchemy.org/en/14/

### modelo | relacionamento 1:1

#### definição da classe modelo Director.
class Director (db.Model):
__tablename__ = ‘directors’
#### representa um objeto como string.
def __repr__(self):
return f”Director #{self.id}: {self.name}”
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
name = db.Column(db.String(45), nullable=False)
#### ...
address = db.relationship(‘Address’, backref=‘director’)
modelo | relacionamento 1:1
#### definição da classe modelo Address.
class Address (db.Model):
__tablename__ = ‘addresses’
#### representa um objeto como string.
def __repr__(self):
return f”Address #{self.id}: {self.street}”
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
street = db.Column(db.String(120), nullable=True)
...
#### relacionamento com o modelo Director
director_id = db.Column(‘Director’, db.ForeignKey(‘directors.id’))
modelo | relacionamento 1:N
modelo | relacionamento 1:N
#### definição da classe modelo Director.
class Director (db.Model):
__tablename__ = ‘directors’
#### representa um objeto como string.
def __repr__(self):
return f”Director #{self.id}: {self.name}”
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
name = db.Column(db.String(45), nullable=False)
...
movies = db.relationship(‘Movie’, backref=‘director’)
modelo | relacionamento 1:N
#### definição da classe modelo Movie.
class Movie (db.Model):
__tablename__ = ‘movies’
#### representa um objeto como string.
def __repr__(self):
return f”Movie #{self.id}: {self.title}”
#### definição dos atributos do modelo.
id = db.Column(db.Integer, primary_key=True)
title = db.Column(db.String(45), nullable=True)
...
#### relacionamento com o modelo Director
director_id = db.Column(db.Integer, db.ForeignKey(‘directors.id’))
modelo | relacionamento N:N
modelo | relacionamento N:N
casts = db.Table(
“casts”,
db.Column(“actor_id”, db.Integer, db.ForeignKey(“actors.id”)),
db.Column(“movie_id”, db.Interger, db.ForeignKey(“movies.id”)),
)
modelo | relacionamento N:N
#### definição da classe modelo Movie.
class Movie (db.Model):
__tablename__ = ‘movies’
#### ...
actors = db.relationship("Actor", secondary=casts)
casts = db.Table(
“casts”,
db.Column(“actor_id”, db.Integer, db.ForeignKey(“actor.id”)),
db.Column(“movie_id”, db.Interger, db.ForeignKey(“movie.id”)),
)
modelo | relacionamento N:N
#### definição da classe modelo Actor.
class Actor(db.Model):
id = db.Column(db.Integer, primary_key=True)
movies = db.relationship(“Movie", secondary=casts)
#### definição da classe modelo Movie.
class Movie (db.Model):
__tablename__ = ‘movies’
#### ...
actors = db.relationship("Actor", secondary=casts)
actors = db.Table(
“actors”,
db.Column(“actor_id”, db.Integer, db.ForeignKey(“actor.id”)),
db.Column(“movie_id”, db.Interger, db.ForeignKey(“movie.id”)),
)

## instalando a extensão flask-migrate
(venv) c:\todo> pip install flask-migrate

## usando flask-migrate
#### app.py
from flask_migrate import Migrate
#### ...
migrate = Migrate(app, db)

## comandos flask-migrate
flask db init - suporte a migrações de banco de dados
flask db migrate –m ”initial migration” - cria um script de migração automática
flask db upgrade - aplica o script de migração no banco de dados

### How to run flask learning project:
1- flask run or flask run --reload
