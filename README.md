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

### How to run flask learning project:
1- flask run or flask run --reload
