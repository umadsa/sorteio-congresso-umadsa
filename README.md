# sorteio-congresso-umadsa
Sorteio Oficial – Congresso UMADSA 2025™
# Sistema de Sorteio e Captação de Leads (Google Apps Script)

Este é um projeto de captação de leads construído 100% com Google Apps Script, utilizando uma Planilha Google como banco de dados. Ele permite que usuários se cadastrem em um formulário web, gerem um número da sorte e consultem um dashboard de métricas.

## Funcionalidades

* **Formulário de Cadastro:** Página (`sorteio.html`) com design responsivo para inserir Nome, Sobrenome, Telefone e Email.
* **Validação de Duplicidade:** O sistema não permite que o mesmo número de telefone seja cadastrado duas vezes.
* **Geração de Código:** Gera um código de sorteio único baseado no DDD e nos últimos 4 dígitos do telefone (ex: `S-111234`).
* **Ticket para Download:** O usuário pode baixar uma imagem (PNG) do seu número da sorte.
* **Recuperação de Código:** Um modal permite que o usuário recupere seu código por e-mail.
* **Atualização de E-mail:** Se o usuário não forneceu um e-mail no cadastro, o e-mail usado na recuperação é salvo na planilha.
* **Dashboard:** Uma página protegida (`dash.html`) que exibe o total de inscritos e o total de e-mails capturados.

---

## Como Instalar

Siga estes 4 passos para configurar o projeto.

### Passo 1: Criar a Planilha (Banco de Dados)

1.  Crie uma nova **Planilha Google**.
2.  Copie o **ID da Planilha** da URL. (Ex: `.../d/`**`1O8fAeN...Pbz4Ngk`**`/edit...`)
3.  Renomeie a primeira aba (página) para exatamente: `Inscricoes_Sorteio`
4.  Na **Linha 1** desta aba, crie os seguintes cabeçalhos, um em cada coluna:
    * `Timestamp`
    * `Nome`
    * `Sobrenome`
    * `Telefone`
    * `Telefone_Normalizado`
    * `Email`
    * `Consentimento`
    * `CodigoSorteio`
    * `Status`

### Passo 2: Criar o Google Apps Script

1.  Acesse [script.google.com](https://script.google.com) e crie um **Novo Projeto**.
2.  No arquivo `Code.gs` padrão, apague todo o conteúdo e cole o conteúdo do arquivo `Code.gs` deste repositório.
3.  Clique no `+` na barra lateral "Arquivos" e selecione **HTML**. Nomeie o arquivo como `sorteio.html` (sem o `.html`).
4.  Apague o conteúdo padrão e cole o conteúdo do arquivo `sorteio.html` deste repositório.
5.  Clique no `+` novamente e crie outro arquivo **HTML** chamado `dash.html`.
6.  Apague o conteúdo padrão e cole o conteúdo do arquivo `dash.html` deste repositório.

### Passo 3: Configurar o Script

1.  Volte ao arquivo `Code.gs`.
2.  Na linha 6, cole o **ID da Planilha** que você copiou no Passo 1 na variável `SPREADSHEET_ID_SORTEIO`.
3.  Salve o projeto (ícone de disquete).

### Passo 4: Implantar o Aplicativo Web

1.  No canto superior direito, clique em **Implantar** > **Nova implantação**.
2.  Clique no ícone de engrenagem (ao lado de "Selecionar tipo") e escolha **Aplicativo da web**.
3.  No campo "Executar como", selecione **"Eu (seu e-mail)"**.
4.  No campo "Quem pode acessar", selecione **"Qualquer pessoa"**. (Isso é crucial para que o público possa se inscrever).
5.  Clique em **Implantar**.
6.  Autorize os serviços do Google (planilhas, e-mail) quando solicitado.
7.  Copie a **URL do aplicativo da web** fornecida.

### Como Usar

* **Página de Inscrição:** A URL do aplicativo da web (ex: `.../exec`) é o formulário de inscrição.
* **Página do Dashboard:** Adicione `?pagina=dash` ao final da URL do aplicativo (ex: `.../exec?pagina=dash`).
