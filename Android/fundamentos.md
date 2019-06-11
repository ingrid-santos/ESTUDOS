# Fundamentos do Android

O Android é um sistema operacional construído basicamente para dispositivos mobile. È baseado no kernel do Linux e em outros softwares _Open Source_, e é desenvolvido pela __Google__. No Android a programação é feita basicamente em duas linguaguens __JAVA__ ou __C++__ e __XML (Extension Markup Language)__. Atualmente, o __KOTLIN__ também tem sido bastante utilizado.

## Os 4 Pilares do Android

Uma aplicação Android em quatro tipos de classes principais, onde cada um desses tipos representa uma forma de interação que sua aplicação irá ter com o usuário, plataforma ou com outras aplicações. Elas podem coexistir em uma única aplicação ou também podem existir separadamente. Os quatro tipos de classes principais são:

- __Activities:__ as classes responsáveis pela interação visual da aplicação com o usuário são as que extendem de _Activity_. Estas classes apresentarão menus, listas, formulários ou qualquer outra interação que você deseja fazer através das telas  da aplicação. Uma classe Activity é composta por um ou vários objetos do tipo _View_, que pode ser texto, imagem, botão ou qualquer outro elemento de interação com o usuário. Uma aplicação pode ter uma ou várias activities, dependendo do design de navegação (nesse caso uma delas deverá ser marcada como a principal quando uma aplicação for iniciada). E a aplicação pode não ter nenhuma Activity (isso pode acontecer se for um serviço).

        public class MainActivity extends Activity {
        }

- __Services:__ uma classe _Service_ não tem interação visual com o usuário, mas tem a característica de executar tarefas por tempo indefinido em background. Esses serviços podem se comunicar com outros serviços, inclusive do SO, e também fazer chamada de aplicações, push de notificações e outros tipos de operação que uma aplicação comum faria.

        public class MyService extends Service {
        }

- __Content Providers:__ fornece dados de uma aplicação para outros sob solicitação. Onde tais pedidos são tratados pelos métodos da classe _ContentResolver_. Os dados podem ser armazenados no sistemas de arquivos, no banco de dados ou em qualquer outro lugar. Um _content provider_ é implementado como uma subclasse da classe _ContentProvider_ e deve implementar um conjunto padrão de APIs que permite que outros aplicativos executem transações.

        public class MyContentProvider extends ContentProvider {
            public void onCreate() {}
        }

- __Broadcast Receivers:__ são componentes que não "fazem nada" a não ser receber e reagir aos _broadcasts_ que são enviados, inclusive pelo sistema, por exemplo, mudança de fuso-horário, bateria fraca, etc. Além disso, uma aplicação também pode emitir algo através de broadcast e esperar que um destes recebedores faça o devido tratamento. Um _Broadcast Receivers_ é implementado como uma subclasse da classe _BroadcastReceiver_ e cada mensagem é transmitida como um objeto _intent_.

## Estrutura da Aplicação Android

![estrutura de um projeto](/home/ingrid/Documentos/Estudos/Android/estrutura.png)

- __Android Manifest__ é um arquivo XML que é a raiz do conjunto de fontes do projeto. Responsável por descrever as informações essenciais sobre o aplicativo e as ferramentas de criação do Android, o sistema operacional Android, e o Google Play. Nele estão as permissões que um aplicativo pode precisar para executar determinada tarefa. Nele também contém os recursos de hardware e software do aplicativo, o que determina a compatibilidade de um aplicativo na Play Store. Inclui também as atividades especiais como serviços, receptor de broadcast, provedores de conteúdo, nome do pacote, etc.
- __Java__ é a pasta onde consistem os arquivos java necessários para executar a tarefa em segundo plano do aplicativo. Ou seja, é onde estão implementadas as funcionalidades dos botões, cálculo, armazenamento, variáveis, tosts (pequenas mensagens popup), etc.
- __Res (Resource)__ é a pasta onde consistem os recursos que são utilizados na aplicação. Ou seja, onde se encontram subpastas como _drawable_ que consiste nas imagens, _layout_ que consiste nos arquivos XML que definem o layout da interface do usuário, _values_ consiste nos valores usados para armazenar os valores(string, colors, etc), etc.
- __Gradle__ é um kit de ferramentas avançadas, usado para gerenciar o processo de criação, que permite definir as configurações de construção customizadas flexíveis. Cada configuração de compilação pode definir seu próprio conjunto de códigos e recursos, enquanto reutiliza as partes comuns a todas as versões do seu aplicativo. O plugin do Android para Gradle funciona com o kit de ferramentas de construção para fornecer processos e configurações configuráveis que são específicos para criar e testar aplicações Android. O Gradle e o plugin do Android são executados independentemente do Android Studio. A flexibilidade do sistema de criação personalizadas sem modificar os principais arquivos de origem do aplicativo.

## Arquitetura do Android

![arquitetura do android](/home/ingrid/Documentos/Estudos/Android/plataforma-android.png)

- __Aplicativos:__ são os aplicativos e jogos desenvolvidos utilizando a linguagem _Java_.
- __Frameworks, Serviços e Bibliotecas:__ essa camada fornece muitos serviços de nível superior para aplicativos na forma de classes Java. A estrutura do Android inclui os seguintes serviços principais:
  - __Activity Manager:__ controla todos os aspectos do ciclo de vida e da pilha de _Activities_ do aplicativo.
  - __Provedores de Conteúdo:__ permite que aplicativos publiquem e compartilhem dados com outros aplicativos.
  - __Gerenciador de Recursos:__ fornece acesso a recursos incorporados não codificados, como sequência de caracteres, configurações de cores e layouts de interface do usuário.
  - __Gerenciador de Notificações:__ permite que os aplicativos exibam alertas e notificações para o usuário.
  - __Sistema de Visualização:__ um conjunto de extensível de visualizações usado para criar interfaces com o usuário do aplicativo.
- __Bibliotecas e Serviços Nativos:__  no topo do kernel do Linux, há um conjunto de bibliotecas incluindo o WebKit, mecanismo de navegação da Web de código aberto, bibliotecas nativas, bancos de dados SQLite que é um repositório útil para armazenamento e compartilhamento de dados de aplicativos, bibliotecas para reprodução e gravação de aúdio e vídeo, bibliotecas SSL responsáveis pela segurança da Internet, etc.
- __Linux:__ na parte inferior tá o Linux. Isso fornece um nível de abstração entre o hardware do dispositivo e contém todos os drivers de hardwares essenciais, como câmera, teclado, display, etc. Além disso, o kernel lida com todas as coisas que o Linux realmente é bom, como rede e uma vasta gama de drivers e dispositivos.
