# das-1-2025-2-a

aula 1 - 04/08

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
aula 2 - 05/08

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
aula 3 - 11/08
SOLID
  Princípio da inversão de dependências
    Esse princípio recomenda que uma classe cliente deve estabelecer dependências prioritariamente com abstrações e não com implementações concretas, pois abstrações (isto é,            interfaces) são mais estáveis do que implementações concretas (isto é, classes). A ideia é então trocar (ou inverter) as dependências: em vez de depender de classes concretas, clientes devem depender de interfaces. Portanto, um nome mais intuitivo para o princípio seria Prefira Interfaces a Classes.

  Prefira composição a herança

      "Herança expõe para subclasses detalhes de implementação das classes pai. Logo, frequentemente diz-se que herança viola o encapsulamento das classes pai. A implementação das         subclasses se torna tão acoplada à implementação da classe pai que qualquer mudança nessas últimas pode forçar modificações nas subclasses."
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
aula 4 - 12/08

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
