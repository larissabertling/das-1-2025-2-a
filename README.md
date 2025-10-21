# das-1-2025-2-a

**aula 1 - 04/08** 

- Principios de projeto de código
- Padronização de código
- Ocultamento de informação
- Coesão
- Acoplamento

ABSTRAÇÃO = Representar alguma coisa do mundo real para resolver o problema. Representação simplificada, que permite interagir e tirar proveito da entidade abstraída, sem dominar todos os detalhes de sua implementação.

COESÃO = Código coeso, limpo, fácil de compreensão. Toda classe deve ter uma única responsabilidade no sistema. Um único motivo para modificar uma classe. Facilita a implementação de uma classe. ENTENDIMENTO e MANUTENÇÃO FÁCIL. 

HERANÇA = seta normal
Implementação = flecha tracejada e aberta

HERANÇA > IMPLEMENTAÇÃO > ASSOCIAÇÃO


Autoacoplamento - toda vez que mexo num pedaço do código, altera outro

_______________________________________________________________________________________________________________________________________
**aula 2 - 05/08**

Robert Martin - Referência na área de software. Um dos maiores nomes da computação.
  Livros dele: código limpo, arquitetura limpa

SOLID = usar a orientação a objetos do jeito certo. Linguagem Small Talk
  Single Responsibility Principle
  Open/Closed Principle
  Liskov Substitution Principle
  Interface Segregation Principle
  Dependency Inversion Principle

  Single Responsability Principle
    Tem relação com a coesão.
    Toda classe deve ter uma responsabilidade única.
    Separar as regras de negócio.

  MVC = Model View Controll = dados  | html  | controla a tela

  
  Open/Closed Principle
  Liskov Substitution Principle
  
  Interface Segregation Principle
    Deveria ter sempre uma interface no meio para a ver uma conversa entre duas classes.


    package br.univille;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;


public class Janelinha extends JFrame{

    private JButton botaozinho;
    private Controlador controlador;

    public Janelinha() {
        setTitle("Eu nao acredito");
        setSize(500,500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        botaozinho = new JButton("ME CLICA");
        controlador = new Controlador();
        botaozinho.addActionListener(controlador);

        /*botaozinho.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                JOptionPane.showMessageDialog(null,"oi");
            }
        });*/
        
        add(botaozinho);

        setVisible(true);
    }
    public static void main(String[] args) {
        new Janelinha();
    }
}



package br.univille;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JOptionPane;

public class Controlador implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e) {
        meClica();
    }

    private void meClica(){
        JOptionPane.showMessageDialog(null, "NAO ACREDITO");
    }
    
    
}


_____________________________________________________________________________________________
**aula 3 - 11/08**
SOLID
  Princípio da inversão de dependências
    Esse princípio recomenda que uma classe cliente deve estabelecer dependências prioritariamente com abstrações e não com implementações concretas, pois abstrações (isto é,            interfaces) são mais estáveis do que implementações concretas (isto é, classes). A ideia é então trocar (ou inverter) as dependências: em vez de depender de classes concretas, clientes devem depender de interfaces. Portanto, um nome mais intuitivo para o princípio seria Prefira Interfaces a Classes.

  Prefira composição a herança

      Herança expõe para subclasses detalhes de implementação das classes pai. Logo, frequentemente diz-se que herança viola o encapsulamento das classes pai. 
      A implementação das subclasses se torna tão acoplada à implementação da classe pai que qualquer mudança nessas últimas pode forçar modificações nas subclasses.
      O princípio, porém, não proíbe o uso de herança. Mas ele recomenda: se existirem duas soluções de projeto, uma baseada em herança e outra em composição, a solução por meio de composição, normalmente, é a melhor. Só para deixar claro, existe uma relação de composição entre duas classes A e B quando a classe A possui um atributo do tipo B.
  
  Princípio de Demeter (menor conhecimento)

        também chamado de Princípio do Menor Conhecimento (Principle of Least Knowledge) — defende que a implementação de um método deve invocar apenas os seguintes outros métodos:

            de sua própria classe (caso 1)
            de objetos passados como parâmetros (caso 2)
            de objetos criados pelo próprio método (caso 3)
            de atributos da classe do método (caso 4)]

        Costuma-se dizer que o Princípio de Demeter recomenda que os métodos de uma classe devem falar apenas com seus amigos, isto é, com métodos da própria classe ou então com métodos         de objetos que eles recebem como parâmetro ou que eles criam. Por outro lado, não é recomendável falar com os amigos dos amigos.
    
  Princípio Aberto/Fechado

      uma classe deve estar fechada para modificações e aberta para extensões.
      quando o projeto da classe prevê a possibilidade de extensões e customizações. Para isso, o projetista pode se valer de recursos como herança, funções de mais alta ordem (ou   funções lambda) e padrões de projeto, como Abstract Factory, Template Method e Strategy.

      o Princípio Aberto/Fechado tem como objetivo a construção de classes flexíveis e extensíveis, capazes de se adaptarem a diversos cenários de uso, sem modificações no seu código fonte.

      
_______________________________________________________________________________________________
**aula 4 - 12/08**

    Princípio de Substituição de Liskov 

        explicita regras para redefinição de métodos de classes base em classes filhas. 
        O Princípio de Substituição de Liskov determina as condições — semânticas e não sintáticas — que as subclasses devem atender para que um programa como o anterior funcione.


exemplo:
Para explicar o Princípio de Substituição de Liskov vamos nos basear no seguinte exemplo:

