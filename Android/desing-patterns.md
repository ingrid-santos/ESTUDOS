# Design Patterns

Um pequeno guia sobre os padrões de design MVC, MVP e MVVM em projetos Android.

## Model View Controller (MVC)

O padrão de design MVC divide a aplicação em três aspectos principais: Model, View e Controller. De tal forma que há uma separação das preocupações, ou seja, o modelo de domínio e a lógica do controlador são desacoplados da interface do usuário (view). Assim, a manutenção e teste da aplicação se tornam mais simples e fáceis.

- __Model:__ o Model representa o conjunto de classes que descreve a lógica de negócios, ou seja, o modelo de negócios assim como as operações de acesso a dados, ou seja, o modelo de dados. Ele também definir regras de negócios para dados significa como os dados podem ser alterados e manipulados.
- __View:__ o View representa os componentes de UI. É responsável apenas por mostrar os dados recebidos do controller como resultado. Assim, transforma os modelos em UI.
- __Controller:__ o Controller é responsável por processar as requisições. Ele recebe entradas do usuário atráves da View, então processa os dados do usuário com ajuda do Model e passa os resultados de volta para a View. Tipicamente, ele age como coordenador entre View e Model.

## Model View Presenter (MVP)

Esse design de padrão é similar ao padrão MVC onde o controlador foi substituido pelo apresentador. Esse padrão de design divide a aplicação em três aspectos principais: Model, View e Presenter.

- __Model:__ o Model representa o conjunto de classes que descreve a lógica de negócios e dados. Também define as regras de negócios para os dados, ou seja,  como eles podem ser alterados e manipulados.
- __View:__ o View representa os componentes de UI. É responsável apenas por mostrar os dados recebidos do presenter como resultado. Assim, transforma os modelos em UI.
- __Presenter:__ o Presenter é responsável por lidar com todos os eventos de UI em nome da View. Ele recebe os dados de entrada do usuário através da View, processa os dados com ajuda do Model e repassa os resultados de volta pra View. Diferentemente da View e do Controller, View e Presenter são completamente desacoplados de cada um e se comunicam via interface. Além disso, o Presenter não gerencia o tráfico de requisições como o Controller.
  
  __Pontos chave sobre o MVP__
  - usuário interage com a View.
  - existe uma relação de um para um entre View e Presenter, o que significa que uma View é mapeada para apenas um Presenter.
  - View tem uma referência para o Presenter, mas View não tem referência para o Model.
  - provê dois caminhos de comunicação entre View e Presenter.

## Model View ViewModel (MVVM)

Esse padrão suporta a vinculação de dados bidirecional entre o modo de exibição e o modelo de exibição. Isso permite a propagação automática de alterações, dentro do view model para a View. Normalmente, o model view usa o padrão observador para notificar mudanças no model view para model.

- __Model:__ o Model representa o conjunto de classes que descreve a lógica de negócios e dados. Também define as regras de negócios para os dados, ou seja, como eles podem ser alterados e manipulados.
- __ViewModel:__ o ViewModel é responsável por expor métodos, comandos e outras propriedades que ajudam a manter o estado da view, manipulam o modelo como resultado de ações na exibição e acionam eventos na própria view.

    __Pontos chaves do MVVM__
    - usuário interage com a View.
    - existe uma relação de muitos para um entre View e ViewModel, o que significa que várias Views podem ser mapeadas para uma ViewModel.
    - View tem uma referência para o ViewModel, mas ViewModel não possui informações sobre a View.
    - suporta vinculação de dados bidirecional entre View e ViewModel.
