# Android Architecture Components

O Android Architecture Componentes é uma coleção de bibliotecas que ajudam a desenvolver aplicações robustas, testáveis e sustentáveis. Ou seja, essa biblioteca busca ajudar a gerir o ciclo de vida das UIs e gerir melhor a persistência de dados mesmo com as alterações no _Lifecycle_ da aplicação. Os componentes nessa biblioteca são:

- __Lifecycle:__  classe responsável por guardar informação sobre o ciclo de vida de uma activity/fragment (seus estados e eventos). Por ser uma classe abstrata, para usar esta classe, utiliza-se o _LifecycleObserver_
- __LifecycleOwner:__ interface que possui apenas um método: _getLifecycle()_ que devolve o Lifecycle da Activy/Fragment. Essa interface serve simplesmente para dizer que a activity tem um objeto _Lifecycle_
- __ViewModel:__ _classe_ capaz de sobreviver à alterações de estado do ciclo de vida da activity/fragment. Ou seja, mesmo que o usuário gire o dispositivo (de _portrait_ para _landscap_ ou vice-versa), o ViewModel mantém o seus estado e os seus dados.
- __Room:__ biblioteca que visa facilitar o uso de base de dados SQLite. È semelhante ao _realm_ e/ou o _SugarORM_

# Lifecycle

Classe responsável por guardar informações sobre o ciclo de vida de uma activit/fragments. Mas o que são esses _estados_ e _estados_?

## Eventos

Representa o evento do ciclo de vida que é chamado quando acontece uma alteração no ciclo de vida (por exemplo, voltar a abrir uma activity). Na biblioteca Components há algumas _Annotations_ para utilizarmos quando queremos definir os métodos que devem ser chamados na alteração de eventos de ciclo de vida. Os eventos que podem ocorrer são:

- __ON_CREATE__ - quando o _LifecycleOwner_ é criado. (Corresponde ao _onCreate_ do Android framework)
- __ON_DESTROY__ - quando o _LifecycleOwner_ é destruído. (Corresponde ao _onDestroy_ do framework)
- __ON_PAUSE__ - quando o _LifecycleOwner_ é pausado. (Corresponde ao _onPause_ do framework)
- __ON_RESUME__ - quando _LifecycleOwner_ é resumido. (Corresponde ao _onResume_ do framework)
- __ON_START__ - quando _LifecycleOwner_ é iniciado. (Corresponde ao _onStart_ do framework)
- __ON_STOP__ - quando o _LifecycleOwner_ é parado. (Corresponde ao _onStop_ do framework)
- __ON_ANY__ - chamdo quando ocorre qualquer tipo de evento no ciclo de vida do _LifecycleOwner_ (Qualquer um dos eventos mencionados acima)

## Estados

Servem para indicar o ponto em que o _LifecycleOwner_ se encontra no ciclo de vida. Sempre que ocorre um evento há também uma mudança de estado.

![diagrama de mudanças de estado](/home/ingrid/Documentos/Estudos/Android/diagrama-estados.png)

Existem 5 estados:

- __INITIALIZED__ - o estado em que fica o _LifecycleOwner_ antes do seu primeiro evento (antes de ser criado).
- __CREATED__ - o estado depois do __ON_CREATE__, mas antes do __ON_START__. E também depois do __ON_STOP__ e antes do __ON_DESTROY__.
- __STARTED__ - o estado depois do __ON_START__, mas antes do __ON_RESUME__. E também depois do __ON_PAUSE__ e antes do __ON_STOP__.
- __RESUMED__ - o estado depois do __ON_RESUME__.
- __DESTROYED__ - o estado depois do __ON_DESTROY__.

A classe _Lifecycle_ possui o método  _getCurrentState()_ que é usado para sabermos em que estado estamos. Além desse método, há mais dois métodos:

- __addObserver()__ - utilizado para adicionar um _Observer_ que é notificado sempre que ocorrem alterações no ciclo de vida do _LifecycleOwner_.
- __removeObserver()__ - utilizado para remover o _Observer_ que está no _LifecycleOwner_. É uma boa prática chamar esse método no evento  __ON_DESTROY__ do _Observer_, ao invés de chamá-lo no _onStop()_ do _LifecycleOwner_, pois assim o _LifecycleOwner_ terá apenas o _onCreate()_ e nada mais.
