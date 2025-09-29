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
