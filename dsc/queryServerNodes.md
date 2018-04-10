---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Fonction DSC pour demander des informations sur le nœud au serveur collecteur.
ms.openlocfilehash: 5c10eefe9ded4fe6339c4e6252cc189bcd793978
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="c378d-103">Fonction DSC pour demander des informations sur le nœud au serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c378d-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="c378d-104">Remplacez le paramètre `Uri` par l’URI de votre serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="c378d-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="c378d-105">Si vous voulez les informations de nœud au format XML, définissez `ContentType` avec la valeur `application/xml`.</span><span class="sxs-lookup"><span data-stu-id="c378d-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="c378d-106">Pour récupérer les informations de nœud à partir du paramètre `$json`, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c378d-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```