void f(A a) {
  ...
  a.g();
  ...
}
O método f pode ser chamado passando-se como parâmetros objetos de subclasses B1, B2, …, Bn da classe base A, como mostrado a seguir:
f(new B1());  // f pode receber objetos da subclasse B1 
...
f(new B2());  // e de qualquer subclasse de A, como B2
...
f(new B3());  // e B3

Suponha que as subclasses B1, B2, …., Bn redefinam o método g() de A, que é um método chamado no corpo de f. O Princípio de Substituição de Liskov prescreve que essas redefinições não podem violar o contrato da implementação original de g em A.
    
LEITURA CAPÍTULO 6
6 Padrões de Projeto

  
  Dependency 
 _____________________________________________________________________________________
  **Aula - 25/08**

  Padrões de Projeto - Implementação Observer


  Observer é um padrão de design comportamental que permite definir um mecanismo de assinatura para notificar vários objetos sobre quaisquer eventos que aconteçam com o objeto que eles estão observando.
  O objeto que possui algum estado interessante é frequentemente chamado de sujeito , mas como ele também notificará outros objetos sobre as alterações em seu estado, o chamaremos de publicador . Todos os outros objetos que desejam rastrear alterações no estado do publicador são chamados de assinantes .
  O padrão Observer sugere que você adicione um mecanismo de assinatura à classe publicadora para que objetos individuais possam assinar ou cancelar a assinatura de um fluxo de eventos provenientes dessa publicadora.  Na realidade, esse mecanismo consiste em 1) um campo de array para armazenar uma lista de referências a objetos assinantes e 2) vários métodos públicos que permitem adicionar e remover assinantes dessa lista.
sempre que um evento importante acontece com o publicador, ele acessa seus assinantes e chama o método de notificação específico em seus objetos.
O publicador notifica os assinantes chamando o método de notificação específico em seus objetos.

  _____________________________________________________________________________________
  **Aula - 26/08**

  Livro Fundamentos da arquitetura de software: uma abordagem de engenharia

  3 coisas que montam a estrututa da arquitetura / design do sistema.

  CARACTERÍSTICAS DA ARQUITETURA:
    Disponibilidade, Confiabilidade, Testabilidade, Escalabilidade, Segurança, Agilidade, Tolerância a falhas, Elasticidade, Recuperabilidade, Desempenho,        Implementabilidade, Capacidade de aprendizagem.

Disponibilidade: Sistema estar acessível e funcionando quando necessário.
Confiabilidade: Capacidade de funcionar sem falhas por um período.
Testabilidade: Facilidade de testar o sistema para encontrar erros.
Escalabilidade: Sistema crescer sem perder desempenho.
Segurança: Proteção contra acessos e ataques não autorizados.
Agilidade: Rapidez para adaptar e implementar mudanças.
Tolerância a falhas: Capacidade de continuar funcionando mesmo quando algo falha.
Elasticidade: Ajuste automático da capacidade conforme a demanda.
Recuperabilidade: Rapidez em se recuperar após uma falha.
Desempenho: Resposta rápida e eficiente do sistema.
Implementabilidade: Facilidade de construir e manter o sistema.
Capacidade de aprendizagem: Sistema que pode evoluir ou se adaptar com base em dados ou feedback.


  DECISÕES DA ARQUITETURA:
    Regras que precisam ser mantidas no nosso sistema para que ele tenha o minimo de domínio, sustento.
    São regras e escolhas fundamentais que definem como o sistema vai funcionar e se manter estável. Garantem a coerência, segurança e eficiência do sistema ao longo do tempo.

  PRINCÍPIOS DO DESIGN:

  Boas práticas. Coisas que sempre que possível deveríamos usar.
  Boas práticas que orientam a criação de sistemas, como modularidade, simplicidade, reutilização, separação de responsabilidades, e clareza. Aplicá-los ajuda a ter sistemas mais fáceis de entender, manter e evoluir.

________________________________________________________________________________________________________
**Aula 01/09**

CARACTERÍSTICAS DA ARQUITETURA = Requisitos NÃO funcionais

É impossível que um sistema atenda 100% todos os itens de características.

Decisão arquitetural é quando escolho qual arquitetura utilizar.

Funções do arquiteto:

    Tomar decisões de arquitetura – 
          Responsável por definir a estrutura e os padrões principais do sistema, garantindo que suportem os        requisitos técnicos e           de negócio.
          Orientação – Guiar a equipe de desenvolvimento nas direções corretas, explicando os motivos das decisões tomadas.
          Não especificar as escolhas da tecnologia – Deve indicar direções, mas não impor ferramentas específicas, deixando espaço para            a equipe propor alternativas.

    Analisar continuamente a arquitetura – 
          Avaliar de forma recorrente se a arquitetura ainda atende às necessidades do projeto, ajustando quando necessário.

    Reconstruir partes do código – 
          Quando a arquitetura não atende mais aos requisitos, pode ser preciso refatorar ou redesenhar partes do sistema.

    Manter-se atualizado com as últimas tendências – 
          Estudar novas práticas, padrões, frameworks e tecnologias para trazer inovação e melhorias ao projeto.

    Assegurar a conformidade com as decisões – 
          Garantir que o time siga as diretrizes arquiteturais, evitando desvios que possam gerar problemas futuros.

    Exposição e experiência diversificadas – 
          Ter vivência com diferentes linguagens, frameworks, ambientes e domínios, para propor soluções mais eficazes.

    Conhecimento sobre o domínio de negócio – 
          Entender o contexto, processos e necessidades da área de negócio para alinhar a arquitetura aos objetivos da organização.

    Habilidades interpessoais – 
          Saber comunicar, negociar e mediar conflitos com diferentes perfis de stakeholders, incluindo desenvolvedores, gerentes e       clientes.

    Entender e lidar bem com questões políticas – 
          Compreender as dinâmicas organizacionais, influências e restrições internas para tomar decisões mais realistas e viáveis.


