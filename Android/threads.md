# Threads

Quando uma aplicação Android é iniciada, o sistema cria a primeira Thread de execução,conhecida como _MainThread_. A MainThread é responsável por despachar os eventos para os widgets apropriados do usuário assim como a comunicação com os componentes kit de ferramentas do Android UI. Para manter a aplicação responsiva é essencial evitar usar a MainThread para performar qualquer operação que possa acabar impedindo o bloqueio.

O Android provê diversas maneiras de criar e gerenciar threads, e muitas bibliotecas de terceiros existem para fazer o gerenciamento de threads mais agradável. No Android, podemos categorizar todos os componentes de threading em duas categorias básicas:

1. __Threads que _são_ anexadas a uma activity/fragment:__ essas threads estão vinculadas ao ciclo de vida da activity/fragment e são finalizados assim que a activity/fragment é destruída.
2. __Threads que _não são_ anexadas a nenhuma activity/fragment:__ essas threads podem continuar a ser executados além do ciclo de vida da activity/fragment (se houver algum) do qual eles foram gerados.

## Componentes de Threads anexadas a uma Activity/Fragment

__AsyncTask__ é o componente de threads Android mais utilizado. É simples de usar e pode ser bom para cenários básicos. Contudo,fica aquém se precisar que a tarefa adiada seja executada além do tempo de vida da activity/fragment. Vale a pena notar que mesmo algo tão simples quanto a rotação da tela pode causar a destruição da atividade.

__Loaders__ são a solução para o problema mencionado anteriormente. Loaders podem automaticamente parar quando a activity é destruída, e pode auto reiniciar após a activity ser recriada. Há dois tipos de loaders principais: __AsyncTaskLoader__ e __CursorLoader__.  

__AsyncTaskLoader__ é similar a __AsyncTask__, porém mais complicado.

## Componentes de Threads que não estão anexadas a uma Activity/Fragment

__Service__ é um componente útil para performar longas (ou potencialmente longas) operações sem qualquer UI. __Service__ é executado na MainThread do processo de hospedagem; o serviço não cria sua própria thread e não executa em um processo separado a menos que especifiquemos. Com __Service__, é nossa responsabilidade de pará-lo quando o trabalho é concluído chamando ou método o _stopSelf()_ ou o _stopService()_

__IntentService__ assim como __Service__, __IntentService__ é executado em uma thread separada, e para automaticamente após concluir seu trabalho. O __IntentService__ geralmente é usado para tarefas curtas que não precisam ser anexadas a nenhuma UI.
