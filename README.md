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

maVoiture est à la fois une instance de Voiture, Vehicule et Object. 
Cela s'explique en partie par la notion d'héritage qui veut que la classe Voiture extends de Vehicule et donc de manière indirecte ou directe Voiture est une instance des ces deux. 
Cependant l'héritage se fait de mère en fille et non pas entre soeurs donc maVoiture n'est pas une instance de Moto ni d'un autre type d'objet (String, Integer, Boolean, ...)


## Approfondissements 

**1. Variables et Références***
Une variable est un élément pointant vers un objet. 

Avant de comprendre la notion de **réference** on doit revenir sur la notion de mémoire vive. 

Mémoire vive => Mémoire RAM (Random Access Memory) 

Nous pouvons la rapprésenter par un ensemble de boites qui ont une adresse spécifique. Donc chaque boite aura son adresse. 

![Capture d’écran du 2023-05-15 12-31-57](https://github.com/naimatouraghe/POO-avec-JAVA/assets/80955884/683292cc-534a-474f-b9f8-087d2987e54d)

``` 
int monAge = 26; 
String maPhrase = "Hello World"
Voiture maFerrari = new Voiture("F488", "Ferrari"); 
```

Lorsque on va instancier (affecter une valeur à une variable) une nouvelle variable cela sera rangé dans une des boites de notre mémoire vive. 

De ce fait quand on appellera la variable en question, cette dernière nous servira seulement pour aller la rechercher à l'adresse qui lui aura été affectée. 

![Capture d’écran du 2023-05-15 12-44-16](https://github.com/naimatouraghe/POO-avec-JAVA/assets/80955884/d6bc35fb-f135-473a-a9e4-80c2e3125981)

Notre variable ```maFerrari``` est ainsi un pointeur qui nous sert à aller chercher l'information au bon endroit. 
Chaque case mémoire peut contenir un seul objet qui est considéré donc unique. 
Concrétement ça veut dire que si on crée deux objets idéntiques, informatiquement parlant ce sont deux réferences bien distinctes avec deux adresses diférente.

```
Voiture maFerrari = new Voiture("F488", "Ferrari");
Voiture maFerrari2 = new Voiture("F488", "Ferrari");
```


Cependant si on crée une deuxième variable qui pointe vers la réference maFerrari elles pointeront toutes les deux sur le meme objet.

```
Voiture maFerrari = new Voiture("F488", "Ferrari");
Voiture maFerrari2 = maFerrari

```
De ce fait si on décide de changer le nom de la première voiture, ce changement se repercutera sur la deuxième variable ```maFerrari2```car nos deux variables pointent vers la meme réference d'objet.


**2. Classes abstraites**

Une Classe abstraite est une Classe avec au moins une méthode abstraite. 

Une méthode ressemble globalement à celle ci: 
```
public void demarrer(){
...<code>...
}
```
Une méthode abstraite ressemble plutot à celle ci: 
```
public abstract void demarrer(); 
```

Le corps de fonction a donc totalement disparu et cette méthode abstraite n'a donc aucun comportement. 
Le fait que cette méthode soit abstraite et que elle n'ait aucun comportement implique que la Classe dans laquelle elle est déclarée est abstraite également. 
Par conséquant on ne peut pas instancier un objet à partir d'une Classe abstraite. 
Pour pouvoir conturner cette contrainte, on passera le corps de fonction dans les Classes filles. 

![Capture d’écran du 2023-05-15 13-15-40](https://github.com/naimatouraghe/POO-avec-JAVA/assets/80955884/dfdef7fa-1ce1-4529-afd6-8c385202bd0f)


**3. Interface**

**4. Méthode**

**5. Surcharge et polymorphisme** 

**6. Encapsulation, Visibilité, Getters et Setters**

**7. Projet Lombok(en finir avec les Getters et Setters?)** 

**8. Collections (List / Set)**

**9. Découverte interface STREAMS (AnyMatch / Filter / Collectors)**

**10. Map(HashMap / LinkedHasMap)**

**11.Exos**


**8. Les exceptions et comment les gérer**

[Exception handling interview questions](https://www.interviewbit.com/exception-handling-interview-questions/)

**a. Définition de l'exception en Java**

**b. Qu’est-ce que la gestion des exceptions en Java et quels sont les avantages de la gestion des exceptions?**
![Exception Handling](https://d3n0h9tb65y8q.cloudfront.net/public_assets/assets/000/003/928/original/exception_handling_in_Java.png?1680152106)


**c. Comment les exceptions sont-elles traitées dans Java?**

**d. Qu’est-ce que la propagation d’exception en Java?**
![Exception Propagation](https://d3n0h9tb65y8q.cloudfront.net/public_assets/assets/000/003/929/original/exception_propagation_in_Java.png?1680152385)

**e. Quelles sont les méthodes importantes définies dans la classe d’exception de Java ?**

**f. Que sont les exceptions d’exécution en Java?**

**g. Quelle est la différence entre les mots clés throw et throws en Java?**

**h.Comment gérez-vous les exceptions vérifiées?**





