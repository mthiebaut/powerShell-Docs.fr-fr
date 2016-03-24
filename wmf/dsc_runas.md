# Prise en charge automatique de RunAs pour les ressources DSC
Prise en charge des informations d’identification DSC RunAs
--------------------------------

La version WMF 5.0 Preview d’avril 2015 inclut la prise en charge de l’exécution de **n’importe quelle** ressource DSC sous un jeu d’informations d’identification spécifié à l’aide de la propriété PsDscRunAsCredential. Cela autorise des scénarios tels que l’installation de packages MSI dans un contexte utilisateur spécifique, l’accès à la ruche du Registre d’un utilisateur, l’accès au répertoire local spécifique d’un utilisateur, l’accès à un partage réseau, et ainsi de suite.

Voici un exemple d’utilisation de la propriété PsDscRunAsCredential dans DSC pour modifier la couleur d’arrière-plan de l’invite de commandes d’un utilisateur.

Configuration ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## Problèmes connus

Voici une liste des problèmes connus avec la fonctionnalité d’informations d’identification DSC RunAs dans cette version :

-   La ressource WindowsProcess ne prend pas en charge les informations d’identification RunAs.

<!--HONumber=Mar16_HO2-->
