# Automação de testes full stack com Cypress

- [Testes](https://zup.com.br/categorias/testes-pt)
- • 29 abr 2021
- 

#### Neste artigo você vai ver:

- [Entendendo o que é Cypress](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
  - [Instalações necessárias para iniciar um projeto Cypress](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
    - [Instalando o cypress via cmd:](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
- [Automação de testes API REST com Cypress](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
  - [Entendendo o que é API REST](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
  - [Primeiro script de teste automatizado com API REST](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
- [Automação de testes front-end com Cypress](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
  - [Entendendo o que é front-end](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
  - [Primeiro script de teste automatizado front-end](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)
- [Cypress: uma ferramenta poderosa de automação de testes!](https://zup.com.br/blog/automacao-de-testes-cypress#texto-blog)

**Automação de testes** é um tema muito interessante, mas que ainda gera muitas dúvidas nas pessoas. Por isso, criei esse tutorial usando **Cypress** para automatizar testes com API REST e com front-end usando a linguagem JavaScript.

Um fator interessante para a utilização do Cypress é que conseguimos **partir do zero ao primeiro script de automação em poucos minutos** e é verdade esse “bilete”. Vamos começar?

## **Entendendo o que é Cypress**

O **Cypress é um framework para automação de testes end-to-end**, onde atualmente usa a linguagem JavaScript e roda em vários navegadores como Chrome, Firefox, Edge, entre outros.

Suas principais vantagens são:

- Instalação e configuração rápida e fácil;
- Roda em vários navegadores;
- Boa quantidade de retorno de erros;
- Rápido e seguro.

### **Instalações necessárias para iniciar um projeto Cypress**

- Node.js, para baixar

   

  clique aqui

  .

  - Após baixar, basta realizar *next*/*next* até o final.

- npm (gerenciador de pacotes JavaScript).

  - Já vem com o Node.js

- Cypress

- Editor de texto ou IDE (utilizaremos o VS Code, [clique aqui](https://code.visualstudio.com/download) para baixar).

Para garantir que tudo está instalado, abra o *cmd* e digite os comandos abaixo:

- ***node –version\***

```bash
C:\Users\luan>node --version
v12.18.4
```

- ***npm –version\***

```bash
C:\Users\luan>npm --version
6.14.6
```

#### **Instalando o cypress via** ***cmd\***:

- Criar uma pasta onde irá instalar o projeto cypress.
- Executar o comando ***npm init -y\*** para criar o arquivo ***package.json.\***

```bash
C:\Users\luan\cypress-fullstack>npm init -y
Wrote to C:\Users\luan\cypress-fullstack\package.json:

{
  "name": "cypress-fullstack",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

- Executar o comando ***npm install cypress\*** para baixar e instalar as dependências do cypress.

```bash
C:\Users\luan\cypress-fullstack>npm install cypress
npm WARN deprecated har-validator@5.1.5: this library is no longer supported

> cypress@6.3.0 postinstall C:\Users\luan\cypress-fullstack\node_modules\cypress
> node index.js --exec install


Installing Cypress (version: 6.4.0)

  √  Downloaded Cypress
  √  Unzipped Cypress
  √  Finished Installation C:\Users\luan\AppData\Local\Cypress\Cache\6.4.0
```

- Abra a pasta no VS Code ou no editor de texto de sua preferência.
  - Caso utilize o VS Code, pode-se digitar ***code .\*** no cmd.
- Note que ainda está faltando os arquivos necessários do Cypress, portanto realize os passos após o print abaixo:

![Raiz inicial das pastas após instalação do cypress no vscode, sendo a principal a pasta cypress-fullstack, dentro dela a node_modules e os arquivos package-lock.json e package.json.](https://lh3.googleusercontent.com/IJkpUy03I0yl_SSjnFOvnrAwxRPvPeOSCYbxL6jsefYUohSIy77XqcsmHJOHyHkrALbNt9G_7RQnOGa-bZoscKAffgKmgmFXPwK1bOUQArHhfhbrn4FPg-oqT4ksmChZs4S3Ht94)

Edite o arquivo package.json inserindo o comando abaixo em “*scripts*”:

“open”: “cypress open”

```bash
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "open": "cypress open"
}
```

Execute o comando ***npm run open\*** via *cmd.* 

O Cypress abrirá uma interface bastante amigável para acompanhar a execução dos testes enquanto os arquivos *specs* são editados.

![Print da interface amigável que o Cypress abre.](https://lh5.googleusercontent.com/vdEHcSr8AiVU4lKHAFKOvQL4jrtgG0kbPCWXUsVQrCn5azlimsz7czMU1h97k9P6OEOWnbVReXqyMYdbo3NFhCXuxKfsZwHJnTyL_8nv34I6EiWrHZjwnXgp-A92LVhE8kZpnxi4)

- Verifique que os arquivos padrões do cypress foram criados.

![Raiz inicial das pastas após iniciar o cypress, sendo a principal a pasta cypress-fullstack, dentro dela a cypress, fixtures, integration, plugins e support.](https://lh6.googleusercontent.com/-7h9yjGo0-H38pNH6-60DDl0QIjwdIHY54c2BgumDr2PTKDsMKnMzMnyxlIkJ1InnhLZAEocaZVI_-1feblajRK5BvTWs5VC80pnwfxqYh165NUHiFLf9I9B6gfP4eSJvf5HgQIT)

## **Automação de testes API REST com Cypress**

Vamos começar nosso **tutorial de automação de testes com Cypress** com as API REST. Vamos entender de forma simples e objetiva como funcionam as **API REST**, o que precisamos para iniciar um projeto de automação de testes com Cypress usando JavaScript e passo a passo para realizar o primeiro teste automatizado com uma chamada GET.

### **Entendendo o que é API REST**

As **API’s servem para que haja comunicação entre aplicações e usuários de forma simplificada**, utilizando padrões de requisições que executam determinadas funções. Elas podem ser representadas em alguns formatos, sendo os mais conhecidos e utilizados: XML, JSON e YAML.

Já o ***REST\*** é a **Transferência de Estado Representacional** onde contém regras que permitem que as aplicações se comuniquem. O *REST* usa como protocolo de comunicação o *HTTP*, tendo inúmeras formas de requisições (verbos) sendo os mais utilizados: ***GET\***, ***POST\***, ***PUT\*** e ***DELETE:\***

- **GET**: recupera a representação de objetos e retorna status 200 quando com sucesso.
- **POST**: cria objetos e retorna o código 201 quando com sucesso.
- **PUT**: atualiza ou cria objetos retornando 200 ou 201.
- **DELETE**: exclui objetos retornando status 200.

### **Primeiro** ***script\*** **de teste automatizado com API REST**

Nesta sessão iremos seguir um passo a passo de como automatizar um GET simples usando o ***request\*** do Cypress. Para isso, usaremos *Dummy api example* no caminho http://dummy.restapiexample.com/api/v1/employees

- Crie um arquivo na pasta “

  integration

  ” com o nome

   

  rest.spec.js.

  - primeiro temos que importar o cypress inserindo o código abaixo:

```bash
/// <reference types="cypress" />
```

- Em seguida criaremos o escopo do teste usando o **it**

```bash
it('Deve realizar um GET simples', () => {
 
})
```

- Dentro do **it** usaremos o request do cypress para realizar o GET já pegando o resultado da requisição e mostrando no console do chrome, ficando da seguinte forma:

```bash
it('Deve realizar um GET simples', () => {
    cy.request({
        method: 'GET',
        url: 'http://dummy.restapiexample.com/api/v1/employees',
    }).then(res => {
        console.log(res)
    })
})
```

- A execução do teste retorna status sucesso 200 e ficará da seguinte forma:

![Print do resultado "status sucesso 200". ](https://lh4.googleusercontent.com/pYXCsourPRdZTnRcl0wMAPqJ4pCNHfXW-boXmGyVf2EpBn-kWWPBAGTNlXVfu8sVAmSLQY8T_iPOwp9PON0xC2Kg7QiCCLWxJ5A3Dhc7XSr7QBHFgeYinWcsXQYfVScezek9Erig)

- Inspecionar a página e na aba “Console” irá trazer o objeto de retorno da requisição, conforme aprendemos no início dessa documentação.

![img](https://lh3.googleusercontent.com/4axYhvCB2r2du6Ptq24_Brd0ql2AumcODfmqIxe-88L3A0taOwscrjMbdx7XlPvNar0SBQQmzE2BpY9eVURMp0cXyuLzj2Jd4jLBYDTvayALumR6dtkLxdrP9yNAFSswa0tN-V1I)

- Agora só falta realizarmos validação de que:
  - O status da requisição foi realizado com sucesso e retornou 200;
  - O retorno não foi vazio;
  - O primeiro elemento possui as propriedades: *id*, *employee_name*, *employee_salary*, *employee_age* e *profile_image;*

```bash
it('Deve realizar um GET simples', () => {
    cy.request({
        method: 'GET',
        url: 'http://dummy.restapiexample.com/api/v1/employees',
    }).then(res => {
        expect(res.status).to.be.equal(200)
        expect(res.body.data).is.not.empty
        expect(res.body.data[0]).to.have.property('id')
        expect(res.body.data[0]).to.have.property('employee_name')
        expect(res.body.data[0]).to.have.property('employee_salary')
        expect(res.body.data[0]).to.have.property('employee_age')
        expect(res.body.data[0]).to.have.property('profile_image')
    })
})
```

![img](https://lh3.googleusercontent.com/TI9GFtLwzP-4VpCLbpBGGtJHEd-B7EIxyMNtEZi0tUHymczG7dzg0dTSWlRkGiF2VGrV4E7YrlOxXryvQVZP227SlqXpCQF6THfntBGF8bM3XiL8kT0jaJAhvcQgL2Z3o6ZOtTC3)

Legal, né?

## **Automação de testes front-end com Cypress**

Agora vamos entender de forma simples e objetiva sobre o *front-end*, o que precisamos para iniciar um projeto de **automação de testes com Cypress** usando JavaScript e passo a passo para realizar o primeiro teste automatizado em uma plataforma de teste em *e-commerce*.

### **Entendendo o que é front-end**

**Front-end é basicamente a parte que vemos e interagimos em sites e aplicações web e mobile**. Nela, o desenvolvedor é responsável pela experiência do usuário (UX) por meio do sentido visual no site ou aplicativo, desenvolvendo a interface gráfica em HTML, CSS e JavaScript (dentre outras linguagens).

Toda essa programação é processada diretamente pelo navegador que o usuário está utilizando, para que o mesmo seja apresentado de acordo com a resolução do equipamento utilizado.

### **Primeiro** ***script\*** **de teste automatizado front-end**

Nesta sessão iremos seguir um passo a passo de como automatizar um *login* usando o ***visit\*** do Cypress. Para isso usaremos uma plataforma de testes simulando um *e-commerce*, o [*Automation Practice*](http://automationpractice.com/index.php)**.**

- Crie um arquivo na pasta “

  integration

  ” com o nome

   

  *front.spec.js.*

  - Primeiro temos que importar o cypress inserindo o código abaixo:

```bash
/// <reference types="cypress" />
```

- Em seguida criaremos o escopo do teste usando o **it:**

```bash
it('Deve realizar Login com sucesso', () => {
 
})
```

- Dentro do **it** usaremos o ***visit\*** do cypress para acessar a página, ficando da seguinte forma:

```bash
it('Deve realizar Login com sucesso', () => {
    cy.visit('http://automationpractice.com/index.php')
})
```

- Executar o teste clicando sobre o arquivo criado:

![Print da Tela do Cypress mostrando os arquivos criados.](https://lh5.googleusercontent.com/K8Giw34T1Arzw-k58ghtElSFa0WWH3BWXqbvccSoPIH-7AoTDYTneY815QhymIJvfPZQdCdrAuNEpAyEmdlxvn96JjpZ8DxBotXRn6vXgm_lCIUi1RBZuwQsOJVfLe__ANGTUND8)

- Usando o próprio Cypress, iremos pegar os elementos e interagir com eles, começando pelo botão

   

  *Sign in*

  . Siga os passos abaixo:

  - Ainda com a interface do Cypress aberta, clicar no ícone![img](https://lh4.googleusercontent.com/qfN6nVKtH1Ef770kmrRE9szn7zdKRynomxlq3NV0SQj9R28T5VbrZ4PeIJK5YQa4YH-pjGzg9u17zNYjdnOFm-Lq7EVZhMSlXDjT-T3Q_JNn_1OoEDOFeElUTJK4WN6iVDv5IcYW)(ícone de uma mira com nome *Open Selector Playground)* na parte superior da página para selecionar e “pegar” os elementos com o ***get\*** do Cypress. Com esse funcionalidade habilitada, clique no botão Sign in e teremos o seguinte comportamento:

![Print da tela do site usado para praticar automações no front-end onde podemos ver os ícones e comandos citados no paragrafo anterior. ](https://lh5.googleusercontent.com/0U2SkW380G-LwKXjXuLEVNHEDiIECz1V8G-76W9xUYneIKdaWguMHK99JoMJkM4MXKWbWB0cknQr2POY_1ufET-MhX5IUmn9HP7ZDKf7sOJzqeNrAHYB4kIEZ2mAqHTI_Wg9vhO3)

- Note que ele preenche o cy.get com a propriedade ***class\*** do elemento, sendo uma ótima forma para interagir. Clique no ícone![img](https://lh3.googleusercontent.com/SJFkvxZQFbNszVhOHD1_PVnM5El3WK03MFdRnuXV4s2KPzdjm0bd8mHarpTSPfEPkNzLNNCpeoNLnfGBhZPDI7KZ4KY5kfncGTWpfX-x7FyLCj0f6MQ_tjy6s92FGu6Z38m-90ZA)(ícone de duas folhas em branco com nome *Copy to clipboard*) para copiar o cy.get completo.

- Retorne ao código e cole o caminho copiado. Complete para que o Cypress clique no botão, ficando da seguinte forma:

```bash
it('Deve realizar Login com sucesso', () => {
    cy.visit('http://automationpractice.com/index.php')
    cy.get('.login').click()
})
```

![Print da tela do site usado para praticar automações no front-end onde podemos ver os resultados dos comandos executados.](https://lh6.googleusercontent.com/I49HalMikxpHD245ubM9K6u_HV1LzEf24MZy8xV2OOG-v7x6XYyJCQ_9eBQ4RqQstyLMiICNtaSBROAGjvKo92FDYqUkZ3TyAnhSjSWPvajsPpzRYCbGuxMAtn0clfuDKvnNne52)

- Agora vamos repetir o processo cy.get nos campos ***Email address\***, ***Password\*** e botão ***Sign in\***. Cole os caminhos no código e solicite ao Cypress para digitar o e-mail e senha de acesso e clicar no botão, ficando assim:

```bash
it('Deve realizar Login com sucesso', () => {
    cy.visit('http://automationpractice.com/index.php')
    cy.get('.login').click()
    cy.get('#email').type('teste2021@teste.com.br')
    cy.get('#passwd').type('teste')
    cy.get('#SubmitLogin > span').click()
})
```

![Print da tela do site usado para praticar automações no front-end onde podemos ver os resultados dos comandos executados.](https://lh4.googleusercontent.com/1YDSFGVbqkX7J4BgptD5heHhNjwEt5nNiLuAzQ7KEorzeRujcfVIoNOSEGN_o0wnaDRCaPCWWAD4Hlho377T2H0PyjASF1fGbFgJn12c1SBifld9mvjcmfaq0ksH0PAY3LOcDYnN)

- Agora só falta realizarmos validação de que:

- O login foi realizado com sucesso por meio de qualquer elemento da tela após o login. Aqui vamos fazer a validação de que o botão ***MY WISHLISTS\*** existe.

```bash
cy.get('.lnk_wishlist > a > span').should('exist')
```

![Print da tela do site usado para praticar automações no front-end onde podemos ver os resultados dos comandos executados.](https://lh3.googleusercontent.com/ziJ0esZaf7fd0vhTeCTvOlt4ykGn-Qg6XDj6R1z4LHaBAIdKXUFKGOhl5gcCTuKTVXwPTXamxuNet2cvJonf3ref3CtbCP-Hm7rtDvXKPifHAN2VFRFOq14JlJ4zQlizvg_1mCKo)

Note que ao fim ele verifica o botão com a característica “existe” para garantir que o login foi realizado com sucesso.

Gostou desse tutorial? O [*Automation Practice*](http://automationpractice.com/index.php) pode ser muito útil para esse e outros testes!

## **Cypress: uma ferramenta poderosa de automação de testes!**

Parabéns, você chegou ao fim do nosso tutorial básico para iniciar um projeto de testes automatizados full stack, tornando sua vida mais ágil e assertiva!

Me conta o que achou do tutorial? Deixe suas dúvidas e sugestões nos comentários! 