# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="01330-101">Guide de style pour les documents PowerShell</span><span class="sxs-lookup"><span data-stu-id="01330-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="01330-102">Titres/En-têtes</span><span class="sxs-lookup"><span data-stu-id="01330-102">Titles/Headings</span></span>

* <span data-ttu-id="01330-103">Les titres/en-têtes (tout élément précédé de \#) doivent être suivis d’un saut de ligne</span><span class="sxs-lookup"><span data-stu-id="01330-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="01330-104">Seule la première lettre d’un titre et les noms propres dans ce titre doivent être en majuscule</span><span class="sxs-lookup"><span data-stu-id="01330-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="01330-105">Un document ne peut contenir qu’un seul titre H1</span><span class="sxs-lookup"><span data-stu-id="01330-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="01330-106">Lorsque vous modifiez le contenu de référence, les titres H2 sont indiqués par platyPS et ne doivent pas être ajoutés ou supprimés, sous peine d’entraîner une défaillance de la build</span><span class="sxs-lookup"><span data-stu-id="01330-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="01330-107">Utilisez uniquement des en-têtes de style \# (par opposition à = ou aux en-têtes de style \-)</span><span class="sxs-lookup"><span data-stu-id="01330-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="01330-108">Correct</span><span class="sxs-lookup"><span data-stu-id="01330-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="01330-109">Incorrect</span><span class="sxs-lookup"><span data-stu-id="01330-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="01330-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01330-110">Syntax</span></span>

* <span data-ttu-id="01330-111">Si vous parlez d’une applet de commande dans un paragraphe, utilisez \\` pour mettre en surbrillance les noms des applets de commande</span><span class="sxs-lookup"><span data-stu-id="01330-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="01330-112">Exemple correct : cette applet de commande `Write-Host` peut...</span><span class="sxs-lookup"><span data-stu-id="01330-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="01330-113">Exemple incorrect : cette applet de commande **Write-Host** peut... et le pipeline pour fichier de sortie de l’applet de commande pour...</span><span class="sxs-lookup"><span data-stu-id="01330-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="01330-114">Lorsque vous écrivez un article (par opposition à du contenu de référence), la première instance d’un nom d’applet de commande doit être un lien vers la documentation de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="01330-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="01330-115">Tous les blocs de syntaxe PowerShell doivent utiliser &#96;&#96;&#96;powershell</span><span class="sxs-lookup"><span data-stu-id="01330-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="01330-116">Ne démarrez pas les commandes PowerShell par « `PS C:\>` »</span><span class="sxs-lookup"><span data-stu-id="01330-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="01330-117">Exemple correct :</span><span class="sxs-lookup"><span data-stu-id="01330-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="01330-118">Exemple incorrect :</span><span class="sxs-lookup"><span data-stu-id="01330-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="01330-119">La sortie émise par les commandes PowerShell doit être placée en commentaire pour éviter que la mise en surbrillance de la syntaxe ne lui soit appliquée</span><span class="sxs-lookup"><span data-stu-id="01330-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="01330-120">Les noms des propriétés et les noms des paramètres doivent être en **gras**</span><span class="sxs-lookup"><span data-stu-id="01330-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="01330-121">Les applets de commande PowerShell utilisent la « [casse Pascal](https://en.wikipedia.org/wiki/PascalCase) ».</span><span class="sxs-lookup"><span data-stu-id="01330-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="01330-122">Les verbes sont séparés des noms par un trait d’union.</span><span class="sxs-lookup"><span data-stu-id="01330-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="01330-123">Listes</span><span class="sxs-lookup"><span data-stu-id="01330-123">Lists</span></span>

* <span data-ttu-id="01330-124">Les éléments d’une liste ne doivent pas se terminer par un point (sauf s’ils contiennent plusieurs phrases)</span><span class="sxs-lookup"><span data-stu-id="01330-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="01330-125">Si votre liste contient plusieurs phrases, envisagez d’utiliser un en-tête 3/4/5 (si applicable) en dessous de l’idée principale</span><span class="sxs-lookup"><span data-stu-id="01330-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="01330-126">Links</span><span class="sxs-lookup"><span data-stu-id="01330-126">Links</span></span>

* <span data-ttu-id="01330-127">Les liens sont toujours marqués à l’aide de la syntaxe `[friendlyname](url)` MarkDown</span><span class="sxs-lookup"><span data-stu-id="01330-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="01330-128">Les liens doivent avoir un nom convivial, si possible, correspondant souvent au titre de la page liée</span><span class="sxs-lookup"><span data-stu-id="01330-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="01330-129">**Exception** : les liens pointant vers des sites non Microsoft ne doivent contenir qu’une URL</span><span class="sxs-lookup"><span data-stu-id="01330-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="01330-130">Tous les éléments de la section « liens connexes » en bas de la page doivent contenir des liens hypertexte.</span><span class="sxs-lookup"><span data-stu-id="01330-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="01330-131">Sauts de ligne</span><span class="sxs-lookup"><span data-stu-id="01330-131">Line breaks</span></span>

* <span data-ttu-id="01330-132">Vous devez inclure des sauts de ligne sémantiques</span><span class="sxs-lookup"><span data-stu-id="01330-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="01330-133">Vous devez limiter les lignes à 100 caractères (élément ouvert : outils pour nous aider à valider ceci)</span><span class="sxs-lookup"><span data-stu-id="01330-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="01330-134">Vous POUVEZ supprimer les sauts de ligne supplémentaires pour PS4+, mais PAS pour ps3 (validation nécessaire)</span><span class="sxs-lookup"><span data-stu-id="01330-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