DEVOPS = maneira de entregar valor pro cliente mais rápido.
Entregar mais rápido funcionalidade, valor.

Devops é meio que se der um problema, todos do devops precisam estar "aptos" a fazer tudo. Todo mundo faz tudo

PLANEJAMENTO
CRIAÇÃO
OPERAÇÃO
FEEDBACK
COMENTÁRIOS CONTÍNUOS
IMPLANTAR
INTEGRAÇÃO CONTÍNUA


  Tomar decisões de arquitetura
      Orientação
      Não especificar as escolhas da tecnologia.
      
  Analisar continuamente a arquitetura
      E as vezes precisar reconstruir uma parte do código.
      
  Manter-se atualizado com as últimas tendências

  
  Assegurar a confirmidade com as decisões
  Exposição e experiência diversificadas.
  Conhecimento sobre o domínio de negócio
  Ter habilidades interpessoais
  Entender e lidar bem com questões políticas

DevOps? =
A contratação de "Dev" e "Ops" refere-se à substituição de operações e desenvolvimento em silos.
____________________________________________________________________________________________
**Aula 02/09**
Resumo Capítulo 2: Pensamnento Arquitetônico
Resuma a diferençca entre: Arquitetura e Design
Como é a formação do conhecimento de um arquiteto modelo T?

Pensamento arquitetônico é  ver as coisas com os olhos da arquitetura. Pensar como arquiteto envolve quatro aspectos principais:
  Entender a diferença entre arquitetura e design, saber como colaborar com as equipes de desenvolvimento para a arquitetura funcionar.     Ter uma grande variedade de conhecimento técnico e ainda manter certo nível de profundidade técnica, permitindo que o arquiteto veja soluções e possibilidades que os outros não veem. 
  Terceiro, é entender, analisar e reconciliar os trade-offs entre várias soluções e tecnologias. 
  Entender a importância das motivações comerciais e como elas se traduzem em preocupações arquitetônicas.

Arquitetura x Design:

Um arquiteto é responsável por analisar os requisitos comerciais para extrair e definir as características da arquitetura, selecionar quais padrões e estilos da arquitetura se encaixariam no domínio do problema e criar componentes . Então os artefatos criados a partir dessas atividades são passados para a equipe de desenvolvimento, responsável por criar diagramas de classes para cada componente, criar telas de interface do usuário e desenvolver e testar o código-fonte.

ARQUITETO > CARACTERÍSTICAS DAS ARQUITETURAS                                > DESIGN DA CLASSE
          > ESTILO                                    > DESENVOLVEDOR       > INTERFACE DO USUÁRIO
          > ESTRUTURA DO COMPONENTE                                         > CÓDIGO FONTE


**Amplitude Técnica**
O escopo dos detalhes técnicos difere entre desenvolvedores e arquitetos. Diferentemente de um desenvolvedor, que deve ter bastante profundidade técnica para realizar seu trabalho, um arquiteto de software deve ter uma grande amplitude técnica para pensar como arquiteto e ver as coisas de um ponto de vista da arquitetura. 
Diferimos o conhecimento em três seções: o que você sabe, o que você sabe que não sabe e o que você não sabe que não sabe.


A formação do arquiteto modelo T é estruturada em dois eixos:

Eixo horizontal (o traço do T): representa a amplitude de conhecimentos. O arquiteto possui uma visão generalista, entendendo de várias áreas relacionadas à arquitetura (como gestão, metodologias ágeis, negócios, segurança, infraestrutura, usabilidade, etc.). Isso permite comunicação e colaboração com diferentes equipes.

Eixo vertical (a base do T): representa a profundidade em uma área específica. O arquiteto tem domínio técnico mais aprofundado em um ou poucos campos centrais (por exemplo, arquitetura de software, banco de dados, nuvem, integração de sistemas).


Em geral o arquiteto modelo T é formado para ter visão ampla e generalista, mas com especialização profunda em um campo específico, unindo capacidade de dialogar com diferentes áreas e, ao mesmo tempo, expertise sólida em sua especialidade. Como arquiteto, amplitude é mais importante do que profundidade

Os arquitetos devem focar a amplitude técnica para que tenham uma aljava maior a partir da qual tiram suas flechas. Os desenvolvedores que fazem a transição para a função de arquiteto talvez precisem mudar o modo como veem a aquisição de conhecimento. Equilibrar seu portfólio de conhecimento em relação à profundidade versus amplitude é algo que todo desenvolvedor deve considerar durante sua carreira.
Pensar como arquiteto é ver os trade-offs em toda solução, técnica ou outra, e analisá-las para determinar qual é a melhor solução.

_________________________________________________________________________________________
**Aula 08/09**
Resumo: Analisando Trade - Offs

Analisando os Trade-offs
Pensar como arquiteto é ver os trade-offs em toda solução, técnica ou outra, e analisá-las para determinar qual é a melhor solução.
Tudo na arquitetura é um trade-off. Não existe resposta certa nem errada na arquitetura, apenas trade-offs..
O pensamento arquitetural requer que o arquiteto analise os trade-offs a cada opção e selecione a melhor, dada a situação específica.

