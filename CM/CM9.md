# Lecture 9 - Logging

## Définition du Logging
Le logging permet de gérer l'émission et le stockage de messages (traces) déclenchés par différents événements durant l'exécution d'un programme.

## API de Logging
Une API de logging est composée de trois éléments principaux :
- **Logger** : Émet des messages, généralement avec un niveau de sévérité associé
- **Formatter** : Formate le contenu des messages
- **Appender/Handler** : Envoie les messages vers une destination de stockage

## Exemple d'implémentation
```java
import java.util.logging.Logger;
import java.util.logging.Level;
import java.util.Arrays;

public class Main {
    private static final Logger LOGGER = Logger.getLogger(Main.class.getName());
    
    public static void main(String[] args) {
        LOGGER.info("Démarrage de la simulation...");
        LOGGER.config("Paramètres : " + Arrays.toString(args));
    }
}
```

## Niveaux de Log
Les niveaux standard (par ordre décroissant de sévérité) :

| Niveau    | Valeur | Description |
|-----------|--------|-------------|
| SEVERE    | 1000   | Erreurs critiques |
| WARNING   | 900    | Avertissements |
| INFO      | 800    | Informations générales |
| CONFIG    | 700    | Configuration |
| FINE      | 500    | Détails |
| FINER     | 400    | Traces détaillées |
| FINEST    | 300    | Traces très détaillées |

## Configuration des niveaux
### Via fichier `logging.properties`
```properties
# Limite l'affichage console aux messages de niveau FINE et supérieur
java.util.logging.ConsoleHandler.level = FINE
```

### Par code
```java
LOGGER.setLevel(Level.INFO);  // Ne loggue que INFO et supérieur
```

## Handlers JDK
Principaux types de handlers :
- **ConsoleHandler** : Sortie vers la console (System.err par défaut)
- **FileHandler** : Écriture dans un fichier
- **SocketHandler** : Envoi via socket réseau
- **MemoryHandler** : Bufferisation en mémoire

## Exemple avec FileHandler
```java
try {
    Handler fileHandler = new FileHandler("application.log"); 
    fileHandler.setLevel(Level.ALL);
    LOGGER.addHandler(fileHandler);
} 
catch (SecurityException | IOException ex) {
    LOGGER.log(Level.SEVERE, "Échec de configuration du logger", ex);
}
```