# programmation_repartie

## TP1

Création d'un Thread, avec la classe *Thread*. On associe à un Thread un objet.
La méthode *start()* exécute le Thread. Si l'objet a implémenté l'interface *Runnable* (avec la méthode *run()*), la méthode *run()* est appelée.
Note : l'appel de la méthode run() exécute le code de la méthode, mais ne crée le thread.
Le Thread peut être arreté/bloqué avec la méthode *suspend()* (déprécié) et relancé avec la méthode *resume()*.
Une autre façon de créer un Thread, est pour l'objet d'hériter de Thread (en implémentant la méthode *run()*).

Un processus a 4 états :
- **prêt** : ressources disponibles => *start()*
- **bloqué** : ressources indisponibles, attente d'accès à une section critique, vérification d'une condition, mise en someille (*synchronized*, *wait()*, *sleep()*)
- **élu** : débloquage, exécution => *signal()*
- mort : processus tué, ou méthode *run()* terminée

Un processus est un programme en cours d'exécution. Il possède son propre espace d'adressage/espace mémoire.
Un thread est un processus avec un espace mémoire partagé (dit processus "léger").

Documentation java :
- Thread : https://docs.oracle.com/javase/7/docs/api/java/lang/Thread.html
- Runnable : https://docs.oracle.com/javase/7/docs/api/java/lang/Runnable.html



## TP2

Création de sémaphore/mutex et d'une section critique. La section critique est
entouré du bloc :
```Java
synchronized(mutex) {
    // section critique
}
```
Dans *synchronized()*, les appels des méthodes *Wait()* et *Signal()* sont automatiques.
On peut toutefois entourer la section critique, sans avoir besoin du bloc *synchronized()*.
Pour ce faire, on appelle des méthodes type wait et signal qui doivent spécifier dans leur en-tête :
```Java
public synchronized void nomMethode() {
    // some code
}

// main
waitMethode();
// section critique
signalMethode();
```


- wait() => P() (décrémentation du sémaphore)
- Signal() => V() (incrémentation du sémaphore)

Une **section critique** est un bloc de code pouvant être exécuté par plusieurs threads.
Un **ressource critique** est une ressource accessible pouvant être accessible par plusieurs thread à la fois (i.e. STDIN).
Un **sémaphore** est un verrou, qui limite l'accès à un bloc de code, une ressource.
Utilisé lorsque la ressource est critique. On utilise autant
de sémpahore que de ressources.
Pour une ressource : sémpahore **binaire**. Pour plusieurs : sémaphore **général**.


### Sources
- Cours de José Paumard :
http://blog.paumard.org/cours/java-api/chap05-concurrent.html