A clara vantagem  para o problema  é a extensabilidade arquitetural. O serviço Quem dá o lance requer apenas uma conexão com um tópico, diferentemente da solução de fila na Figura 2-9, em que Quem dá o lance precisa conectar três filas diferentes.

 ponto aqui é que usar filas requer uma mudança significativa no sistema ao adicionar a nova funcionalidade de lances; já na abordagem de tópicos, nenhuma mudança é necessária na infraestrutura existente.
 Os programadores conhecem os benefícios de tudo e os trade-offs de nada. Os arquitetos precisam entender ambos.

 Pensar de modo arquitetural é ver os benefícios de certa solução, mas também analisar os lados negativos, ou os trade-offs, associados a uma solução. Continuando com o exemplo do sistema de leilão, um arquiteto de software analisaria os lados negativos da solução de tópico. 

 Note que esse trade-off é específico da tecnologia em que o Protocolo Avançado de Enfileiramento de Mensagens (AMQP) pode suportar o equilíbrio da carga programática e o monitoramento por causa da separação entre uma troca (o que aquele que dá o lance envia) e uma fila (o que o consumidor ouve).

 A questão aqui é que tudo na arquitetura de software tem um trade-off: escolher entre uma vantagem e uma desvantagem. Pensar como arquiteto é analisar esses trade-offs, então perguntar “qual é mais importante: extensão ou segurança?” A decisão entre as diferentes soluções sempre dependerá das motivações comerciais, do ambiente e de muitos outros fatores.
_______________________________________________________________________________________
**Aula 09/09**
Código


_________________________________________________________________________________________
**Aula 15/09**

Azure
Publisher -> Broker <- Subscriber
^
|
broker
azure service bus

https://portal.azure.com/#@univillebr.onmicrosoft.com/resource/subscriptions/4a70cb43-f047-4c9b-adec-e0e58c9357d6/resourceGroups/rg-das-1-2025a-dev-eastus2-01/providers/Microsoft.ServiceBus/namespaces/sbdas12025a/overview

CÓDIGO

__________________________________________________________________________________________
**Aula 16/09**

CÓDIGO 

________________________________________________________________________________________
22/09 - prova 1

_____________________________________________________________________________________________
23/09 


















_________________________________________________   _ ________________________________________  
**2 BIMESTRE**
**29/09**

https://learn.microsoft.com/pt-br/azure/architecture/patterns/circuit-breaker?wt.mc_id=AZ-MVP-5003638

CIRCUIT BREAK
Função = Proteger a comunicação entre sistemas.

O padrão Circuit Breaker ajuda a lidar com falhas que podem levar períodos variados para serem recuperadas quando um aplicativo se conecta a um serviço ou recurso remoto. 
O padrão Circuit Breaker ajuda a evitar que um aplicativo tente executar repetidamente uma operação com probabilidade de falha. 
Esse padrão permite que o aplicativo continue em execução sem esperar que a falha seja corrigida ou desperdiçar ciclos de CPU para determinar que a falha é persistente. O padrão Circuit Breaker também permite que um aplicativo detecte quando a falha é resolvida. Se a falha for resolvida, o aplicativo pode tentar invocar a operação novamente.

DIJUNTOR:
ESTADO FECHADO = tudo dando certo
ESTADO DE ABERTO - aconteceu uma falha, erro, algum problema
ESTADO MEIO ABERTO = half open = de tempos em tempos ele vai pro meio aberto, pra ver se fecha ou se precisa voltar pro aberto

**Fechado**: A solicitação do aplicativo é roteada para a operação. O proxy mantém uma contagem do número de falhas recentes. Se a chamada para a operação não for bem-sucedida, o proxy incrementa essa contagem. 
Se o número de falhas recentes exceder um limite especificado dentro de um determinado período, o proxy é colocado no estado **Aberto** e inicia um temporizador de tempo limite. Quando o temporizador expira, o proxy é colocado no estado **Meio Aberto** .

**Aberto**: A solicitação do aplicativo falha imediatamente e uma exceção é retornada ao aplicativo.

**Meio-Aberto**: Um número limitado de solicitações da aplicação pode passar e invocar a operação. Se essas solicitações forem bem-sucedidas, o disjuntor assume que a falha que causou a falha foi corrigida e o disjuntor comuta para o estado Fechado . O contador de falhas é zerado. Se alguma solicitação falhar, o disjuntor assume que a falha ainda está presente e, portanto, retorna ao estado Aberto . Ele reinicia o temporizador de tempo limite para que o sistema possa se recuperar da falha.

O contador de falhas para o estado Fechado é baseado em tempo. Ele é reiniciado automaticamente em intervalos periódicos. Este projeto ajuda a evitar que o disjuntor entre no estado Aberto caso apresente falhas ocasionais. O limite de falha aciona o estado Aberto somente quando um número especificado de falhas ocorre durante um intervalo especificado.

O contador de sucessos para o estado Meio Aberto registra o número de tentativas bem-sucedidas de invocação da operação. O disjuntor retorna ao estado Fechado após um número especificado de invocações consecutivas bem-sucedidas. Se alguma invocação falhar, o disjuntor entra no estado Aberto imediatamente e o contador de sucessos é zerado na próxima vez que entrar no estado Meio Aberto .


Um disjuntor bloqueia temporariamente o acesso a um serviço com defeito após detectar falhas. Essa ação evita tentativas repetidas sem sucesso, permitindo que o sistema se recupere com eficácia. Esse padrão pode melhorar a estabilidade e a resiliência de um aplicativo.

Para ajudar a gerenciar essas falhas, você deve projetar um aplicativo em nuvem para usar uma estratégia, como o padrão Retry .


RETRY x CIRCUIT BREAK

