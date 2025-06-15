# Introdução ao Cypress: Um Guia Passo a Passo para Testes de Aplicações Web

![Thiago Castilho](https://miro.medium.com/v2/resize:fill:40:40/1*188RxeoNmbffWlmds9oXaA.png)

[Thiago Castilho](https://medium.com/@thiago-castilho?source=post_page---byline--6be295b0557---------------------------------------)

Follow

12 min read

·

May 13, 2023



106







![Imagen com o logo do Cypress](https://miro.medium.com/v2/resize:fit:875/0*CkYF8pNwANy6rgbp.png)

# O que você aprenderá

- Criar um projeto de testes automatizados com Cypress do zero.
- Automatizar o seu primeiro caso de teste.

# Pré-requisitos

- [NodeJS](https://nodejs.org/en/download)
- [Visual Studio Code](https://code.visualstudio.com/download) (ou um editor de texto que preferir)
- Saber o mínimo de lógica de programação
- Conhecimento mínimo em alguma linguagem de programação (utilizaremos JavaScript em nossos testes)

Depois de muito tempo ensaiando, finalmente dei início ao projeto de compartilhar meu conhecimento com a comunidade de QA, e nada melhor que um guia inicial com Cypress para estrear esse novo desafio. Para começarmos sem enrolação, vou considerar que você já tem os pré-requisitos instalados e configurados em sua máquina. Bora lá?

# Introdução

No cenário atual de desenvolvimento de aplicações, a qualidade e a confiabilidade do software são essenciais para o sucesso de um projeto. É aqui que entra o Cypress, uma poderosa e moderna ferramenta de teste de ponta a ponta, que tem ganhado destaque por sua facilidade de uso e recursos avançados. Além de testes de aplicações web, o Cypress também oferece suporte a testes de API, embora o foco deste artigo seja nos testes web. Diferente de outras soluções, como o Selenium, o Cypress proporciona uma experiência de teste mais simplificada, rápida e fácil de configurar. Neste artigo, meu objetivo é apresentar um guia passo a passo para ajudar iniciantes a começarem a utilizar o Cypress no processo de teste de suas aplicações web. Vamos explorar desde a configuração inicial do ambiente de desenvolvimento até a criação e execução do seu primeiro teste.

# Instalação e configuração do projeto

Para criar um projeto do zero com o Cypress, o primeiro passo é criarmos uma pasta com o nome do projeto desejado. Neste exemplo, chamaremos o projeto de ***primeiro-teste-cypress\***. Para simplificar, vou criar o projeto no seguinte diretório: *“****C:/Workspace/primeiro-teste-cypress\****”*.

Com o diretório criado, é hora de criarmos o projeto efetivamente. Vamos entrar na pasta que acabamos de criar e abrir o prompt de comando do windows, ou se preferir pode ser pelo [Git Bash](https://git-scm.com/downloads). Neste exemplo utilizarei o Git Bash.

![Abrindo o diretório do projeto com o Git Bash.](https://miro.medium.com/v2/resize:fit:875/1*b3OvP_EO4XavbjlESd6yHg.png)

Abrindo o diretório do projeto com o Git Bash.

Com o prompt de comando aberto, vamos criar o nosso projeto Node.js com o seguinte comando:

```
**npm init -y**
```

![Criação do projeto Node.js.](https://miro.medium.com/v2/resize:fit:875/1*iv6RqD3p9wCpxoN0nEIWLA.png)

Criação do projeto Node.js.

Note que com este comando um arquivo com o nome “*package.json”* foi gerado no diretório com configurações padrão, que também foram mostradas no prompt de comando. Este arquivo é essencial em um projeto Node.js, pois contém informações sobre o projeto e suas dependências.

Com o projeto criado, o próximo passo é instalar o Cypress como uma dependência de desenvolvimento usando o npm:

```
**npm install cypress --save-dev**
```

![Instalação do Cypress como dependência de desenvolvimento.](https://miro.medium.com/v2/resize:fit:875/1*p0KoCbMfQwpzK-cWri5gnQ.png)

Instalação do Cypress como dependência de desenvolvimento.

O pacote com a versão mais atualizada do Cypress e suas dependências são instalados na pasta “*node_modules”*. Como a opção `**--save-dev**` é usada no comando, o *npm* atualiza o arquivo “*package.json”* do projeto, adicionando o pacote Cypress à seção “*devDependencies”*. Isso significa que o Cypress é uma dependência de desenvolvimento, ou seja, é necessário apenas durante o desenvolvimento e teste do projeto, e não é necessário para a execução do projeto em produção.

![Cypress adicionado às dependências de desenvolvimento no arquivo “package.json”.](https://miro.medium.com/v2/resize:fit:875/1*Y6f-LIB_nvP59J6KpaAmyQ.png)

Cypress adicionado às dependências de desenvolvimento no arquivo “*package.json*”.

O arquivo “*package-lock.json*” é gerado automaticamente quando você executa `**npm install**` (ou instala qualquer pacote com o *npm*) em um projeto que possui um arquivo “*package.json*”. Ele desempenha um papel importante no gerenciamento de dependências e na garantia de que as mesmas versões de pacotes sejam instaladas em todos os ambientes.

# Executando o Cypress pela primeira vez

Cypress instalado, é hora de executá-lo pela primeira vez. No mesmo prompt de comando em que o instalamos, vamos executar o seguinte comando:

```
**npx cypress open**
```

Ao executar este comando, algumas coisas acontecem:

- Pode ser que o Windows emita um Alerta de Segurança (basta permitir o acesso sem medo).

![Alerta do Windows Defender ao executar o Cypress pela primeira vez.](https://miro.medium.com/v2/resize:fit:875/1*gQbKUIPmbeOUtj6ZhdLulA.png)

Alerta do Windows Defender ao executar o Cypress pela primeira vez.

Isso ocorre porque o Cypress é uma ferramenta que controla navegadores e executa código de teste dentro deles, o que pode ser considerado um comportamento suspeito pelo Windows Defender.

- O Cypress abrirá o Cypress Test Runner. O Test Runner é uma interface gráfica que exibe a lista de arquivos de teste (especificações/ *specs*) disponíveis e permite que você execute os testes em um navegador. A partir daqui, você pode executar todos os testes de uma vez ou executar testes individuais conforme necessário.

![Tela inicial do Cypress Test Runner.](https://miro.medium.com/v2/resize:fit:875/1*Uplc_E-3f-EAe3hc37KpdQ.png)

Tela inicial do Cypress Test Runner.

Aqui selecionaremos a opção ***E2E Testing\*** para realizarmos testes de ponta a ponta.

- Ao selecionarmos ***E2E Testing\***, *end-to-end testing* ou testes de ponta a ponta, o Cypress verifica se a estrutura de pastas padrão do projeto já existe. Se não existir, ele criará automaticamente a estrutura de pastas e arquivos de exemplo necessários para começar a escrever testes. Isso inclui a pasta `**cypress**` com subpastas como `**fixtures**` e `**support**`, bem como o arquivo de configuração `**cypress.config.json**`.

![Estrutura padrão criada pelo Cypress.](https://miro.medium.com/v2/resize:fit:440/1*lN79dWTz9kkRBqPKMZyu6w.png)

Estrutura padrão criada pelo Cypress.

Além disso, ele fará uma breve introdução sobre os arquivos de configuração que foram criados. Nessa tela, clicaremos no botão **Continue**.

![Introdução do Cypress aos arquivos de configuração.](https://miro.medium.com/v2/resize:fit:875/1*0QMOtz_2wzUHHm0pw_xaxg.png)

Introdução do Cypress aos arquivos de configuração.

Na tela seguinte, será solicitado a escolha de um navegador para iniciar com os testes, seguiremos com o Google Chrome que já vem selecionado por padrão, e clicaremos em **Start E2E Testing in Chrome**.

![Tela de escolha do navegador para iniciar o desenvolvimento dos testes.](https://miro.medium.com/v2/resize:fit:875/1*cqZ4xr-LbVq3BcBxu6rvtQ.png)

Tela de escolha do navegador para iniciar o desenvolvimento dos testes.

Será aberta uma nova instância do Google Chrome gerenciada pelo Cypress, que carregará a tela para a criação do seu primeiro arquivo *spec*, que é um arquivo de teste que contém as especificações de teste para um determinado conjunto de funcionalidades ou componentes de uma aplicação.

![Tela inicial para a criação do nosso primeiro caso de teste.](https://miro.medium.com/v2/resize:fit:875/1*IoVDjhyluDXiQ9oIgHFuvA.png)

Tela inicial para a criação do nosso primeiro caso de teste.

Nesta tela temos duas opções: **Scaffold example specs** e **Create new spec**. A primeira opção gerará muitos exemplos com diversos tipos de funcionalidades no próprio site do Cypress. Já a segunda opção criará um template de arquivo para criarmos do zero os testes de nossa aplicação. Seguiremos com a opção **Create new spec**.

# Criando nosso primeiro spec

Será solicitado um nome para seu arquivo, vamos chamar este exemplo de ***cadastro.cy.js\*** e podemos clicar em **Create spec** em seguida.

![Nomeando nosso arquivo de teste.](https://miro.medium.com/v2/resize:fit:875/1*KQjRqGF4PzZ26Y04JHuR8g.png)

Nomeando nosso arquivo de teste.

O Cypress mostrará que foi gerado um template base para começarmos com nosso teste. Basta clicar no botão **Okay, run the spec** que ele executará nosso novo teste.

![Criação do template base para início dos testes.](https://miro.medium.com/v2/resize:fit:809/1*H4N6W29_tQhWwgWjpZYhHg.png)

Criação do *template* base para início dos testes.

A execução é bem rápida e o feedback é instantâneo! Como podemos ver na imagem a seguir, o Cypress nos mostra o passo a passo do teste que foi executado na coluna ao lado da imagem, que é a evidência após cada passo executado.

![Execução finalizada com a ilustração do passo a passo e evidências coletadas durante o teste.](https://miro.medium.com/v2/resize:fit:875/1*fugo6tiY58r-G_gkKbhiKQ.png)

Execução finalizada com a ilustração do passo a passo e evidências coletadas durante o teste.

Agora que já temos um template base, vamos abrir nosso projeto no *Visual Studio Code* (ou no seu editor de texto escolhido) para começarmos a desenvolver nosso script de teste.

# Desenvolvendo nosso primeiro caso de teste

Abra seu projeto no editor escolhido. No Visual Studio Code *(VS Code)* podemos abrir seguindo o caminho: **File > Open Folder > Selecionar a pasta do seu projeto**. Ao abrir, vamos expandir a pasta **cypress > e2e** e lá veremos nossa *spec* **cadastro.cy.js** já com o template criado pelo Cypress. Vamos abrir este arquivo e iniciar nosso desenvolvimento.

Dentro de um arquivo *spec*, você escreve suas especificações de teste usando a função `**describe**` para agrupar testes relacionados e a função `**it**` para definir casos de teste individuais. Além disso, você utiliza a API do Cypress para interagir com a aplicação, como visitar páginas, preencher formulários, clicar em botões e verificar elementos e suas propriedades.

Um exemplo simples de um arquivo *spec* que podemos escrever em nosso teste pode ser assim:

```
describe('funcionalidades de cadastro', () => { // Especificação da funcionalidade a ser testada
  beforeEach(() => {
    cy.visit('/'); // Visita a página inicial da aplicação utilizando a API do Cypress com o alias "cy"
  });

  it('cadastrar um novo usuário', () => { // Descrição do cenário de teste
    // Código aqui
  });

  it('cadastrar um usuário já existente', () => { // Descrição do cenário de teste
    // Código aqui
  });
});
```

O `**beforeEach**` é uma função usada para executar um bloco de código antes de cada teste individual (`**it**`) dentro de um grupo de testes (`**describe**`). Essa função é útil para definir configurações, condições iniciais ou ações que são comuns a todos os testes dentro de um grupo específico. Ao usar `**beforeEach**`, você evita a repetição de código e garante que cada teste comece com um estado consistente e previsível. Neste exemplo, evitamos de colocar `**cy.visit()**`repetidamente nos dois cenários de teste (`**it**`).

Utilizaremos o site [https://automationexercise.com](https://automationexercise.com/) para fazer nosso teste. Gosto bastante desse site pois, além de possuir diversos cenários, ele ainda tem casos de teste prontos para treinarmos automação. Para acessarmos esse site, basta colocar o link dento do código dessa forma: `**cy.visit('https://automationexercise.com')**`. Com isso, ao salvarmos o arquivo, o Cypress executará automaticamente de modo muito rápido e você terá o feedback instantâneo!

Nosso código então deve estar dessa forma:

```
describe('funcionalidades de cadastro', () => {
  beforeEach(() => {
    cy.visit('https://automationexercise.com');
  });

  it('cadastrar um novo usuário', () => { 
   // Código aqui
  });

  it('cadastrar um usuário já existente', () => { 
    // Código aqui
  });
});
```

E se repararmos no navegador controlado pelo Cypress, ele já deve ter executado esse novo comando nos dois casos de teste (`**it**`) que inserimos:

![Resultado da execução com o site configurado.](https://miro.medium.com/v2/resize:fit:875/1*Gd9jivpe7H4ZBb7zH-sgJw.png)

Resultado da execução com o site configurado.

# Inspecionando elementos

O Inspector do Cypress é uma ferramenta interativa que ajuda a desenvolver, depurar e entender os testes end-to-end (E2E) enquanto são executados no Cypress Test Runner. Ele permite que você inspecione elementos na aplicação testada, veja o estado do DOM em diferentes pontos do teste e rastreie ações e eventos do Cypress.

Para utilizar é bem simples: Basta clicar no botão de inspecionar, clicar sobre o elemento que deseja identificar, e em seguida copiar o path apresentado, como mostrado no GIF a seguir:

![Exemplo de uso do inspector do Cypress.](https://miro.medium.com/v2/resize:fit:875/1*y3H2ZnfyIKwkNopc5HQ3FQ.gif)

Exemplo de uso do inspector do Cypress.

Após copiar o path, basta colocar em seu código de acordo com as ações que deseja executar. No tópico seguinte mostrarei alguns dos principais comandos mais utilizados do Cypress.

# Principais comandos do Cypress

`**cy.visit(url)**`: Visita uma URL específica da aplicação.

`**cy.get(selector)**`: Seleciona um elemento do DOM usando um seletor CSS.

`**cy.contains(text)**`: Seleciona o primeiro elemento que contém o texto especificado.

`**cy.click()**`: Clica no elemento selecionado.

`**cy.type(text)**`: Digita o texto especificado no elemento selecionado (geralmente campos de entrada).

`**cy.submit()**`: Submete um formulário.

`**cy.reload()**`: Recarrega a página atual.

`**cy.url()**`: Obtém a URL atual da página.

`**cy.title()**`: Obtém o título da página atual.

`**cy.viewport(width, height)**`: Define a largura e a altura da janela do navegador.

`**should(assertion, value)**`**:** Esta função é usada para fazer asserções sobre o estado do elemento ou valor atualmente encadeado.

`**and(assertion, value)**`**:** É usada para encadear várias asserções em um único comando.

`**expect(actual).to.have.something(expected)**`: É usada para fazer asserções fora do contexto de um comando Cypress encadeado.

# Caso de teste

O teste que vamos desenvolver é o primeiro caso de teste sugerido pelo próprio site: Cadastro de usuário. Ele consiste nos seguintes passos:

**1.** Executar o navegador

**2.** Navegar para a *url* [‘](https://automationexercise.com/)[http://automationexercise.com](http://automationexercise.com/)'

**3.** Verificar que a página inicial carregou com sucesso

**4.** Clicar no botão “Signup / Login”

**5.** Validar que ‘New User Signup!’ está visível

**6.** Entrar com nome e e-mail

**7.** Clicar no botão “Signup”

**8.** Validar que a legenda “ENTER ACCOUNT INFORMATION” está visível

**9.** Preencher os campos: Title, Name, Email, Password, Date of birth

**10.** Selecionar o *checkbox* “Sign up for our newsletter!”

**11.** Selecionar o *checkbox* “Receive special offers from our partners!”

**12.** Preencher os campos: First name, Last name, Company, Address, Address2, Country, State, City, Zipcode, Mobile Number

**13.** Clicar no botão “Create Account button”

**14.** Validar que a mensagem “ACCOUNT CREATED!”” está visível

**15.** Clicar no botão “Continue”

**16.** Validar que o nome de usuário “Logged in as $username” está visível

**17.** Clicar no botão ‘Delete Account’

**18.** Validar que a mensagem “ACCOUNT DELETED!” está visível e clicar no botão “Continue”

Agora que temos um caso de teste definido, é hora de inspecionar os elementos necessários e preencher nosso código conforme aprendido no passo anterior. Para uma melhor compreensão, recomendo que você tente fazer esse processo sozinho, e depois compare com meu exemplo. Caso prefira, você pode simplesmente copiar o código que apresento a seguir:

```
describe('funcionalidades de cadastro', () => {

  beforeEach(() => {
    // 1. Executar o navegador
    // 2. Navegar para a url 'http://automationexercise.com'
    cy.visit('https://automationexercise.com');
  });

  it('cadastrar um novo usuário', () => { 
    // 3. Validar que a página inicial carregou com sucesso
    cy.get('a > img').should('be.visible');
    cy.get('.shop-menu > .nav > :nth-child(1) > a').should('be.visible');

    // 4. Clicar no botão “Signup / Login”
    cy.get('.shop-menu > .nav > :nth-child(4) > a').click();

    // 5. Validar que 'New User Signup!' está visível
    cy.get('.signup-form > h2').should('be.visible');

    // 6. Entrar com nome e e-mail
    cy.get('[data-qa="signup-name"]').type('Thiago');
    cy.get('[data-qa="signup-email"]').type('email@teste.com.br');

    // 7. Clicar no botão “Signup”
    cy.get('[data-qa="signup-button"]').click();

    // 8. Validar que a label “ENTER ACCOUNT INFORMATION” está visível
    cy.get(':nth-child(1) > b').should('be.visible');

    // 9. Preencher os campos: Title, Name, Email, Password, Date of birth
    cy.get('#id_gender1').click();
    cy.get('[data-qa="name"]').clear().type('Thiago');
    cy.get('[data-qa="email"]').should('have.value', 'email@teste.com.br');
    cy.get('[data-qa="password"]').type('password');
    cy.get('[data-qa="days"]').select('6');
    cy.get('[data-qa="months"]').select('November');
    cy.get('[data-qa="years"]').select('1996');

    // 10. Selecionar o checkbox “Sign up for our newsletter!”
    cy.get('#newsletter').click();

    // 11. Selecionar o checkbox “Receive special offers from our partners!”
    cy.get('#optin').click();

    // 12. Preencher os campos: First name, Last name, Company, Address, Address2, Country, State, City, Zipcode, Mobile Number
    cy.get('[data-qa="first_name"]').type('Thiago');
    cy.get('[data-qa="last_name"]').type('Castilho');
    cy.get('[data-qa="company"]').type('Study');
    cy.get('[data-qa="address"]').type('Rua A, 123');
    cy.get('[data-qa="address2"]').type('Rua B, 321');
    cy.get('[data-qa="country"]').select('Australia');
    cy.get('[data-qa="state"]').type('São Paulo');
    cy.get('[data-qa="city"]').type('São Paulo');
    cy.get('[data-qa="zipcode"]').type('03416555');
    cy.get('[data-qa="mobile_number"]').type('11912345678');
    
    // 13. Clicar em "Create Account button"
    cy.get('[data-qa="create-account"]').click();

    // 14. Validar que a mensagem "ACCOUNT CREATED!"" está visível
    cy.get('[data-qa="account-created"]').should('be.visible');

    // 15. Clicar no botão "Continue"
    cy.get('[data-qa="continue-button"]').click();
    
    // 16. Validar que o nome de usuário "Logged in as $username" está visível
    cy.get('b').should('have.text', 'Thiago')

    // 17. Clicar no botão 'Delete Account'
    cy.get('.shop-menu > .nav > :nth-child(5) > a').click();

    // 18. Validar que a mensagem "ACCOUNT DELETED!" está visível e clicar no botão "Continue"
    cy.get('[data-qa="account-deleted"]').should('be.visible');
  });
});
```

Para finalizar, vamos salvar o nosso arquivo de teste e aguardar a execução do Cypress:

![Execução completa do nosso caso de teste.](https://miro.medium.com/v2/resize:fit:875/1*lbQvAnvqby3aZDUUtBA6Wg.gif)

Execução completa do nosso caso de teste.

# Entendendo a estrutura de pastas

A estrutura de pastas padrão do Cypress inclui as seguintes pastas e arquivos:

- `**cypress/**`: Esta é a pasta principal do Cypress, onde você encontrará todas as pastas e arquivos relacionados aos testes.
- `**cypress/fixtures/**`: Aqui, você pode armazenar arquivos de dados estáticos que podem ser usados em seus testes, como JSON, imagens ou arquivos de texto.
- `**cypress/e2e/**`: Esta pasta contém os arquivos de teste (especificações / *specs*) que você escreverá. Por padrão, o Cypress cria alguns arquivos de exemplo nesta pasta para ajudá-lo a começar quando a opção **Scaffold example specs** é selecionada.
- `**cypress/plugins/**`: Aqui, você pode estender ou modificar o comportamento do Cypress através de *plugins*.
- `**cypress/screenshots/**`: Quando você executa testes no modo "*headless*" ou captura *screenshots* manualmente, elas serão armazenadas nesta pasta.
- `**cypress/support/**`: Nesta pasta, você encontrará arquivos de suporte que podem conter comandos personalizados ou sobrescrever comandos existentes do Cypress. Os arquivos nesta pasta são executados automaticamente antes de cada teste.
- `**cypress/downloads/**`: Todos os arquivos baixados durante o teste do recurso de download de arquivo de um aplicativo serão armazenados nesta pasta.
- `**cypress.config.js**`: Este é o arquivo de configuração principal do Cypress, onde você pode definir várias opções e configurações globais para seus testes.

# Desafio

Agora deixo aqui o desafio para você escolher um caso de teste existente nesse mesmo site, e automatizá-lo com o Cypress! 😁

# Conclusão

Neste artigo, abordamos como começar com o Cypress, desde a instalação até a execução do seu primeiro teste end-to-end (E2E). Discutimos o uso de arquivos *spec* e a estrutura de pastas padrão. Também exploramos a utilização do *inspector* do Cypress para desenvolver testes.

É fundamental enfatizar a importância dos testes de aplicações web para garantir a qualidade e a confiabilidade do software. O Cypress facilita esse processo, fornecendo uma plataforma poderosa e fácil de usar para a criação de testes E2E.

Espero que tenham gostado deste guia de início rápido com o Cypress! Obrigado por ler até o final, e até a próxima.