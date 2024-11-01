# Padrões Criativos

## Quando usar o Método Fabrica?

**Quando precisarmos organizar os Instanciações!**  

```js
class Model(){

}

class ModelX(){

}

import Model
import ModelX
import x.yz.g.z.Model

Model model = new Model()
Model modelx = new ModelX()
Model modelxx = new ModelX()
Model modelxx = new ModelX()

```

* Usando Metodo Fabrica

```js
class Model(){

}

class ModelX(){

}


class Fabrica {
    import Model
    import ModelX
    import x.yz.g.z.Model

    public static Object createModel(String modelName) {
        switch (modelName) {
            case "Model":
                return new Model();
            case "ModelX":
                return new ModelX();
            default:
                throw new IllegalArgumentException("Modelo desconhecido: " + modelName);
        }
    }
}

c/ Uso da classe Fabrica para criar instâncias
Model model = (Model) Fabrica.createModel("Model");
ModelX modelx = (ModelX) Fabrica.createModel("ModelX");

```
## Model Fabrica
```mermaid
classDiagram
    c% Classe Model - Representa um tipo de modelo
    class Model {
    }

    c% Classe ModelX - Representa outro tipo de modelo
    class ModelX {
    }

    c% Classe Fabrica - Implementa o método de fábrica
    class Fabrica {
        +static createModel(modelName: String) Object
    }

    %% Relações de Fabrica com Model e ModelX
    Fabrica ..> Model : createModel("Model")
    Fabrica ..> ModelX : createModel("ModelX")

```

### Quando usar o Método Fabrica Abstrata?

Resposta: Para definir um padrão de Métodos Fabricas

```js
class Model(){

}

class ModelX(){

}


class FabricaModel {
    import Model

    public static createModel(String modelName){
        return funcaoparaInstanciar(modelName)

    }
}

class FabricaModelX {
    import ModelX

    public static createX(String modelName){
        return funcaoparaInstanciar(modelName)

    }
}

Model model = Fabrica.createModel("Model")
Model modelx = FabricaModelX.createX("Modelx")

```

Aplicando Fabrica Abstrata

```js
interface FabricaAbstrata {

    public any create(String nomedofi)
}

class Model(){

}

class ModelX(){

}


class FabricaModel implements FabricaAbstrata{
    import Model

    public any create(String nomedofi){
        return funcaoparaInstanciar(modelName)

    }
}

class FabricaModelX implements FabricaAbstrata {
    import ModelX

    public any create(String nomedofi){{
        return funcaoparaInstanciar(modelName)

    }

}

Model model = Fabrica.create("Model")
Model modelx = FabricaModelX.create("Modelx")

```
## Modelo do Fabrica Abstrata

```mermaid
classDiagram
    %% Interface FabricaAbstrata - Declara o método de fábrica
    class FabricaAbstrata {
        +create(nomedofi: String) any
    }

    c% Classe Model - Representa um tipo de modelo
    class Model {
    }

    c% Classe ModelX - Representa outro tipo de modelo
    class ModelX {
    }

    c% Classe FabricaModel - Implementa a interface FabricaAbstrata para criar instâncias de Model
    class FabricaModel {
        +create(nomedofi: String) any
    }

    c% Classe FabricaModelX - Implementa a interface FabricaAbstrata para criar instâncias de ModelX
    class FabricaModelX {
        +create(nomedofi: String) any
    }

    FabricaAbstrata <|-- FabricaModel
    FabricaAbstrata <|-- FabricaModelX
    FabricaModel ..> Model : create("Model")
    FabricaModelX ..> ModelX : create("ModelX")
``` 

## Quando usar o Builder?

Quando temos que definir etapas para criar um objeto! Em objetos complexos

```js
class Usuario {

    
}

class endereco {

    usuario:usuario
}

usuario Usuario = new Usuario()
endereco endereco = new Endereco (usuario)

```

Perceba que para criar o Endereco é necessário ter um usuario .. assim ele é complexo

Forçando a Barra com o builder