O padrão Circuit Breaker tem uma finalidade diferente do padrão Retry. O padrão Retry permite que um aplicativo tente novamente uma operação com a expectativa de que ela seja bem-sucedida. O padrão Circuit Breaker impede que um aplicativo execute uma operação com probabilidade de falha. Um aplicativo pode combinar esses dois padrões usando o padrão Retry para invocar uma operação por meio de um disjuntor. No entanto, a lógica de repetição deve ser sensível a quaisquer exceções retornadas pelo disjuntor e interromper as tentativas de repetição se o disjuntor indicar que a falha não é transitória.


PROBLEMAS:
Tratamento de exceções: O aplicativo deve lidar com falhas quando o disjuntor bloquear uma operação — reduzindo funções, tentando alternativas ou avisando o usuário.

Tipos de exceções: O disjuntor pode ajustar sua resposta conforme o tipo de falha (ex.: tempo limite ou serviço indisponível).

Monitoramento: É essencial registrar falhas e sucessos para avaliar a saúde do sistema.

Recuperabilidade: O tempo de reabertura do disjuntor deve seguir o padrão de recuperação da operação, evitando erros ou instabilidade.

Teste de falhas: O disjuntor pode testar periodicamente o serviço (ping) antes de voltar ao estado normal.

Substituição manual: Administradores devem poder reabrir ou fechar o disjuntor manualmente em casos especiais.

Concorrência: O disjuntor deve suportar múltiplas instâncias sem causar bloqueios ou lentidão.

Diferenciação de recursos: Evite usar um único disjuntor para vários provedores — falhas isoladas podem afetar recursos saudáveis.

Interrupção acelerada: Se a resposta indicar falha prolongada, o disjuntor pode permanecer aberto por tempo mínimo antes de tentar novamente.

Implantações multirregionais: Use disjuntores com reconhecimento de região e balanceamento global para garantir failover e desempenho.

Malha de serviço: Disjuntores podem ser implementados no código da aplicação ou como recurso da malha de serviço.

Repetição de solicitações: O disjuntor pode registrar solicitações falhas e reenviá-las quando o serviço voltar.

Tempos limite longos: Tempos limite altos em serviços externos podem bloquear threads e reduzir a proteção do disjuntor.

Adaptabilidade: Disjuntores devem se ajustar a diferentes ambientes (serverless, contêineres etc.) para manter a resiliência.


Quando usar:

Para evitar falhas em cascata e limitar chamadas a serviços remotos com falha.
Para redirecionar tráfego com base em falhas em tempo real e aumentar a resiliência multirregional.
Para proteger contra serviços lentos e manter o desempenho.
Para lidar com problemas intermitentes de conectividade em sistemas distribuídos.

Quando não usar:

Em recursos locais na memória, onde o disjuntor gera sobrecarga desnecessária.
Como substituto do tratamento de exceções da lógica de negócio.
Quando algoritmos de repetição já resolvem o problema.
Se o tempo de reinício do disjuntor causar atrasos inaceitáveis.
Em arquiteturas baseadas em mensagens que já têm filas de falha e isolamento nativo.
Quando a recuperação é feita pela própria infraestrutura (como balanceadores ou malhas de serviço).

++ IMPLEMENTAÇÃO
____________________________________________________________________________________________________________
AULA 30/09

IMPLEMENTAÇÃO


_________________________________________________________________________________________________________
AULA 06/10

Solução de software: auditoria > desempenho > segurança > requisitos > dados > legalidade > escalabilidade

Uma característica da arquitetura atende a três critérios:

- Especifica uma consideração de design fora do domínio
- Influencia algum aspecto estrutural de design
- É essencial ou importante para o sucesso da aplicação

Características da arquitetura são considerações de design que vão além dos requisitos funcionais — definem como o sistema deve funcionar e por que certas escolhas são feitas (ex.: desempenho, segurança, confiabilidade).

Elas influenciam o design estrutural da aplicação. Por exemplo:
Se o pagamento é feito por um serviço terceirizado → medidas padrão de segurança bastam.
Se o sistema processa pagamentos internamente → exige um módulo específico e maior isolamento de segurança.
Nem todas as características merecem foco: cada uma adiciona complexidade, então o arquiteto deve priorizar as essenciais para o sucesso do sistema.
Há características explícitas (descritas nos requisitos) e implícitas (como disponibilidade e segurança, que são esperadas mesmo sem estarem documentadas).
Esses elementos se interligam e exigem equilíbrio (trade-offs) no design da arquitetura.

CARACTERÍSTICAS OPERACIONAIS DA ARQUITETURA:
    As características operacionais da arquitetura têm uma sopreposição significativa com as preocupações de operações e DevOps, formando     a interseção dessas questões em muitos projetos de software.

- Disponibilidade: Por quanto tempo o sistema precisa ficar disponível (se for 24/7, é preciso ter etapas para permitir que o sistema fique ativo rápido no caso de qualquer falha).
- Continuidade:	Capacidade de recuperação de desastres.
- Desempenho:	Inclui teste de estresse, análise de pico, análise da frequência das funções usadas, capacidade requerida e tempos de resposta. Por vezes, a aceitação do desempenho requer um exercício próprio, levando meses para concluir.
- Recuperabilidade:	Requisitos de continuidade do negócio (por exemplo, no caso de desastres, com que rapidez o sistema precisa ficar online de novo?). Isso afetará a estratégia de backup e os requisitos para o hardware duplicado.
- Confiabilidade/ segurança:	Avalia se o sistema precisa ser à prova de falhas ou se tem uma missão crítica no modo como afeta a vida das pessoas. Se ele falha, custará muito dinheiro para a empresa?
- Robustez:	A capacidade de lidar com condições de erro e limites durante a execução, caso a conexão de internet caia ou se há falta de energia ou falha no hardware.
- Escalabilidade:	A capacidade de o sistema rodar e operar quando o número de usuários ou requisições aumenta.

