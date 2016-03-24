# Mises à jour de l’objet FileInfo
Les informations de version peuvent prêter à confusion, notamment dans les cas où le fichier a été corrigé. Cette version de WMF Production Preview ajoute de nouvelles propriétés de script **FileVersionRaw** et **ProductVersionRaw** aux objets FileInfo. Voici les propriétés telles qu’elles sont affichées pour powershell.exe :

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
