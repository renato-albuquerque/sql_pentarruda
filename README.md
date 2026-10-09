# Projeto sql_pentarruda

Time envolvido: <br>
[Renato Albuquerque](https://www.linkedin.com/in/renato-malbuquerque/) <br>
[Kleber Freitas](https://www.linkedin.com/in/kleber-freitas-2795227b/) <br>
[Arruda Consulting](https://www.linkedin.com/company/arrudaconsulting/)

## 1. Arquitetura do Projeto
![imagem_arquitetura_projeto](images/arquitetura_projeto.jpg)

## 2. Configuração inicial do projeto (Git & GitHub)
Passo a passo para criar o projeto com [uv](https://docs.astral.sh/uv/) e vinculá-lo a um repositório no GitHub.

### 2.1. Criar a pasta do projeto
No Windows, crie a pasta que abrigará o projeto (ex.: `sql_pentarruda`).

### 2.2. Inicializar o projeto com uv
Abra o terminal dentro da pasta do projeto e execute:
```bash
uv init
```

Isso cria a estrutura básica (`pyproject.toml`, `main.py`, `README.md`, `.python-version`) e inicializa um repositório Git local.

### 2.3. Criar o repositório no GitHub
No GitHub, crie um novo repositório **vazio** (sem README, `.gitignore` ou licença), para evitar conflitos no primeiro push.

### 2.4. Vincular a pasta local ao GitHub
No terminal, na pasta do projeto, seguir os passos do GitHub:
```bash
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/renato-albuquerque/sql_pentarruda.git
git push -u origin main
```

### 2.5. Verificação
Atualize a página do repositório no GitHub: os arquivos do projeto devem aparecer lá. Para conferir pelo terminal:
```bash
git remote -v
```

O resultado deve mostrar a URL do repositório para `fetch` e `push`.

### 2.6 Fluxo de trabalho no dia a dia
```bash
git add .
git commit -m "descrição da alteração"
git push
```

### 2.7. Observações
- `uv add <pacote>` adiciona dependências Python ao projeto (ex.: `uv add pandas`).

## 3. Preparação do Ambiente

### Instalação WSL (Windows Subsystem for Linux)
É um recurso do Windows que permite executar um ambiente Linux de forma nativa no computador, sem precisar de uma máquina virtual separada. <br>
[Informações sobre a instalação](https://learn.microsoft.com/pt-br/windows/wsl/install) <br>
Como apoio para instalação, sugestão vídeo Eng. Dados Iury Rosal: <br>
[Instalando WSL | Preparação de Ambiente Moderno para Engenharia de Dados #1](https://www.youtube.com/watch?v=nLgn43SYVU0&t=4s) 

### Instalação Docker Desktop
O Docker é uma plataforma de software de código aberto usada para criar, testar e implantar aplicativos rapidamente por meio de contêineres. <br>
Um contêiner empacota o código de um aplicativo junto com todas as suas dependências, bibliotecas e arquivos de configuração. <br>
Ele funciona de forma isolada do restante do sistema, garantindo que o programa rode igual em qualquer computador. Diferente de uma máquina virtual, o contêiner compartilha o núcleo (kernel) do sistema operacional da máquina principal, o que o torna muito mais leve e rápido. <br>
[Informações sobre a instalação](https://docs.docker.com/desktop/setup/install/windows-install/) <br>
Como apoio para instalação, sugestão vídeo Eng. Dados Iury Rosal: <br>
[O que são containers e como lidar com eles com Docker | Introdução e Instalação](https://www.youtube.com/watch?v=je54-rHZVx4&t=5s)

### Dockerfile
Parametrização do ambiente. <br>

1. Na pasta do projeto, criar arquivo Dockerfile. <br>
Comando no PowerShell: New-Item Dockerfile -Type File <br>
2. Abrir arquivo DockerFile. <br>
Comando no PowerShell: notepad C:\Users\...\Dockerfile <br>
Ou abrir arquivo "clicando" em Dockerfile.
3. Inserir informações no arquivo Dockerfile: <br>
FROM postgres <br>
RUN localedef -i pt_BR -c -f UTF-8 -A /usr/share/locale/locale.alias pt_BR.UTF-8 <br>
ENV LANG pt_BR.utf8 <br>
Salvar e fechar arquivo.

### Criar/Construir a imagem do Postgres
Comando no PowerShell: docker build -t sql_pentarruda . <br>
Obs.: Docker Desktop precisa está "rodando, running". <br>
Resultado: Imagem criada no Docker Desktop. Checar no menu "Images". 

### Criar o container do Postgres
Comando no PowerShell: docker run -d -p 5436:5432 -e POSTGRES_PASSWORD=123 -e POSTGRES_USER=postgres -e POSTGRES_DB=treinamento -e LANG=pt_BR.utf8 -e LC_ALL=pt_BR.UTF8 sql_pentarruda <br>
Resultado: Container criado no Docker Desktop. Checar no menu "Containers". 

### Instação Dbeaver


### Instalação SQL Power Architect


