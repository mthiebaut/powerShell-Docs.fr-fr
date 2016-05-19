---
title: Préparation à l’utilisation de Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
---
# Préparation à l’utilisation de Windows PowerShell
Une fois Windows PowerShell installé et démarré, envisagez les options de configuration suivantes. Vous pouvez effectuer ces tâches à tout moment.

-   **Installez les fichiers d’aide.** Les applets de commande incluses dans Windows PowerShell 3.0 ne sont pas fournies avec des fichiers d’aide. En revanche, vous pouvez utiliser l’applet de commande [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) pour télécharger et installer les fichiers d’aide les plus récents sur votre ordinateur. Lorsque les fichiers sont installés, vous pouvez utiliser l’applet de commande [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) pour les afficher sur la ligne de commande. Pour plus d’informations, voir [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe)..

    Si vous décidez de ne pas installer les fichiers d’aide, vous pouvez toujours lire les rubriques d’aide en ligne. Pour trouver la version en ligne de la rubrique d’aide relative à une applet de commande, tapez : `Get-Help <CmdletName> -Online`. Pour parcourir les rubriques d’aide de Windows PowerShell dans la bibliothèque TechNet, commencez par accéder à la page [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116)..

-   **Exécutez les scripts.** Pour sécuriser Windows PowerShell, la stratégie d’exécution par défaut de Windows PowerShell est **Restricted**. Cette stratégie permet d’exécuter des applets de commande, mais pas des scripts. Pour exécuter des scripts, utilisez l’applet de commande [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) afin de modifier la stratégie d’exécution en la définissant sur **AllSigned** ou **RemoteSigned**. Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent exécuter cette applet de commande. Pour plus d’informations, consultez [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6)..

-   **Activez la communication à distance.** Le système est déjà configuré pour exécuter des commandes à distance sur d’autres ordinateurs. Sur Windows Server 2012 R2 et Windows Server 2012, le système est également configuré pour recevoir des commandes à distance, c’est-à-dire pour permettre à d’autres ordinateurs d’exécuter des commandes à distance sur l’ordinateur local. Pour permettre à des ordinateurs exécutant d’autres versions de Windows de recevoir des commandes à distance, exécutez l’applet de commande [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) sur l’ordinateur que vous souhaitez gérer à distance. Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent exécuter cette applet de commande. Pour plus d’informations, consultez [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)..

    REMARQUE : Si la communication à distance est activée sur un ordinateur exécutant Windows PowerShell 2.0, la communication à distance reste activée après l’installation de Windows Management Framework 3.0. Toutefois, sur Windows Server 2008 (pas sur Windows Server 2008 R2), vous devez réactiver la communication à distance après l’installation de Windows Management Framework 3.0.

## Voir aussi
[Installation de Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
[Démarrage de Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


