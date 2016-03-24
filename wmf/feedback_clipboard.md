# Applets de commande de Presse-papiers
**Get-Clipboard** et **Set-Clipboard** simplifient le transfert de contenu vers et à partir d’une session Windows PowerShell. L’exemple suivant utilise l’Explorateur de fichiers pour copier trois fichiers :

Désormais, vous pouvez accéder facilement au contenu du Presse-papiers sous forme de liste de fichiers :

PS C:\\&gt; Get-Clipboard -Format FileDropList

Répertoire : C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt

Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.
<!--HONumber=Mar16_HO2-->
