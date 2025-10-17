-----

# 🍷 API: Gerenciamento de Vinhos (Backend)

Este repositório contém o código backend para o sistema *WineFlow, uma API RESTful simples desenvolvida em **Flask* e *SQLAlchemy* para gerenciar o cadastro e o catálogo de vinhos.

## 🚀 Tecnologias Utilizadas

  * *Linguagem:* Python 3.x
  * *Framework Web:* *Flask*
  * *Banco de Dados:* *SQLite* (usado em ambiente de desenvolvimento, configurável para PostgreSQL/MySQL em produção)
  * *ORM:* *Flask-SQLAlchemy*
  * *Documentação da API:* *Flasgger* (baseado em Swagger/OpenAPI)
  * *Cross-Origin:* *Flask-CORS*

## 📂 Estrutura do Projeto

A aplicação segue uma estrutura modular para separar a configuração, o modelo de dados e a lógica da aplicação principal:


backend-api/
├── app.py                      # Aplicação Flask principal e definições de rotas (Endpoints)
├── database.db                 # Arquivo SQLite gerado ao rodar o app.py
├── schemas/
│   └── config.py               # Definições de classes de configuração (Desenvolvimento/Produção)
├── model/
│   └── models.py               # Definição da classe Vinho (Modelo SQLAlchemy)



## ⚙️ Instalação e Execução

Siga os passos abaixo para configurar e executar o backend em seu ambiente local.

### Pré-requisitos

Você deve ter o *Python 3* instalado em seu sistema.

### 1\. Criar e Ativar o Ambiente Virtual

Recomendado para isolar as dependências do projeto.

⁠ Virtualenv 

# Cria o ambiente virtual

python3 -m venv venv

# Ativa o ambiente virtual

# No Linux/macOS:
source venv/bin/activate
# No Windows (PowerShell):
.\venv\Scripts\Activate
 ⁠

### 2\. Instalar Dependências

Instale todas as bibliotecas necessárias. *Nota:* Assumindo que você tem um arquivo ⁠ requirements.txt ⁠ com as dependências (Flask, Flask-SQLAlchemy, Flasgger, Flask-CORS). Se não tiver, instale manualmente:

⁠ bash
pip install Flask, pip intall Flask-SQLAlchemy, pip install Flasgger, pip install Flask-CORS

No seu terminal
 ⁠
### No terminal de um Pip Freeze para gerar o arquivo Requirements.txt

### 3\. Executar a Aplicação

A aplicação será iniciada no modo de desenvolvimento, criando o arquivo ⁠ database.db ⁠ na raiz, caso ele não exista.

⁠ bash
python app.py
 ⁠

O backend estará rodando em: **⁠ http://127.0.0.1:5000/ ⁠** 
-----

## 📝 Documentação da API (Swagger UI)

A documentação interativa completa dos endpoints está disponível através do *Swagger UI*, acessível no seu navegador após iniciar o servidor:

*URL da Documentação:* ⁠ http://127.0.0.1:5000/apidocs ⁠

### Endpoints Principais (CRUD)

| Método | URL | Descrição |
| :--- | :--- | :--- |
| *POST* | ⁠ /cadastrar_vinho ⁠ | Cria um novo registro de vinho no banco de dados. |
| *GET* | ⁠ /buscar_vinhos ⁠ | Retorna uma lista JSON de todos os vinhos cadastrados. |
| *DELETE* | ⁠ /deletar_vinho/<int:id> ⁠ | Deleta um vinho específico usando seu ID único. |

### Exemplo de Requisição (POST /cadastrar\_vinho)

*Corpo da Requisição (JSON):*

⁠ json
{
    "nome_vinho": "Vinho Tinto Cabernet Sauvignon Reserva",
    "data_fabricacao": "2022-10-25",
    "cidade_producao": "Vale dos Vinhedos"
}
 ⁠

*Resposta de Sucesso (201 Created):*

⁠ json
{
    "message": "Vinho cadastrado com sucesso!"
}
 ⁠

## 🛠️ Configuração

O arquivo ⁠ schemas/config.py ⁠ gerencia as configurações de ambiente.

  * A chave *⁠ config_name = 'development' ⁠* em ⁠ app.py ⁠ carrega a configuração da classe ⁠ DevelopmentConfig ⁠.
  * O banco de dados é configurado por padrão como *SQLite* (⁠ sqlite:///database.db ⁠), persistindo o arquivo ⁠ database.db ⁠ na raiz do projeto. Para mudar para um banco de dados de produção, basta atualizar a ⁠ SQLALCHEMY_DATABASE_URI ⁠ na classe ⁠ ProductionConfig ⁠.


