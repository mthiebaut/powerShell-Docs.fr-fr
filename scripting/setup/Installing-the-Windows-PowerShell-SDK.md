---
title:  Installation du SDK Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c3636b45-61aa-4720-85f0-58312c4fc8f9
---

# Installation du SDK Windows PowerShell
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.</para>
  </introduction>
  <section>
    <title>Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012</title>
    <content>
      <para>Windows PowerShell 3.0 est installé automatiquement avec Windows 8 et Windows Server 2012. De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8. Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0. Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont automatiquement installés dans le dossier d’assemblys de référence, dans \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Pour plus d’informations, consultez le <externalLink><linkText>site de téléchargement du SDK Windows 8</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>. Des exemples de code Windows PowerShell sont aussi disponibles dans le Centre de développement. Pour plus d’informations, consultez la page d’exemples de code Windows Desktop sur le <externalLink><linkText>site Centre de développement</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>. </para>
      <para>Par ailleurs, Windows PowerShell 3.0 est rétrocompatible avec le SDK Windows PowerShell 2.0 qui comprend un certain nombre d’exemples de code. Pour plus d’informations sur la façon de télécharger le SDK Windows PowerShell 2.0, voir ci-dessous. (Même si les exemples de code 2.0 sont compatibles avec Windows 8 et Windows PowerShell 3.0, notez que vous ne pouvez pas installer Windows PowerShell 2.0 sur une plateforme Windows 8.) </para>
    </content>
  </section>
  <section>
    <title>Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2</title>
    <content>
      <para>PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows PowerShell 2008 R2. Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes. (Pour plus d’informations, consultez <link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">Installing Windows PowerShell</link> (Installation de Windows PowerShell.). Comme indiqué plus haut, vous pouvez aussi installer le SDK Windows 8 sur Windows 7 et Windows Server 2008 R2.</para>
    </content>
  </section>
  <section>
    <title>Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008</title>
    <content>
      <para>Le SDK <token>mshshort</token> 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code. </para>
      <para>Pour installer ce SDK, consultez <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section>
        <title>Assemblys de référence</title>
        <content>
          <para>Par défaut, les assemblys de référence sont installés à l’emplacement suivant : <codeInline>c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>.</para>
          <alert class="note">
            <para>Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0. En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Exemples</title>
        <content>
          <para>Par défaut, des exemples de code sont installés à l’emplacement suivant : <codeInline>C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>.</para>
          <para>Les sections suivantes proposent une brève description de la fonction de chaque exemple.</para>
        </content>
        <sections>
          <section>
            <title>Exemples d’applets de commande</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>Montre comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>Montre comment ajouter des paramètres à l’applet de commande. L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>Montre comment ajouter des paramètres qui acceptent les entrées du pipeline.</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>Montre comment gérer les erreurs sans fin d’exécution.</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>Montre comment afficher une liste de processus spécifiés.</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>Montre comment écrire un filtre pour sélectionner uniquement certains objets. </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>Montre comment rechercher des modèles spécifiés dans des fichiers.</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>Montre comment implémenter un paramètre <parameterReference>PassThru</parameterReference> et comment demander des commentaires utilisateur en appelant les méthodes <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> et <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference>. Les utilisateurs spécifient le paramètre <parameterReference>PassThru</parameterReference> quand ils veulent forcer l’applet de commande à retourner un objet, </para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>Montre comment arrêter un processus spécifique.</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>Montre comment déclarer des alias de paramètres et comment prendre en charge les caractères génériques.</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>Montre comment déclarer des jeux de paramètres, l’objet que prend l’applet de commande comme entrée et comment spécifier le jeu de paramètres à utiliser par défaut.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemples de communication à distance</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>Montre comment créer une instance d’exécution à distance servant à établir une connexion à distance.</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>Montre comment construire un pool d’instances d’exécution à distance et comment exécuter plusieurs commandes simultanément en utilisant ce pool.</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>Montre comment examiner une classe .NET existante et vérifier que les informations tirées des propriétés publiques sélectionnées de cette classe sont conservées à l’issue de la sérialisation/désérialisation.</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>Montre comment examiner une classe .NET existante et vérifier que les informations tirées de l’instance de cette classe sont conservées à l’issue de la sérialisation/désérialisation quand les informations ne sont pas disponibles dans les propriétés publiques de la classe.</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>Montre comment examiner une classe .NET existante et vérifier que les instances de cette classe et des classes dérivées sont désérialisées (réactivées) en objets .NET dynamiques.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemples d’événements</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>Montre comment créer une applet de commande pour l’inscription d’événements en la faisant dériver de la classe ObjectEventRegistrationBase.</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>Montre comment recevoir des notifications d’événements <token>mshshort</token> générés sur des ordinateurs distants. Il utilise l’événement PSEventReceived exposé via la classe <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemples d’applications d’hébergement</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>Montre comment utiliser la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> pour exécuter l’applet de commande <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> de façon synchrone. L’applet de commande <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> retourne des objets <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> pour chaque processus s’exécutant sur l’ordinateur local.</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>Montre comment utiliser la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> pour exécuter les applets de commande <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> et <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> de façon synchrone. L’applet de commande <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> retourne des objets <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> pour chaque processus s’exécutant sur l’ordinateur local, tandis que Sort-Object trie les objets en fonction de leur propriété <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference>. Le résultat de ces commandes s’affiche au moyen d’un contrôle <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>Montre comment utiliser la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution. Le script reçoit une liste de noms de processus et récupère ensuite ces processus. Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>Montre comment utiliser la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> pour exécuter des commandes et comment intercepter les erreurs avec fin d’exécution qui sont levées pendant l’exécution des commandes. Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide. En conséquence, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>Montre comment ajouter un composant logiciel enfichable à un objet <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> de telle sorte que l’applet de commande du composant logiciel enfichable soit disponible quand l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par l’<legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">exemple GetProcessSample01</legacyLink>) qui est exécutée de façon synchrone à l’aide d’un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>Montre comment ajouter un module à un objet <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> de telle sorte que le module soit chargé quand l’instance d’exécution est ouverte. Le module fournit une applet de commande Get-Process (définie par l’<legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">exemple GetProcessSample02</legacyLink>) qui est exécuté de façon synchrone en utilisant un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>Montre comment créer une instance d’exécution et s’en servir pour exécuter deux applets de commande de façon synchrone en utilisant un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>Montre comment ajouter des commandes et des arguments au pipeline d’un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> et comment exécuter les commandes de façon synchrone.</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>Montre comment ajouter un script au pipeline d’un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> et comment exécuter le script de façon asynchrone. Des événements sont utilisés pour gérer la sortie du script.</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>Montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>, comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande en utilisant un objet <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>Montre comment utiliser la classe <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> pour créer une commande proxy qui appelle une applet de commande existante, mais qui limite le jeu de paramètres disponibles. La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte. Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>Montre comment créer une instance d’exécution contrainte en utilisant un objet <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>.</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>Montre comment utiliser un pool d’instances d’exécution pour exécuter plusieurs commandes simultanément.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemples d’hôtes</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>Montre comment implémenter une application hôte qui utilise un hôte personnalisé. Dans cet exemple, l’instance d’exécution qui est créée utilise l’hôte personnalisé, puis l’API <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> est utilisée pour exécuter un script qui appelle « exit ». L’application hôte analyse ensuite la sortie du script et imprime les résultats.</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>Montre comment écrire une application hôte qui utilise le runtime <token>mshshort</token> avec une implémentation d’hôte personnalisée. L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> et affiche les résultats à l’aide de pwrsh.exe pour ensuite imprimer la date et l’heure actuelles en allemand.</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge les appels aux ordinateurs distants à l’aide des applets de commande <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> et <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink>.</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemples de fournisseurs</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>Montre comment déclarer une classe de fournisseur qui dérive directement de la classe <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference>. Il est indiqué ici uniquement par souci d’exhaustivité.</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>Montre comment remplacer les méthodes <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> et <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> pour prendre en charge les appels aux applets de commande New-PSDrive et Remove-PSDrive. La classe de fournisseur de cet exemple dérive de la classe <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>Montre comment remplacer les méthodes <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> et <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> pour prendre en charge les appels aux applets de commande Get-Item et Set-Item. La classe de fournisseur de cet exemple dérive de la classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Copy-Item, Get-ChildItem, New-Item et Remove-Item. Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur de cet exemple dérive de la classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Move-Item et Join-Path. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur de cet exemple dérive de la classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>Montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux applets de commande Clear-Content, Get-Content et Set-Content. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur de cet exemple dérive de la classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> et implémente l’interface <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>



<!--HONumber=May16_HO4-->