CARACTERÍSTICAS ESTRUTURAIS DA ARQUITETURA:
    Os arquitetos devem se preocupar com a estrutura do código. Em muitos casos, o arquiteto tem uma responsabilidade única ou                 compartilhada pelas questões de qualidade do código, como boa modularidade, acoplamento controlado entre os componentes, código           legível e muitas outras avaliações internas da qualidade. O Quadro 4-2 lista algumas características estruturais da arquitetura.


- Configuração:	A capacidade dos usuários finais de mudar com facilidade os aspectos de configuração do software (com interfaces úteis).
- Extensão:	Como é importante ligar as novas partes da funcionalidade.
- Instabilidade: Facilidade de instalação do sistema em todas as plataformas necessárias.
- Aproveitamento/ reutilização:	Capacidade de aproveitar os componentes comuns em vários produtos.
- Localização: 	Suporte para vários idiomas nas telas de entrada/consulta nos campos de dados; nos relatórios, requisitos de caracteres multibytes e unidades de medidas ou moedas.
- Manutenção:	Quão facilmente aplica as alterações e melhora o sistema?
- Portabilidade: 	O sistema precisa rodar em mais de uma plataforma? (Por exemplo, o front-end precisa rodar no Oracle e no banco de dados SAP?)
- Suporte: 	De qual nível de suporte técnico a aplicação precisa? Qual nível de registro e outras facilidades são requeridos para depurar os erros no sistema?
- Atualização: 	A capacidade de atualizar com facilidade/rapidez uma versão prévia dessa aplicação/solução para uma versão mais nova nos servidores e nos clientes.

CARACTERÍSTICAS TRANSVERSAIS DA ARQUITETURA:
  Embora muitas características da arquitetura se classifiquem em categorias fáceis de reconhecer, muitas estão fora ou desafiam a           categorização, formando importantes restrições de design e considerações. O Quadro 4-3 descreve algumas.

  - Acessibilidade:	Acesso a todos os usuários, inclusive com deficiências, como daltonismo e perda auditiva.
-  Armazenamento:	Os dados precisarão ser armazenados ou excluídos após um período de tempo? (Por exemplo, as contas do cliente serão excluídas após três meses ou marcadas como obsoletas e armazenadas em um banco de dados secundário para futuro acesso.)
- Autenticação: 	Requisitos de segurança para assegurar que os usuários são quem dizem ser.
- Autorização:	Requisitos de segurança para assegurar que os usuários possam acessar apenas certas funções na aplicação (por caso de uso, subsistema, página web, regra comercial, nível do campo etc.).
- Legalidade:	Com quais restrições legais o sistema opera (proteção de dados, Sarbanes Oxley, GDPR etc.)? Quais direitos de reserva a empresa requer? Alguma regulação no modo como a aplicação será criada ou implantada?
- Privacidade: 	A capacidade de ocultar as transações dos funcionários internos da empresa (transações criptografadas para que até os DBAs e os arquitetos de rede não possam vê-las).
- Segurança: 	Os dados precisam ser criptografados no banco de dados? Criptografados para a comunicação de rede entre os sistemas internos? Qual tipo de autenticação precisa existir para o acesso remoto do usuário?
 - Suporte:	De qual nível de suporte técnico a aplicação precisa? Qual nível de registro e outras facilidades são necessários para depurar os erros no sistema?


A ISO define um conjunto de características de qualidade de software, organizadas por categorias — embora a lista não seja completa.

Principais características:

- Eficiência do desempenho: mede o uso de recursos e tempo de resposta do sistema.
- Compatibilidade: capacidade de coexistir e trocar informações com outros sistemas.
- Usabilidade: facilidade de uso, aprendizado, proteção contra erros e acessibilidade.
- Confiabilidade: funcionamento contínuo e recuperação após falhas.
- Segurança: proteção de dados e controle de acesso (confidencialidade, integridade, autenticidade etc.).
- Manutenibilidade: facilidade para modificar, testar e reutilizar o software.
- Portabilidade: facilidade para transferir o software entre ambientes ou plataformas.

A adequação funcional, embora listada pela ISO, não é considerada uma característica da arquitetura, e sim um requisito funcional — pois descreve o que o sistema faz, não como ele é projetado.


__________________________________________________________________________________________________
AULA 07/10

**Padrão CQRS (Command Query Responsibility Segregation)**:
Separa as operações de leitura (consulta) e gravação (comando) em modelos de dados distintos, permitindo otimização independente para melhor desempenho, escalabilidade e segurança.

<img width="349" height="200" alt="image" src="https://github.com/user-attachments/assets/2bc8ded4-f8e1-4fbd-881b-7e1f185d9fd0" />

Desafio:
Em sistemas grandes, o mesmo modelo para leitura e gravação causa problemas de desempenho, bloqueio, segurança e complexidade, pois as operações têm requisitos diferentes.

Principais problemas:

- Diferença entre os dados usados para leitura e gravação.
- Contenção de bloqueio em acessos simultâneos.
- Quedas de desempenho por consultas complexas.
- Riscos de segurança ao misturar funções de leitura e escrita.

Solução (CQRS):
Separar comandos (gravação) e consultas (leitura) em modelos distintos.

    Comandos: representam ações de negócio (ex.: Reservar quarto), e não simples atualizações de dados.
    Consultas: apenas leem informações, retornando DTOs (objetos de transferência de dados) sem lógica de domínio.

Essa separação traz clareza, melhor desempenho e organização ao sistema.

