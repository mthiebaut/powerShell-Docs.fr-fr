# <a name="contributing-to-powershell-documentation"></a>Contribution à la documentation de PowerShell

Merci de l’intérêt que vous portez à la documentation de PowerShell ! Lisez ce qui suit pour savoir comment contribuer à notre documentation technique.

>Si vous voulez des informations générales sur la façon de bien démarrer avec Git et GitHub, consultez [l’aide de GitHub](https://help.github.com/). 

## <a name="sign-a-cla"></a>Signer un contrat de licence de contribution

Avant de pouvoir contribuer au contenu d’un dépôt PowerShell, vous devez [signer un contrat de licence de contribution Microsoft](https://cla.microsoft.com/). Si vous avez déjà contribué à des dépôts PowerShell, félicitations ! Vous avez déjà effectué cette étape.

## <a name="providing-feedback-on-powershell-documentation"></a>Envoi de commentaires sur la documentation de PowerShell

Vous pouvez signaler des erreurs, proposer des changements ou demander de nouvelles rubriques en [créant une question](https://help.github.com/articles/creating-an-issue/) dans la [page des questions du dépôt PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs/issues).

Les membres de l’équipe de la documentation PowerShell consultent régulièrement les questions, les trient, les attribuent et les traitent en conséquence.

## <a name="writing-powershell-documentation"></a>Rédaction de la documentation de PowerShell

L’une des façons les plus simples de contribuer à PowerShell consiste à participer à l’écriture et à la modification de la documentation. Toute notre documentation hébergée sur GitHub est écrite à l’aide de la syntaxe GFM [(GitHub Flavored Markdown)](https://help.github.com/articles/github-flavored-markdown/).

## <a name="making-minor-edits-to-existing-topics"></a>Apport de modifications mineures à des rubriques existantes

Pour [modifier un fichier existant](https://help.github.com/articles/editing-files-in-another-user-s-repository/), accédez simplement au fichier, puis cliquez sur le bouton Modifier. GitHub crée automatiquement votre propre branchement de notre dépôt où vous pouvez apporter vos modifications. Une fois que vous avez terminé, enregistrez vos modifications et envoyez une [demande de tirage (Pull)](https://help.github.com/articles/creating-a-pull-request/) à la branche de *préproduction* du dépôt [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs). Une fois que la demande Pull est créée, un membre de l’équipe de documentation de PowerShell examine vos modifications avant de les fusionner dans la branche de *préproduction*.

## <a name="making-major-edits-to-existing-topics"></a>Apport de modifications majeures à des rubriques existantes

Si vous apportez des modifications substantielles à un article existant, ajoutez ou modifiez des images, ou contribuez à un nouvel article, vous devez créer manuellement votre branchement GitHub, puis le cloner sur votre ordinateur local. Un branchement est un réplica GitHub du dépôt principal, sous votre compte GitHub, qui vous fournit une copie de travail que vous pouvez utiliser de manière isolée. Vous allez créer des demandes Pull à partir de votre branchement. De même, un clone est un réplica local du dépôt qui, dans ce cas, est un clone de votre branchement. Le clone vous permet de travailler sur des dépôts Git en mode hors connexion et avec des logiciels/outils natifs plus puissants.

Voici le workflow pour apporter des modifications majeures à la documentation existante :

1. [Créez un branchement](https://help.github.com/articles/fork-a-repo/) du dépôt [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).
2. [Créez un clone de votre branchement](https://help.github.com/articles/cloning-a-repository/) sur votre ordinateur local.
3. Créez une branche locale dans votre dépôt cloné.
4. Apportez des modifications aux fichiers que vous souhaitez mettre à jour dans un éditeur de texte Markdown. 
   Voir ci-dessous pour connaître les éditeurs de texte Markdown couramment utilisés.
5. [Envoyez votre branche locale](https://help.github.com/articles/pushing-to-a-remote/) sur votre branchement.
6. [Créez une demande Pull](https://help.github.com/articles/creating-a-pull-request/) dans la branche de *préproduction* du dépôt [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs).

## <a name="creating-new-topics"></a>Création de nouvelles rubriques

Si vous souhaitez contribuer à la nouvelle documentation, commencez par rechercher les [questions marquées comme « en cours »](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) pour vérifier que vous ne travaillez pas inutilement.
Si personne ne semble travailler sur ce que vous avez prévu :

* Ouvrez une nouvelle question et étiquetez-la comme « en cours » (si vous êtes membre de l’organisation PowerShell) ou ajoutez « en cours » en commentaire pour indiquer aux autres personnes que vous travaillez dessus.
* Suivez le même workflow que décrit ci-dessus pour apporter des modifications majeures à des rubriques existantes.
* Modifiez la rubrique `TOC.md` (située dans le dossier de niveau supérieur de chaque ensemble de documentation) pour ajouter vos nouvelles rubriques à la table des matières. 
  Déterminez où se trouve votre nouvelle rubrique dans la table des matières et ajoutez un titre de niveau approprié, avec un lien vers votre rubrique (`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Éditeurs de texte Markdown

Voici quelques éditeurs de texte Markdown que vous pouvez essayer :

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GFM (GitHub Flavored Markdown)

Tous les articles de ce dépôt utilisent [GFM (GitHub Flavored Markdown)](https://help.github.com/articles/github-flavored-markdown/).

Une partie de la syntaxe GFM de base inclut :

* **Sauts de ligne et paragraphes :** Dans Markdown, il n’existe pas d’élément HTML `<br />` ni `<p />`. À la place, un nouveau paragraphe est désigné par une ligne vide entre deux blocs de texte.

> **Remarque** : Ajoutez une nouvelle ligne unique après chaque phrase pour simplifier la sortie de ligne de commande des différences et de l’historique.
Cette pratique n’est pas encore adoptée dans tout PowerShell-Docs, mais nous travaillons dans ce but à terme. Votre aide est la bienvenue. 

* **Italique :** l’élément HTML `<em>some text</em>` est écrit sous la forme `*some text*`
* **Gras :** l’élément HTML `<strong>some text</strong>` est écrit sous la forme `**some text**`
* **Titres :** les titres HTML sont désignés à l’aide de caractères `#` au début de la ligne. 
  Le nombre de caractères `#` correspond au niveau hiérarchique du titre (par exemple, `#` = `<h1>` et `###` = ```<h3>```).
* **Listes numérotées :** pour qu’une liste numérotée (mise en ordre) commence la ligne par `1. `.  
  Si vous souhaitez plusieurs éléments dans un seul élément de liste, mettez votre liste en forme comme suit :
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
pour obtenir ce résultat :

1.  Pour le premier élément (comme celui-ci), insérez un taquet de tabulation après le 1. 

    Pour inclure un deuxième élément (comme celui-ci), insérez un saut de ligne après le premier et alignez les mises en retrait.

* **Listes à puces :** les listes à puces (non triées) sont presque identiques aux listes mises en ordre, sauf que `1. ` est remplacé par `* `, `- ` ou `+ `. Plusieurs listes d’éléments fonctionnent de la même façon qu’avec les listes mises en ordre.
* **Liens :** la syntaxe d’un lien hypertexte est `[visible link text](link URL)`.
* **Lien vers une autre rubrique dans le même ensemble de documents :** un ensemble de documents est un dossier de niveau supérieur dans ce dépôt (par exemple, « dsc », « scripting »).
    La syntaxe d’un lien hypertexte vers une rubrique dans le même ensemble de documents est `[topic title](relative path to topic)`. 
    Pour plus d’informations, voir [Relative links in READMEs (Liens relatifs dans les fichiers Lisez-moi)](https://help.github.com/articles/relative-links-in-readmes/). 
    Pour créer un lien vers une rubrique dans un autre dossier de niveau supérieur, utilisez l’URL de la page publiée, comme décrit ci-dessus.
