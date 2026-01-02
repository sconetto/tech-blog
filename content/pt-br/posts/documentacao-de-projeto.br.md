+++
title = "Documentação de projeto de um jeito simples!"
author = "João Pedro Sconetto"
date = "2026-01-02T14:39:25+01:00"
description = "Como configurar rapidamente um sistema de documentação com implementação automática para seus projetos."
cover = "/img/project-documentation-made-easy.jpg"
+++

Aqui vou mostrar como você pode criar facilmente um sistema de documentação para seu projeto usando Python.

## Criando documentação de projeto

De vez em quando você tem um projeto muito legal que deseja compartilhar com o mundo, mas a única documentação que você tem é o README do seu repositório? Que tal criar uma página web para ser a documentação do seu projeto? Melhor ainda, aqui vou mostrar como você pode fazer isso e hospedá-la gratuitamente!

Vamos começar a trabalhar e fazer isso.

## Configurando o GitHub

Primeiro, vamos criar um repositório para hospedar nossos arquivos. A primeira coisa é bem simples, vá para o [GitHub](github) e clique no botão verde [**New**](github-new-repo) no canto superior esquerdo da página. Caso você não tenha uma conta no GitHub, você pode criar uma [aqui](github-join).

Para este post, vou criar um chamado `dev-to-docs`.

### MkDocs

Agora vamos configurar nosso MkDocs, o sistema que criará as páginas para nossa documentação. Para mais informações sobre o MkDocs, você pode verificar a [documentação](mkdocs-docs) deles.
Para gerenciar nossos pacotes Python, vou usar o [_pipenv_](pipenv-docs), mas fique à vontade para usar o que você mais gostar!

Vamos instalar e inicializar o ambiente Python do nosso projeto:

{{< code language="shell" open="true" >}}
sudo apt install pipenv # certifique-se de usar o gerenciador de pacotes da sua distro!
pipenv --three # cria o ambiente com Python 3
{{< /code >}}

Com nosso ambiente criado (_pipenv_ criará os arquivos necessários), vamos instalar nossas dependências:

{{< code language="shell" open="true" >}}
pipenv install mkdocs==1.6.1
pipenv install mkdocs-material==9.7.1
pipenv install --dev black==25.12.0 # para formatação de código
{{< /code >}}

Agora devemos estar prontos para criar nosso projeto MkDocs:

{{< code language="shell" open="true" >}}
pipenv shell # ativa nosso ambiente
mkdocs new dev-to-docs
{{< /code >}}

Isso gerará a seguinte árvore:

{{< code language="shell" open="true" >}}
.
├── dev-to-docs
│   ├── docs
│   │   └── index.md
│   └── mkdocs.yml
├── Pipfile
└── Pipfile.lock
{{< /code >}}

Nosso sistema base está pronto! Se você quiser verificar em sua máquina local, você pode digitar:

{{< code language="shell" open="true" >}}
cd dev-to-docs # Vá para a pasta raiz do mkdocs.yml
mkdocs serve
{{< /code >}}

> O MkDocs servirá o sistema localmente, geralmente em <http://localhost:8080> ou 127.0.0.1:8080.

## Personalizando nosso sistema

No arquivo `mkdocs.yml` você tem toda a configuração para sua página. Lá você pode definir o nome do seu projeto, o tema, um link para um repositório e muito mais. Para uma lista completa das configurações possíveis, você pode verificar na página [MkDocs: Settings][mkdocs-settings].

Há também mais algumas configurações relacionadas ao design material do MkDocs. A maioria das personalizações aqui está relacionada à aparência, mas explore o quanto quiser as opções aqui [MkDocs Material: Settings][mkdocs-material-settings].

Para este exemplo, o sistema está assim:

{{< code language="yaml" open="true" >}}
site_name: Article Documentation - Docs
site_description: Example project for Documentation system.

repo_url: https://github.com/sconetto/dev-to-docs
repo_name: sconetto/dev-to-docs

edit_uri: edit/main/docs/

theme:
  name: material
  icon:
    repo: fontawesome/brands/github
    logo: fontawesome/solid/users-line
  font:
    text: Fira Sans
    code: Fira Mono
  palette:
    - teal: "(prefers-color-scheme: light)"
      scheme: default
      primary: red
      accent: indigo
      toggle:
        icon: material/lightbulb-outline
        name: Switch to dark mode
    # Dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: indigo
      accent: red
      toggle:
        icon: material/lightbulb
        name: Switch to light mode
  features:
    - navigation.instant
    - navigation.expand
    - navigation.top

extra:
  social:
    - icon: fontawesome/brands/linkedin
      link: https://www.linkedin.com/in/sconetto/
      name: Sconetto's LinkedIn
    - icon: fontawesome/brands/github
      link: https://github.com/sconetto
      name: Sconetto's GitHub

copyright: Copyright &copy; 2026 - 2026 João Pedro Sconetto

markdown_extensions:
  - markdown.extensions.toc:
      slugify: !!python/object/apply:pymdownx.slugs.slugify
        kwds:
          case: lower
  - pymdownx.arithmatex
  - pymdownx.betterem:
      smart_enable: all
  - pymdownx.caret
  - pymdownx.critic
  - pymdownx.details
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
  - pymdownx.inlinehilite
  - pymdownx.magiclink
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.superfences
  - pymdownx.tasklist:
      custom_checkbox: true
  - pymdownx.tilde
  - footnotes