Separar modelos de leitura e gravação:
Dividir os modelos de leitura e gravação simplifica o design, aumenta a clareza, desempenho e escalabilidade.

Desvantagem:
Ferramentas automáticas (como O/RM) não geram código CQRS automaticamente — é preciso criar lógica personalizada para manter os modelos sincronizados e consistentes.

Implementação:
Existem duas abordagens principais para separar esses modelos, cada uma com seus próprios desafios de sincronização e consistência.

**Benefícios do CQRS**

1. Escalabilidade independente
O CQRS permite que os modelos de leitura e de gravação sejam escalados de forma independente, reduzindo a contenção de bloqueios e melhorando o desempenho do sistema sob alta carga. Isso é especialmente útil em sistemas com muito mais leituras do que gravações.

2. Esquemas de dados otimizados
Com o CQRS, cada modelo pode ter seu próprio esquema de dados otimizado. O modelo de leitura pode ser estruturado para consultas rápidas e agregações, enquanto o modelo de gravação é projetado para consistência e integridade transacional.

3. Maior segurança
A separação entre leitura e gravação permite controlar melhor os acessos: apenas as operações e entidades de domínio autorizadas podem realizar alterações nos dados, aumentando a segurança e evitando modificações indevidas.

4. Separação de preocupações
O CQRS promove uma clara separação entre as responsabilidades de leitura e gravação, tornando o código mais limpo e fácil de manter. O lado da gravação trata da lógica de negócios e regras de domínio, enquanto o lado da leitura foca em consultas rápidas e eficientes.

5. Consultas mais simples e performáticas
Ao manter views ou projeções materializadas no banco de leitura, o sistema pode realizar consultas diretas e evitar junções complexas, resultando em respostas mais rápidas e menos sobrecarga no banco.

**Problemas e Considerações**

Ao implementar o padrão CQRS (Command Query Responsibility Segregation), é importante considerar alguns desafios e pontos de atenção:

1. Maior complexidade
Embora o conceito central do CQRS seja simples, sua implementação pode introduzir complexidade significativa na arquitetura da aplicação — especialmente quando combinado com o padrão Event Sourcing. Essa combinação exige maior esforço de design, testes e manutenção.

2. Desafios no envio de mensagens
O uso de mensageria não é obrigatório no CQRS, mas é comum em aplicações que precisam processar comandos e publicar eventos de atualização. Nesse contexto, o sistema deve lidar com desafios como falhas na entrega de mensagens, duplicatas e reenvios. Estratégias como filas de prioridade e mecanismos de confirmação podem ser necessárias para garantir a confiabilidade da comunicação entre os componentes.

3. Consistência eventual
Quando há bancos de dados separados para leitura e gravação, os dados de leitura podem não refletir as alterações mais recentes de forma imediata. Esse atraso (consistência eventual) pode causar divergência temporária entre os modelos.
Garantir que o repositório de leitura esteja constantemente sincronizado com o de gravação pode ser desafiador. Além disso, é necessário prever como o sistema deve reagir quando um usuário interagir com dados desatualizados.

**Quando Usar o CQRS**
O padrão CQRS é especialmente útil em cenários com complexidade de domínio, alto volume de leituras ou necessidade de evolução contínua. Ele é indicado quando:

- Ambientes colaborativos:
  Em sistemas com múltiplos usuários modificando os mesmos dados simultaneamente, o CQRS ajuda a reduzir conflitos. Comandos bem             definidos podem tratar conflitos de forma granular e previsível.

- Interfaces de usuário baseadas em tarefas:
  Aplicações que guiam o usuário por processos complexos ou possuem modelos de domínio ricos se beneficiam do CQRS, pois permitem modelar separadamente os fluxos de leitura e gravação.

- Modelos de gravação ricos em lógica de negócios:
  O lado de gravação pode conter toda a pilha de validação e regras de negócio, tratando agregados (conjuntos de objetos relacionados) como uma única unidade, garantindo a consistência do domínio.

- Modelos de leitura simplificados:
  O lado de leitura é otimizado para performance e simplicidade, retornando DTOs (Data Transfer Objects) diretamente para a camada de visualização, e mantendo consistência eventual com o modelo de gravação.

- Necessidade de ajuste de desempenho:
  Sistemas em que o número de leituras é muito superior ao de gravações podem escalar horizontalmente apenas o modelo de leitura, garantindo alta performance e custo controlado.

- Separação de responsabilidades de desenvolvimento:
  O CQRS favorece a divisão de equipes — uma focada na lógica de negócios (modelo de gravação) e outra na experiência do usuário (modelo de leitura) — promovendo desenvolvimento paralelo e independente.

- Sistemas em evolução:
  O padrão suporta modificações graduais e evolução constante das regras de negócio, permitindo a introdução de novas versões de modelos sem comprometer funcionalidades já existentes.

- Integração entre sistemas:
  O CQRS é adequado em arquiteturas distribuídas ou que usam Event Sourcing, pois permite isolar falhas e manter o sistema funcional mesmo quando um subsistema está indisponível.

**Quando não usar o CQRS**

- O padrão pode ser desnecessário ou contraproducente quando:
- O domínio de negócio é simples e não exige separação de responsabilidades complexas.
- Uma interface CRUD tradicional (criação, leitura, atualização e exclusão) atende bem às necessidades da aplicação.

**Combinação de CQRS e Event Sourcing**

Algumas implementações do CQRS utilizam o padrão Event Sourcing, que armazena o estado do sistema como uma sequência de eventos cronológica. O estado atual é reconstruído reproduzindo os eventos na ordem em que ocorreram.

