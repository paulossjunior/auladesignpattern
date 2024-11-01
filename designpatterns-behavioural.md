# Padrões Comportamental

## Quando usar o Strategy ?

Quando eu quero separar o algoritmo/comportamento da estrutura da classe.

```js
class CalcularImpostoRenda {

   public int calcularImposto (valor: double){
        //Todo o comportamento ta no metodo
        if (valor < 1000){
            //realizar calculo com 10%
        }
        if (valor > 1000 and valor < 3000){
            //realizar calculo com 20%
        }

        return resultado
   }
}
```

Podemos colocar o algoritmo em classes

```js

interface Calcular {

   public int executar (valor: double) 
}

class CalcularRendaAteh1000 implments Calcular {
   public int executar (valor: double) {
    //realizar calculo com 10%
   }
}


class CalcularRendaacima1000 implments Calcular {
   public int executar (valor: double) {
    //realizar calculo com 20%
   }
}

class CalcularImpostoRenda {
    Calcular calcular;

   public int calcularImposto (valor: double){
        return calcular.executar(valor)
   }
}


CalcularImpostoRenda instance = new CalcularImpostoRenda(new CalcularRendaAteh1000() )

instance.calcularImposto(200)


CalcularImpostoRenda instance = new CalcularImpostoRenda(new CalcularRendaacima1000() )
instance.calcularImposto(200000)

```

Aplicando o Metodo Fabrica

Podemos colocar o algoritmo em classes

```js

interface Calcular {

   public int executar (valor: double) 
}

class CalcularRendaAteh1000 implments Calcular {
   public int executar (valor: double) {
    //realizar calculo com 10%
   }
}


class CalcularRendaacima1000 implments Calcular {
   public int executar (valor: double) {
    //realizar calculo com 20%
   }
}

class CalcularImpostoRenda {
    Calcular calcular;

   public int calcularImposto (valor: double){
        return calcular.executar(valor)
   }
}


class Fabrica {

    public static CalcularImpostoRenda create (valor: double){

        Calcular calcular = null;

        if (valor < 1000){
            calcular = new CalcularRendaAteh1000()
        }else{
            calcular = new CalcularRendaacima1000() 
        }

        CalcularImpostoRenda instance = new CalcularImpostoRenda(calcular)
    }
}

CalcularImpostoRenda instance = Fabrica.create(1000)
instance.calcularImposto(1000)

```
```mermaid
classDiagram
    %% Interface Calcular - Define o método de cálculo
    Class Calcular {
        <<interface>>
        +executar(valor: double) int
    }

    %% Classe CalcularRendaAteh1000 - Implementa Calcular para valores até 1000 com taxa de 10%
    Class CalcularRendaAteh1000 {
        +executar(valor: double) int
    }
    Calcular <|.. CalcularRendaAteh1000

    %% Classe CalcularRendaAcima1000 - Implementa Calcular para valores acima de 1000 com taxa de 20%
    Class CalcularRendaAcima1000 {
        +executar(valor: double) int
    }
    Calcular <|.. CalcularRendaAcima1000

    %% Classe CalcularImpostoRenda - Utiliza Calcular para calcular o imposto de renda
    Class CalcularImpostoRenda {
        -Calcular calcular
        +calcularImposto(valor: double) int
    }
    CalcularImpostoRenda ..> Calcular : usa

    %% Classe Fabrica - Cria a instância apropriada de CalcularImpostoRenda com base no valor
    Class Fabrica {
        +static create(valor: double) CalcularImpostoRenda
    }
    Fabrica ..> CalcularImpostoRenda : cria instância
    Fabrica ..> CalcularRendaAteh1000 : cria instância
    Fabrica ..> CalcularRendaAcima1000 : cria instância

```

## Quando usar a Cadeia de responsabilidade ?

Quando temos comportamentos que podem ser encadeados e passar para classes especificadas.

```js

interface Calcular {

   public boolean math (valor: double)
   public int executar (valor: double)
   public setNext(calcular: Calcular) 
}

class CalcularRendaacima1000 implments Calcular {

    Calcular next = null
   
   public boolean math (valor: double){
        return valor > 1000?  true : false   
   } 

   public setNext(calcular: Calcular){
     Calcular next = calcular
   }   

   public int executar (valor: double) {
     if (this.math(valor)){
        return //faca a aconta 
     }else {
        return this.next.executar (valor)
     }
   }
}

class Fabrica {

    calcular index = null

    public Fabrica (){

        index = new CalcularRendaAteh1000()
        calcular calcularRendaacima1000 = new CalcularRendaacima1000()

        //Criando a lista encadeada
        calculareh1000.setNext(calcularRendaacima1000)

    }

    public static CalcularImpostoRenda create (){
            return index
    }
}

Calcular instance = Fabrica.create()
//executa a conta de até 1000 reais chamando CalcularRendaAteh1000
instance.executar(900)
//executa a conta acima de 1000 reais chamando CalcularRendaacima1000
instance.executar(1900)

```
```mermaid
ClassDiagram
    %% Interface Calcular - Define métodos para a cadeia de responsabilidade
    class Calcular {
        <<interface>>
        +math(valor: double) boolean
        +executar(valor: double) int
        +setNext(calcular: Calcular)
    }

    %% Classe CalcularRendaAcima1000 - Implementa Calcular para valores acima de 1000
    Class CalcularRendaAcima1000 {
        -Calcular next
        +math(valor: double) boolean
        +setNext(calcular: Calcular)
        +executar(valor: double) int
    }
    Calcular <|.. CalcularRendaAcima1000

    %% Classe CalcularRendaAteh1000 - Implementa Calcular para valores até 1000
    Class CalcularRendaAteh1000 {
        -Calcular next
        +math(valor: double) boolean
        +setNext(calcular: Calcular)
        +executar(valor: double) int
    }
    Calcular <|.. CalcularRendaAteh1000

    %% Classe Fabrica - Cria a cadeia de responsabilidades para Calcular
    Class Fabrica {
        -Calcular index
        +Fabrica()
        +static create() Calcular
    }
    
    %% Relacionamento de Fabrica com os nós da cadeia
    Fabrica ..> CalcularRendaAteh1000 : inicializa
    Fabrica ..> CalcularRendaAcima1000 : inicializa
    CalcularRendaAteh1000 --> CalcularRendaAcima1000 : next

```