```js
class BuilderEndereco {

    public Endereco create (nome_usuario: string){
         Usuario usuario = Fabrica.create (nome_usuario)
        return new Endereco(usuario)
    }
}
class FabricaEndereco {

    create (nome_usuario: String){
       
        Endereco endereco = BuilderEndereco.create (nome_usuario)
        return endereco

    } 

}

Endereco endereco = FabricaEndereco.create("Zé")
```
## Model
```mermaid
classDiagram
    c% Classe BuilderEndereco - Responsável por construir o Endereco
    class BuilderEndereco {
        +Endereco create(nome_usuario: String)
    }

    c% Classe FabricaEndereco - Fabrica que utiliza o BuilderEndereco para criar Endereco
    class FabricaEndereco {
        +Endereco create(nome_usuario: String)
    }

    c% Classe Usuario - Representa o usuário
    class Usuario {
    }

    c% Classe Endereco - Representa o endereço associado ao usuário
    class Endereco {
        +Endereco(usuario: Usuario)
    }

    c% Relacionamentos entre as classes
    FabricaEndereco ..> BuilderEndereco : utiliza
    BuilderEndereco ..> Endereco : create
    Endereco o-- Usuario : associação

```
## Quando usar Singleton?

Quando queremos ter um ponto único para controlar o acesso e o uso de um recurso.

Por exemplo, controlar o número de requisições no banco de dados.

```js

class ControlarRequisicao{

    private instance: ControlarRequisicao

    // Metodo contrutor privado
    private ControlarRequisicao()
    // Unico metodo para criar a instancia
    public static ControlarRequisicao create(){
        
        if (instance == null){
            this.instance = new ControlarRequisicao()
        }

        return this.instance

    }
}

ControlarRequisicao controlarRequisicao = ControlarRequisicao.create();

```
### Model
```mermaid
classDiagram
    c% Classe ControlarRequisicao - Implementa o padrão Singleton
    class ControlarRequisicao {
        -instance: ControlarRequisicao
        -ControlarRequisicao() // Construtor privado
        +static create(): ControlarRequisicao
    }
```

## Quando usar Prototype?

cuando queremo criar instancias de uma mesma classe de forma rapida. 

```js
interface FabricaAbstrata {

    public any create(String nomedofi)
}

class Model(){

}


class FabricaModel implements FabricaAbstrata{
    import Model

    public any create(String nomedofi){
        return funcaoparaInstanciar(modelName)

    }
}


Model model = Fabrica.create("Model")
Model model = Fabrica.create("Model")
Model model = Fabrica.create("Model")
Model model = Fabrica.create("Model")


```
criando Clones da minha classe com dados já preenchidos.

```js
interface FabricaAbstrata {

    public any create(String nomedofi)
}

interface Prototype <T> {

    public T clone()
}

class Model implements Prototype{

    nome: string

    public Model clone(){

        return new Mode(nome)
    }

}


class FabricaModel implements FabricaAbstrata{
    import Model

    public any create(String nomedofi){
        return funcaoparaInstanciar(modelName)

    }
}


Model model = Fabrica.create("Model")
model.setNome = "Zé"
Model modelx = model.clone()
modelx.setNome = "Joao"
Model modely = model.clone()
modely.setNome = "xxx"
Model modelz = model.clone()
```
```mermaid
classDiagram
    %% Interface FabricaAbstrata - Declara o método de fábrica
    class FabricaAbstrata {
        <<interface>>
        +create(nomedofi: String) any
    }

    %% Interface Prototype - Declara o método clone
    class Prototype {
        <<interface>>
        +clone() any
    }

    c% Classe Model - Implementa Prototype e possui um atributo nome
    class Model {
        -nome: String
        +clone() Model
    }
    Prototype <|.. Model

    c% Classe FabricaModel - Implementa FabricaAbstrata e utiliza Model
    class FabricaModel {
        +create(nomedofi: String) any
    }
    FabricaAbstrata <|.. FabricaModel
    FabricaModel ..> Model : utiliza

```

