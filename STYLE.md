# <a name="style-guide-for-powershell-docs"></a>Guide de style pour les documents PowerShell


## <a name="titlesheadings"></a>Titres/En-têtes

* Les titres/en-têtes (tout élément précédé de \#) doivent être suivis d’un saut de ligne
* Seule la première lettre d’un titre et les noms propres dans ce titre doivent être en majuscule
* Un document ne peut contenir qu’un seul titre H1
* Lorsque vous modifiez le contenu de référence, les titres H2 sont indiqués par platyPS et ne doivent pas être ajoutés ou supprimés, sous peine d’entraîner une défaillance de la build
* Utilisez uniquement des en-têtes de style \# (par opposition à = ou aux en-têtes de style \-)

### <a name="correct"></a>Correct

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a>Incorrect

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a>Syntaxe

* Si vous parlez d’une applet de commande dans un paragraphe, utilisez \` pour mettre en surbrillance les noms des applets de commande
  * Exemple correct : cette applet de commande `Write-Host` peut...
  * Exemple incorrect : cette applet de commande **Write-Host** peut... et le pipeline pour fichier de sortie de l’applet de commande pour...
* Lorsque vous écrivez un article (par opposition à du contenu de référence), la première instance d’un nom d’applet de commande doit être un lien vers la documentation de l’applet de commande
* Tous les blocs de syntaxe PowerShell doivent utiliser &#96;&#96;&#96;powershell
* Ne démarrez pas les commandes PowerShell par « `PS C:\>` »
  * Exemple correct :
  ```powershell
  Get-Process
  ```
  * Exemple incorrect :
  ```powershell
  PS C:\> Get-Process
  ```
* La sortie émise par les commandes PowerShell doit être placée en commentaire pour éviter que la mise en surbrillance de la syntaxe ne lui soit appliquée
* Les noms des propriétés et les noms des paramètres doivent être en **gras**
* Les applets de commande PowerShell utilisent la « [casse Pascal](https://en.wikipedia.org/wiki/PascalCase) ». Les verbes sont séparés des noms par un trait d’union.

## <a name="lists"></a>Listes

* Les éléments d’une liste ne doivent pas se terminer par un point (sauf s’ils contiennent plusieurs phrases)
* Si votre liste contient plusieurs phrases, envisagez d’utiliser un en-tête 3/4/5 (si applicable) en dessous de l’idée principale

## <a name="links"></a>Links

* Les liens sont toujours marqués à l’aide de la syntaxe `[friendlyname](url)` MarkDown
* Les liens doivent avoir un nom convivial, si possible, correspondant souvent au titre de la page liée
  * **Exception** : les liens pointant vers des sites non Microsoft ne doivent contenir qu’une URL
* Tous les éléments de la section « liens connexes » en bas de la page doivent contenir des liens hypertexte. 

## <a name="line-breaks"></a>Sauts de ligne

* Vous devez inclure des sauts de ligne sémantiques
* Vous devez limiter les lignes à 100 caractères (élément ouvert : outils pour nous aider à valider ceci)
* Vous POUVEZ supprimer les sauts de ligne supplémentaires pour PS4+, mais PAS pour ps3 (validation nécessaire)
