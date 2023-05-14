# POO-avec-JAVA

Bases et approfondissements de la programmation orientée objet en Java.

Ce paradigme peut se resumer par `Tout est objet`.

## Les bases

**1. Objets**


**Définition**

Les objets sont un ensemble de méthodes et attribus stockés dans une variable.

**Exemples**


```
public class HelloWorld {

    public static void main(String[] args){

            System.out.printIn("Hello objects!");

            Date currentDate = new Date();


            System.out.printIn("Aujourd'hui on est le jour -> " + currentDate.getDay() );
            System.out.printIn("Aujourd'hui on est le mois de -> " + currentDate.getMonth() );
            System.out.printIn("Aujourd'hui on est l'année -> " + currentDate.getYear() );

    }

}
```

Ici on peut distinguer 2 objets : **System** et **currentDate**.

```
L'objets Voiture peut avoir deux attribus:

- Nom
- Marque

Et posséder deux méthodes :

- démarrer()
- avancer()

``` 
**2. Les classes**

Les classes sont des modèles d'objets. Elles servent à définir l'objet (méthodes et attribus) un peu comme un moule.

```
class Voiture {

    String nom;
    String marque;

    public void démarrer(){
        ...
    }
    public void avancer(){
        ...
    }

}
```
Cet objet a donc 2 attributs et 2 méthodes.

**3. Instances**

À partir de notre modèle d'objet on peut facilement créer un objet de type Ferrari.

La Ferrari sera considérée ainsi comme une instance de la Classe Voiture

```

- F488
- Ferrari

- démarrer()
- avancer()

```

Afin de pouvoir instancier des objets à partir du modèle d'objet(ou Classe) on va se servir du `constructeur`.
Le constructeur en bref est une méthode avec le superpouvoir de création d'instrances.

```
class Voiture {
String nom;
String marque;

    public Voiture voiture(String nom, String marque){
        this.nom= nom;
        this.marque= marque;
    }
    public void démarrer(){
        ...
    }
    public void avancer(){
        ...
    }

}
```

Pour instancier on aura ensuite à déclarer une variable maFerrari de type Voiture(nom de la Classe) qui contiendra la création (new) de notre Voiture(Classe) en lui passant en paramètres son nom (F488) et son modèle (Ferrari).
Suite à la création de l'instance on pourra alors se servir des méthodes déclaré dans la Classe Voiture.

```
Voiture maFerrari = new Voiture("F488","Ferrari");

maFerrari.demarrer()
maFerrari.avancer()
```

**4. L'héritage**

Dans l'exemple suivant on va vouloir créer deux modèles d'objets afin de pouvoir instancier des voitures et des motos.

```
class Voiture {
String nom;
String marque;

    public Voiture voiture(String nom, String marque){
        this.nom= nom;
        this.marque= marque;
    }
    public void démarrer(){
        ...
    }
    public void avancer(){
        ...
    }

    public void activerAirBag(){
    ...
    }

}

class Moto {
String nom;
String marque;

    public Voiture voiture(String nom, String marque){
        this.nom= nom;
        this.marque= marque;
    }
    public void démarrer(){
        ...
    }
    public void avancer(){
        ...
    }

    public void mettreLaBequille(){
    ...
    }

}

```
On peut noter que dans cette architecture de code nous avons le 80% du code qui se repète( meme attribus, constructeur et des méthodes similaires ).
Afin de ne pas se répéter nous allons utiliser le concept d'héritage et refactorer le code ainsi:

```
class Vehicule {
String nom;
String marque;

    public Vehicule vehicule(String nom, String marque){
        this.nom= nom;
        this.marque= marque;
    }
    public void démarrer(){
        ...
    }
    public void avancer(){
        ...
    }

}
```

En créant une `Classe mère` Vehicule on va pouvoir rassembler le 80% du code qui aurait été similaire en créant 2 classes (moto et voiture).
De cette manière on va pouvoir créer 2 `Classes filles` qui extendent de la `classe Mère`.

```
class Voiture extends Vehicule {

...

    public void activerAirBag(){
        ...
    }

}

class Moto extends Vehicule {

...

    public void mettreLaBequille(){
        ...
    }

}

```

**5. InstanceOf**

**Instance** : objet crée à partir d'une classe

```
Voiture maVoiture = new Voiture("F488", "Ferrari");

class Voiture extends Vehicule {
...
    public void activerAirBag() {
    ...
    }
}
```

- if(maVoiture instanceof Voiture) => true
- if(maVoiture instanceof Vehicule) => true
- if(maVoiture instanceof Object) => true

- if(maVoiture instanceof Moto) => false
- if(maVoiture instanceof Integer) => false



## Approfondissements 

**1. Variables et Références**

**2. Classes abstraites**

**3. Interface**

**4. Méthode**

**5. Surcharge et polymorphisme** 

**6. Encapsulation, Visibilité, Getters et Setters**

**7. Projet Lombok(en finir avec les Getters et Setters?)** 