**Como funciona a integração:**
  Modelo de gravação: o armazenamento de eventos atua como a única fonte de verdade.
  Modelo de leitura: gera visualizações materializadas a partir dos eventos, normalmente desnormalizadas, otimizadas para consultas e exibição.
  
  Benefícios da combinação:
- Os eventos que atualizam o modelo de gravação alimentam o modelo de leitura, permitindo instantâneos em tempo real do estado atual.

- Reduz conflitos de atualização em agregados e melhora desempenho e escalabilidade.

- Visualizações materializadas funcionam como cache durável, permitindo consultas rápidas e a reconstrução de dados históricos ou adaptação a novos modelos de leitura.

- Permite preservar todo o histórico de alterações, facilitando auditoria e análises.

**Considerações importantes:**

- Consistência eventual: atrasos na atualização das visualizações podem ocorrer, exigindo atenção a dados temporariamente desatualizados.

- Maior complexidade: implementar CQRS com Event Sourcing requer criar, processar e manipular eventos, além de gerar e atualizar visualizações de leitura.

- Desempenho: gerar visualizações materializadas pode consumir muitos recursos, especialmente em agregações complexas.

**Solução**: usar snapshots periódicos para armazenar estados atuais ou totais agregados, reduzindo a necessidade de processar todo o histórico de eventos.

________________________________________________________________________________________________
  AULA 13.10

**PADRÕES DE REPETIÇÃO**

Padrão de Repetição (Retry Pattern)

O padrão de repetição permite que um aplicativo lidar com falhas transitórias em serviços ou recursos de rede, repetindo operações com falha de forma transparente, aumentando a estabilidade e confiabilidade.

Contexto e Problema

Aplicações em ambientes de nuvem podem sofrer falhas transitórias, como:
- Perda momentânea de conectividade;
- Serviços temporariamente indisponíveis;
- Timeouts devido a alta carga.

Essas falhas geralmente se autocorrigem; repetir a operação após um atraso adequado aumenta a chance de sucesso.

Solução

- Projetar aplicativos para tratar falhas de forma elegante, minimizando impacto nas tarefas de negócio.
- Implementar mecanismos de repetição que lidem com diferentes tipos de falhas.

Estratégias de Repetição

- Cancelar : Quando a falha não é transitória ou repetida provavelmente falhará, interromper a operação e reportar a exceção.

- Tentar novamente imediatamente : Para falhas raras ou incomuns (ex.: pacote de rede corrompido), repetir a operação sem atraso.

- Tentar novamente após atraso : Para falhas comuns, como sobrecarga de serviço ou problemas de conectividade, aguardar um período antes de repetir.
O atraso pode ser incremental ou exponencial, distribuindo solicitações para reduzir sobrecarga no serviço.

- Política de repetição: cada serviço pode ter uma política personalizada.

- Registro de falhas: Registrar falhas iniciais como informativas;
Registrar apenas a falha final como erro real, evitando sobrecarga de alertas.

Considerações Adicionais

Se serviços falham frequentemente, pode ser necessário escalar ou particionar recursos, distribuindo a carga para reduzir indisponibilidade.
A combinação de retry + escalabilidade melhora desempenho e resiliência do sistema.


**Questões e Considerações do Padrão de Repetição**

Impacto no desempenho:
Ajuste a política de repetição conforme a criticidade da operação e a natureza da falha.
Operações não críticas podem falhar rapidamente; operações em lote podem ter várias tentativas com atrasos exponenciais.
Repetições agressivas podem sobrecarregar serviços já ocupados e reduzir a capacidade de resposta do aplicativo.
Se muitas tentativas falharem, considere impedir novas solicitações temporariamente (ver padrão Circuit Breaker).

**Idempotência**: Verifique se a operação é idempotente; se não for, repetir pode causar efeitos indesejados.
Ex.: uma solicitação processada com sucesso mas sem resposta pode ser reenviada erroneamente.

**Tipo de exceção**: Diferentes falhas geram diferentes exceções; ajuste o intervalo entre tentativas de acordo com a natureza da exceção.

**Consistência da transação**: Ao repetir operações transacionais, ajuste a política de repetição para minimizar o risco de inconsistência e reduzir a necessidade de rollback de etapas anteriores.


**Orientação Geral do Padrão de Repetição**

**Testes e desempenho**
- Garanta que todo código de repetição seja testado para diferentes condições de falha.
- Evite sobrecarregar serviços, gerar gargalos ou afetar a confiabilidade do aplicativo.

**Uso consciente da repetição**
- Implemente repetição apenas quando o contexto completo da operação falha for entendido.
- Evite múltiplas camadas de repetição encadeadas que causem atrasos desnecessários; preferir falha rápida em tarefas internas e gerenciar repetição na tarefa superior.

**Registro de falhas**
- Registre todas as falhas que desencadeiam repetição para identificar problemas subjacentes em serviços ou recursos.
- Investigue falhas frequentes para distinguir entre falhas transitórias e duradouras; trate falhas duradouras como exceções e considere alternativas, incluindo funcionalidade degradada ou serviços substitutos (ver Circuit Breaker).

**Quando usar**
- Aplicações que interagem com serviços ou recursos remotos sujeitos a falhas transitórias de curta duração.
- Repetições podem ser bem-sucedidas se a falha for temporária.

**Quando não usar**
- Falhas prováveis de serem duradouras, que prejudicam a capacidade de resposta do sistema.
- Falhas internas causadas por lógica de negócio.
- Como substituto para problemas de escalabilidade; se falhas frequentes indicarem sobrecarga do serviço, é melhor escalar o recurso.

+++ CAP9
______________________________________________________________________________________________________
AULA 14.10


CAP9
