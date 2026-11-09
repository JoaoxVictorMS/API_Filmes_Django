<h1 align="center" style="font-weight: bold;">MovieFlix API Django REST</h1>

<p align="center">
  API RESTful desenvolvida em Django e Django REST Framework para gerenciamento de catálogo de filmes e séries, contando com documentação interativa Swagger/Redoc, autenticação via BasicAuth, busca/filtros avançados, carga inicial via Fixtures e suíte de testes automatizados.
</p>

[PYTHON__BADGE]: https://img.shields.io/badge/Python-%233776AB.svg?style=for-the-badge&logo=python&logoColor=white
[DJANGO__BADGE]: https://img.shields.io/badge/Django_REST-ff1744?style=for-the-badge&logo=django&logoColor=white
[SWAGGER__BADGE]: https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black
[SQLITE__BADGE]: https://img.shields.io/badge/SQLite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white

<p align="center">
  • <a href="#technologies">Tecnologias</a> •
  <a href="#started">Iniciando</a> •
  <a href="#fixtures">Banco de Dados & Fixtures</a> •
  <a href="#tests">Testes Automatizados</a> •
  <a href="#documentation">Documentação OpenAPI</a> •
  <a href="#routes">API Endpoints</a> •
  <a href="#colab">Colaboradores</a> •
  <a href="#contribute">Contribua</a>
</p>

<h2 id="technologies">💻 Tecnologias</h2>

<div>

![Python][PYTHON__BADGE]
![Django REST Framework][DJANGO__BADGE]
![Swagger][SWAGGER__BADGE]
![SQLite][SQLITE__BADGE]

</div>

<h2 id="started">🚀 Iniciando</h2>

Siga as instruções abaixo para rodar o projeto em seu ambiente local.

<h3>Pré-requisitos</h3>

- [Python 3.10+](https://www.python.org/)
- [Git](https://git-scm.com/)

<h3>Clonando</h3>

```bash
git clone https://github.com/JoaoxVictorMS/API_Filmes_Django.git
cd API_Filmes_Django
```

<h3>Criando e ativando o ambiente virtual</h3>

```bash
# Criar ambiente virtual
python -m venv .venv

# Ativar no Windows (PowerShell)
.\.venv\Scripts\Activate.ps1

# Ativar no Windows (Git Bash)
source .venv/Scripts/activate

# Ativar no Linux / macOS
source .venv/bin/activate
```

<h3>Instalando dependências</h3>

```bash
pip install -r requirements.txt
```

<h2 id="fixtures">🗄️ Executando as Migrações e Populando o Banco (Fixtures)</h2>

Este projeto utiliza o mecanismo nativo de **Fixtures** do Django para pré-popular o catálogo inicial de filmes e séries:

```bash
# Aplicar migrações do banco
python manage.py makemigrations
python manage.py migrate

# Carregar dados iniciais (Fixtures)
python manage.py loaddata programas_iniciais.json
```

<h3>Criando Superusuário (Para Autenticação)</h3>

Como esta API requer autenticação para os endpoints protegidos, crie uma conta administrativa:

```bash
python manage.py createsuperuser
```

<h3>Executando a aplicação</h3>

```bash
python manage.py runserver
```

A API estará disponível no endereço `http://127.0.0.1:8000/`.

<h2 id="tests">🧪 Testes Automatizados</h2>

O projeto conta com testes automatizados cobrindo Models, Serializers, Autenticação e Fixtures.

Para rodar a suíte completa de testes:

```bash
python manage.py test
```

<h2 id="documentation">📑 Documentação Interativa (Swagger & Redoc)</h2>

Com o servidor rodando, você pode acessar a documentação OpenAPI gerada automaticamente via `drf-yasg`:

- **Swagger UI:** [http://127.0.0.1:8000/swagger/](http://127.0.0.1:8000/swagger/)
- **Redoc:** [http://127.0.0.1:8000/redoc/](http://127.0.0.1:8000/redoc/)

<h2 id="routes">📍 API Endpoints</h2>

> **Nota de Autenticação:** Os endpoints de `/programas/` exigem autenticação básica (`BasicAuthentication`). Você deve enviar o nome de usuário e senha (criados via `createsuperuser`) no cabeçalho HTTP da requisição.

| rota                               | descrição                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------------- |
| <kbd>GET /programas/</kbd>         | Retorna a lista de programas (filmes/séries), veja os [detalhes da resposta](#get-programas-list) |
| <kbd>POST /programas/</kbd>        | Cadastra um novo programa no catálogo, veja os [detalhes da requisição](#post-programas-detail)   |
| <kbd>GET /programas/{id}/</kbd>    | Retorna os detalhes de um programa específico pelo ID                                             |
| <kbd>PUT /programas/{id}/</kbd>    | Atualiza todos os dados de um programa específico                                                 |
| <kbd>PATCH /programas/{id}/</kbd>  | Atualiza parcialmente os dados de um programa específico                                          |
| <kbd>DELETE /programas/{id}/</kbd> | Remove um programa do catálogo                                                                    |

> **Filtros e Buscas disponíveis no `GET /programas/`:**
>
> - **Filtro Por Tipo (`?tipo=`):** Filtra o tipo de programa (`?tipo=F` para Filmes ou `?tipo=S` para Séries).
> - **Busca Por Título (`?search=`):** Realiza busca textual no título do programa (ex: `?search=Bruxo`).

<h3 id="get-programas-list">GET /programas/</h3>

**RESPOSTA**

```json
[
  {
    "titulo": "Coisas bizarras",
    "tipo": "S",
    "data_lancamento": "2016-07-15",
    "likes": 7864
  },
  {
    "titulo": "Capitão Bahia",
    "tipo": "F",
    "data_lancamento": "2011-07-29",
    "likes": 10340
  }
]
```

<h3 id="post-programas-detail">POST /programas/</h3>

**REQUISIÇÃO**

```json
{
  "titulo": "Interestelar",
  "tipo": "F",
  "data_lancamento": "2014-11-06",
  "likes": 15200
}
```

**RESPOSTA (201 Created)**

```json
{
  "titulo": "Interestelar",
  "tipo": "F",
  "data_lancamento": "2014-11-06",
  "likes": 15200
}
```

<h2 id="colab">🤝 Colaboradores</h2>

Um agradecimento especial a todas as pessoas que contribuíram para este projeto.

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/JoaoxVictorMS">
        <img src="https://avatars.githubusercontent.com/u/98715957?v=4" width="100px;" alt="Foto de perfil"/><br>
        <sub>
          <b>João Victor</b>
        </sub>
      </a>
    </td>
  </tr>
</table>

<h2 id="contribute">📫 Contribua</h2>

Para contribuir com o projeto:

1. Faça o fork do projeto
2. Crie uma nova branch com a sua funcionalidade (`git checkout -b feature/minha-feature`)
3. Faça commit das suas alterações (`git commit -m 'feat: Adiciona minha funcionalidade'`)
4. Faça o push para a branch (`git push origin feature/minha-feature`)
5. Abra um Pull Request

<h3>Documentações que podem ajudar</h3>

[📝 Como criar um Pull Request](https://www.atlassian.com/br/git/tutorials/making-a-pull-request)

[💾 Padrão de commit](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)
