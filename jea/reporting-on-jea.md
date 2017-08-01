---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "création de rapports sur JEA"
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="reporting-on-jea"></a><span data-ttu-id="e2ee5-103">Création de rapports sur JEA</span><span class="sxs-lookup"><span data-stu-id="e2ee5-103">Reporting on JEA</span></span>
<span data-ttu-id="e2ee5-104">Étant donné que JEA permet à des utilisateurs non privilégiés de s’exécuter dans un contexte privilégié, la journalisation et l’audit sont extrêmement importants.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="e2ee5-105">Dans cette section, nous allons passer en revue les outils que vous pouvez utiliser pour la journalisation et la création de rapports.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="e2ee5-106">Création de rapports sur les actions JEA</span><span class="sxs-lookup"><span data-stu-id="e2ee5-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="e2ee5-107">Transcription de procuration de privilège</span><span class="sxs-lookup"><span data-stu-id="e2ee5-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="e2ee5-108">Un des moyens les plus rapides d’obtenir un résumé de ce qui se passe au cours d’une session PowerShell consiste à observer une personne qui tape au clavier.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="e2ee5-109">Vous voyez ses commandes, la sortie de ces commandes et tout va bien.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="e2ee5-110">Ou pas, mais au moins vous savez.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="e2ee5-111">La transcription PowerShell a pour but de vous donner un aperçu similaire après coup.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="e2ee5-112">Quand vous utilisez le champ « TranscriptDirectory » dans votre configuration de session, PowerShell enregistre automatiquement une transcription de toutes les actions effectuées au cours d’une session donnée.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="e2ee5-113">Vous pouvez trouver des transcriptions de vos sessions dans ce document : « $env:ProgramData\JEAConfiguration\Transcripts ».</span><span class="sxs-lookup"><span data-stu-id="e2ee5-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="e2ee5-114">Comme vous pouvez le voir, la transcription enregistre des informations sur l’utilisateur « connecté », l’utilisateur « du compte d’identification », les commandes exécutées pendant la session et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="e2ee5-115">Pour plus d’informations sur la transcription PowerShell, consultez [ce billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="e2ee5-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="e2ee5-116">Journaux des événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2ee5-116">PowerShell Event Logs</span></span>
<span data-ttu-id="e2ee5-117">Quand l’enregistrement des modules est activé, toutes les actions PowerShell sont également enregistrées dans les journaux des événements Windows standard.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="e2ee5-118">Ces journaux sont un peu plus délicats à gérer par rapport aux transcriptions, mais le niveau de détail qu’ils donnent peut vous être utile.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="e2ee5-119">Dans le journal des opérations « PowerShell », l’ID d’événement 4104 enregistre chaque commande appelée si vous avez activé l’enregistrement des modules.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="e2ee5-120">Autres journaux des événements</span><span class="sxs-lookup"><span data-stu-id="e2ee5-120">Other Event Logs</span></span>
<span data-ttu-id="e2ee5-121">Contrairement aux journaux et transcriptions PowerShell, les autres mécanismes de journalisation ne capturent pas « l’utilisateur connecté ».</span><span class="sxs-lookup"><span data-stu-id="e2ee5-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="e2ee5-122">Vous devrez effectuer une corrélation entre les autres journaux et les journaux PowerShell pour faire correspondre les actions effectuées.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="e2ee5-123">Dans le journal des opérations « Windows Remote Management », l’ID d’événement 193 enregistre le SID et le nom de l’utilisateur, ainsi que le SID du compte virtuel d’identification pour faciliter cette corrélation.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="e2ee5-124">Vous avez peut-être également remarqué que le nom du compte virtuel d’identification inclut à la fin le domaine et le nom de l’utilisateur qui tente d’établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="e2ee5-125">Création de rapports sur la configuration JEA</span><span class="sxs-lookup"><span data-stu-id="e2ee5-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="e2ee5-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e2ee5-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="e2ee5-127">Pour créer des rapports précis sur l’état de votre environnement, il est important de connaître le nombre de points de terminaison JEA que vous avez configurés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="e2ee5-128">`Get-PSSessionConfiguration` permet exactement de le déterminer.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="e2ee5-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="e2ee5-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="e2ee5-130">Créer manuellement des rapports sur les capacités d’un utilisateur donné par le biais d’un point de terminaison JEA peut s’avérer assez complexe.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="e2ee5-131">Vous devez probablement inspecter plusieurs capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="e2ee5-132">Heureusement, l’applet de commande « Get-PSSessionCapability » permet de le faire.</span><span class="sxs-lookup"><span data-stu-id="e2ee5-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="e2ee5-133">Pour tester, exécutez la commande suivante à partir d’une invite PowerShell d’administrateur :</span><span class="sxs-lookup"><span data-stu-id="e2ee5-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

