# Projet SAE 05 - Traitement de données

## TP 2.2
**SCHER Florian**  
**DAIRIN Côme**

# - PokéRadar -

## PokéFiche et Pokéstats

### ▶ Fonctionnement en front-end :

L'utilisateur entre un identifiant de Pokémon dans le programme via la commande suivante :  
```bash
pokefiche.py --verbose=[y|n] <id_pokemon>
```

## Options

### `--verbose=y`
- Cette option permet d'afficher les informations de débogage, telles que :
  - La création des répertoires nécessaires.
  - La gestion du cache.
  - Les étapes de récupération des données pour générer la fiche du Pokémon.

### `--verbose=n`
- Cette option désactive les messages de débogage et présente uniquement les résultats de la fiche du Pokémon, sans les informations supplémentaires.

# Fonctionnement en Back-End

## Bibliothèques utilisées

- **Requests** : Utilisée pour effectuer les requêtes vers l'API PokéAPI afin de récupérer les informations des Pokémon.
- **Markdown** : Permet de générer des documents au format Markdown, facilitant ainsi la présentation des fiches Pokémon.
- **Matplotlib** : Employée pour créer les diagrammes circulaires représentant la répartition des types du Pokémon dans son lieu d'apparition.
- **Json** : Sert à convertir les données récupérées depuis l'API (en format XML) en format JSON pour une manipulation plus facile.
- **OS** : Utilisée pour gérer les répertoires nécessaires au stockage des fichiers générés, ainsi que pour la gestion du cache.
- **Sys** : Permet de gérer les arguments de la ligne de commande pour personnaliser l'exécution du programme (par exemple, pour activer ou désactiver le mode verbose).

# Implémentation du Cache

Les programmes `stats.py` et `pokefiche.py` utilisent la fonction suivante pour gérer le cache des données :


def request_cached_data(url: str, filename: str, limit: int=0, offset: int=0, verbose: bool=False) -> dict:

Cette fonction permet de vérifier si une donnée est déjà présente dans le cache avant de faire
    une nouvelle requête vers l'API. Si la donnée est absente, elle est récupérée et ajoutée
    au cache pour les futures requêtes.
    
    Arguments :
    - `url` : L'URL de l'API à interroger.
    - `filename` : Le nom du fichier utilisé pour stocker la donnée en cache.
    - `limit` : Limite du nombre de résultats à récupérer (par défaut 0).
    - `offset` : Décalage des résultats (par défaut 0).
    - `verbose` : Si True, affiche des informations de débogage (par défaut False).
    
    Retourne :
    - Un dictionnaire contenant les données récupérées (soit depuis le cache, soit via l'API).
    """

# Mise en Forme

Les deux programmes `stats.py` et `pokefiche.py` utilisent la fonction suivante pour convertir des fichiers Markdown en HTML :

```python
def convert(input_f: str, output_f: str, page_name: str="Converted") -> None:
    """
    Cette fonction convertit un fichier Markdown en HTML.

    Arguments :
    - `input_f` : Le fichier d'entrée au format Markdown.
    - `output_f` : Le fichier de sortie au format HTML.
    - `page_name` : Le nom de la page HTML générée (par défaut "Converted").

    Cette fonction prend les données formatées en Markdown et les convertit en HTML. 
    Les documents générés incluent des styles permettant :
    - De modifier la police de texte.
    - De centrer les tableaux.
    - D'ajouter des marges pour une lecture plus agréable.
    """
# Choix Techniques et Difficultés

- **Stockage des documents** :  
  Les fichiers générés sont stockés dans des répertoires séparés, permettant un accès facile aux résultats. Les répertoires sont créés automatiquement si nécessaire.

- **Gestion des erreurs** :  
  Des blocs `try-except` ont été utilisés pour mieux gérer les erreurs et fournir des messages d'erreur clairs à l'utilisateur en cas de problème.

- **Recherche de lieux** :  
  Le programme `PokéStats` permet de rechercher un lieu où un Pokémon peut être trouvé. Si l'utilisateur ne spécifie pas complètement le lieu, une liste de suggestions est proposée pour faciliter la recherche.

- **Option de debug `--verbose`** :  
  L'option `--verbose` permet d'afficher des messages de débogage pour suivre l'exécution du programme et l'accès au cache, ce qui est utile pour détecter des problèmes ou comprendre le flux du programme.

- **Limitations de l'API** :  
  Certaines données récentes sont manquantes dans l'API, ce qui a conduit à omettre certaines traductions et à utiliser des valeurs par défaut comme "???" pour les Pokémon légendaires ou les Ultra-Chimères qui n'ont pas d'habitat ou de description disponibles.

- **Accessibilité des fichiers** :  
  Les programmes créent leurs répertoires de manière autonome et stockent les fichiers en sortie dans ces répertoires, garantissant ainsi une organisation des fichiers efficace et automatique.

- **Style et présentation** :  
  Les documents Markdown et HTML générés contiennent des balises de style pour améliorer l’apparence visuelle. La mise en forme inclut des marges et des éléments centrés pour rendre la lecture plus fluide et agréable.

## 📧 Contact  

Pour toute question ou assistance, veuillez contacter :  
- **Nom :** Florian Scher  
- **Email :** florian.scher.pro@mail.com  

---

## 🏗️ Auteurs  

- **Florian Scher** – Créateur et développeur ayant participé au programme
- **LeCDROM** - Chef du projet, créateur et et développeur du programme. D'autre projets du **LeCDROM** : https://github.com/LeCDrom

---
