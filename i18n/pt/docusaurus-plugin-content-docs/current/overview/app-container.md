---
sidebar_position: 3
---

# App Container

O Expresso TS usa **[InversifyJS](https://inversify.io/)** como seu ioC (Inversão de Controle) container, pois é uma ferramenta poderosa para gerenciar injeção de dependência. O Inversify é um container com suporte a tipos que pode ser utilizado para gerenciar a instância e resolução de objetos, bem como o gerenciamento do ciclo de vida deles.

O contêiner fornece um local central para gerenciar dependências e criar objetos que dependem de outros objetos. Quando uma classe é registrada no contêiner, suas dependências são automaticamente resolvidas e injetadas em seu construtor quando ela é instanciada. Isso permite a criação de gráficos de objetos complexos com um mínimo de código boilerplate.

Aproveitando o InversifyJS, criamos um wrapper para reduzir a complexidade sobre como os controladores, casos de uso e provedores são injetados no contêiner de aplicativos. O wrapper é chamado de AppContainer e é responsável por registrar todos os módulos da aplicação no contêiner.

Aqui está um exemplo de como registrar **[módulos](./module.md)** no container:

```typescript
// Criar novo container
const appContainer = new AppContainer();

const container = appContainer.create([
    // Registrar todos os módulos
    UserModule,
    PaymentModule,
    ProductModule
]);

export default container;
```

A classe `AppContainer` tem um método `create` que recebe um array de módulos e retorna o contêiner com todos os módulos registrados. O contêiner aqui criado é o mesmo contêiner usado pela classe `Application` para inicializar o servidor.

:::note
O InversifyJS contém uma função auxiliar chamada `buildProviderModule()` que pode ser usada para criar um módulo que registra automaticamente todos os provedores e controladores em um determinado diretório.

A função recebe um argumento do tipo string que representa o caminho para o diretório contendo as classes de provedores e controladores, e retorna um módulo que pode ser registrado no contêiner InversifyJS. O módulo registrará automaticamente todas as classes de provedores e controladores no diretório e seus subdiretórios.

Essa é uma funcionalidade útil ao construir grandes aplicações com muitos provedores e controladores, pois permite registrá-los facilmente sem precisar registrá-los manualmente um por um.

Observe que buildProviderModule() funciona apenas com provedores e controladores que são decorados com o decorador @injectable().
:::

A razão pela qual criamos a classe `AppContainer` é reduzir a complexidade de como o container é criado e fornecer uma maneira de registrar módulos sem muita configuração extra.

---

## Apoie o projeto

Expresso TS é um projeto de código aberto licenciado sob o MIT. É um projeto independente com desenvolvimento contínuo possibilitado graças ao seu suporte. Se você deseja ajudar, por favor considere:

- Se tornar um **[Sponsor no GitHub](https://github.com/sponsors/expressots)**
- Siga a **[organização](https://github.com/expressots)** no GitHub e de um Star ⭐ no projeto
- Subscreva no nosso canal na Twitch: **[Richard Zampieri](https://www.twitch.tv/richardzampieri)**
- Entre no nosso **[Discord](https://discord.com/invite/PyPJfGK)**
- Contribua submetendo **[issues e pull requests](https://github.com/expressots/expressots/issues/new/choose)**
- Compartilhe o projeto com seus amigos e colegas