nav:
  - Home: index.md
  - Solution:
      - Overview: solution/overview.md
      - Architecture: solution/architecture.md
  - Modules:
      - Auth API: modules/api-auth.md
      - Paycheck API: modules/api-paycheck.md
      - Register API: modules/api-register.md
      - Vacation API: modules/api-vacation.md
      - Human Resources UI: modules/front-register.md
  - Interfaces:
      - About Interfaces: interfaces/about.md
      - Auth API Blueprint: interfaces/api-auth.md
      - Paycheck API Blueprint: interfaces/api-paycheck.md
      - Register API Blueprint: interfaces/api-register.md
      - Vacation API Blueprint: interfaces/api-vacation.md
  - About: about-rh.md
{{< /code >}}

Neste arquivo de exemplo há muitas personalizações, mudanças na paleta de cores, um modo escuro e claro, diferentes ícones, fontes e assim por diante. Mais importante, a navegação é personalizada. Isso pode ser alcançado usando a opção `nav` e criando a árvore de navegação desejada.

Caso você não queira ter uma navegação personalizada, basta colocar os documentos (arquivos markdown) dentro da pasta `docs`. Qualquer subpasta que esta pasta tenha será considerada como a estrutura do documento (dessa forma você pode organizar o nível da documentação).

## Adicionando conteúdo

Adicionar novas páginas ao sistema é muito simples, você só precisa adicionar um arquivo markdown dentro da pasta `docs` e escrever seu conteúdo lá. Ele suporta todos os recursos do markdown, incluindo destaque de código, imagens, links, etc.

Se você quiser uma referência rápida da sintaxe básica e uma folha de dicas, verifique esta página do Markdown Guide, [Markdown Cheat Sheet][markdown-cheatsheet].

Um exemplo de uma página extraída de `docs/about-rh.md`:

{{< code language="markdown" open="true" >}}
# About the HR Project Documentation

In this repository there is an instance of a framework proposal for the
documentation of systems built using microservices, as proposed in the
paper **Microservices Documentation Proposal**[^1]. Therefore the navigation
represents an instance in a case study of the HR system, in which it was
tested for framework validation in the article.

In this framework, the documentation is built according to the desired view.
The following structure describes how the structure of the documents in this
system is arranged according to the strategy of the views:

- `Solution` - Documentation of the software design solution level.
- `Modules` - Documentation of individual architecture modules.
- `Interface` - Documentation of module interfaces and system interactions.

[^1]: Insert article full text link.
{{< /code >}}

Lembre-se: se você tiver uma navegação personalizada, você precisa atualizar o `mkdocs.yml` e indicar o caminho do arquivo adicionado à sua navegação.

**Observação**: Este exemplo tem a extensão para notas de rodapé, isso pode ser usado adicionando `[^n]` no texto e depois no final `[^n]: algum texto`, onde **`n`** indica o número da nota de rodapé.

## Publicando seu sistema

Finalmente, agora que temos tudo configurado, personalizado e com nossa documentação incrível, só precisamos implantá-la. Para isso, vamos usar o GitHub Pages e o GitHub Actions, isso tornará o processo gratuito e simples.

Primeiro, vamos criar e configurar nossa GitHub Action, para isso vamos criar um arquivo YAML e colocá-lo em uma pasta chamada `.github/workflows`:

{{< code language="yaml" open="true" >}}
name: deploy-action
on:
  push:
    branches:
      - master
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: actions/setup-python@v6
        with:
          python-version: '3.12'
          cache: 'pipenv'
      - name: Install pipenv
        run: curl https://raw.githubusercontent.com/pypa/pipenv/master/get-pipenv.py | python
      - run: pipenv install
      - run: cd dev-to-docs && pipenv run mkdocs gh-deploy --force
{{< /code >}}

Isso será executado em cada push para o branch _master_ ou _main_, instalará as dependências, gerará nosso site e o implantará no branch _gh-pages_.

Você pode precisar ativar manualmente o GitHub Pages nas configurações do seu repositório, basta ir em _**Settings > Options > GitHub Pages**_. Selecione a fonte para ser o branch _gh-pages_ e o resto deve ser automático. Caso você tenha um domínio personalizado, você também pode alterá-lo aqui.

Suas configurações ficarão mais ou menos assim:

{{< image src="/img/github-pages-settings.png" alt="Exemplo de configurações para a página." position="center" style="border-radius: 8px;" >}}

Sua documentação deve aparecer em breve em `<username>.github.io/<repository>` ou em `custom.domain/<repository>`, caso você tenha definido um domínio personalizado para a página.

_Pode ser necessário criar um [token de acesso pessoal][github-personal] ao implantar, o que pode ser feito usando [GitHub Secrets][github-secrets]._

---

É isso! Tudo pronto.
Se você chegou até aqui, provavelmente tem um sistema funcionando, que será implantado automaticamente a cada nova mudança no seu branch principal e acessível a todos através de uma página.

Caso você queira verificar o sistema de exemplo:

> [sconetto.me/dev-to-docs][example-system]

O repositório com o código do exemplo pode ser encontrado em [sconetto/dev-to-docs][example-system-github] ou em um link presente na barra de navegação do sistema no canto superior direito.

Obrigado por ler e nos vemos no próximo 🧑🏻‍💻

---

[example-system]: https://sconetto.me/dev-to-docs/
[example-system-github]: https://github.com/sconetto/dev-to-docs
[github-personal]: https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token
[github-secrets]: https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets
[markdown-cheatsheet]: https://devhints.io/markdown
[mkdocs-settings]: https://www.mkdocs.org/user-guide/configuration/
[mkdocs-material-settings]: https://squidfunk.github.io/mkdocs-material/creating-your-site/#advanced-configuration
