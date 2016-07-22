---
title: "Inscriptions du serveur collecteur améliorées"
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## Inscription du serveur collecteur améliorée ##

Dans les versions antérieures de WMF, les inscriptions/demandes de création de rapports simultanées auprès d’un serveur collecteur DSC lors de l’utilisation de la base de données ESENT aboutissaient à un échec d’inscription/de création de rapport du LCM selon le cas. Dans ce cas, les journaux des événements sur le serveur collecteur affichent l’erreur « Le nom d’instance est déjà utilisé ».
Cela est dû à l’utilisation d’un modèle incorrect pour accéder à la base de données ESENT dans un scénario multithread. Dans WMF 5.1, ce problème a été résolu. Les inscriptions ou demandes de création de rapports simultanées (impliquant la base de données ESENT) fonctionnent correctement dans WMF 5.1. Ce problème s’applique uniquement à la base de données ESENT et ne s’applique pas à la base de données OLE DB. 



<!--HONumber=Jul16_HO3-->


