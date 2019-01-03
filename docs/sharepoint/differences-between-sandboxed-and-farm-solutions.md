---
title: Differenze tra modalità sandbox e soluzioni Farm | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4f37d908448eba54924589cd669dbdda84956d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849745"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Differenze tra modalità sandbox e soluzioni farm
  Quando si compila una soluzione di SharePoint, viene distribuito nel server SharePoint e un debugger viene collegato per eseguirne il debug. Il processo usato per il debug della soluzione dipende dall'impostazione della proprietà soluzione creata mediante sandbox: soluzione creata mediante sandbox o una soluzione farm.  
  
 Per altre informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluzioni farm
 Soluzioni farm, che sono ospitate nel processo di lavoro IIS (W3WP.exe), eseguire il codice che può interessare l'intera farm. Quando si esegue il debug di un progetto SharePoint la cui proprietà soluzione creata mediante sandbox è impostata su "la soluzione farm", viene riciclato il pool di applicazioni IIS del sistema prima di SharePoint viene ritratta o distribuisce la funzionalità in modo da rilasciare tutti i file bloccati dal processo di lavoro IIS. Solo il pool di applicazioni IIS che servono URL del sito del progetto SharePoint viene riciclato.  
  
## <a name="sandboxed-solutions"></a>Soluzioni create mediante sandbox
 Soluzioni create mediante sandbox, che sono ospitate nel processo di lavoro soluzione con codice di utente SharePoint (SPUCWorkerProcess.exe), eseguire il codice che può interessare solo la raccolta di siti della soluzione. Poiché soluzioni create mediante sandbox non vengono eseguiti nel processo di lavoro IIS, è necessario riavviare il pool di applicazioni IIS, né il server IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Collega il debugger al processo SPUCWorkerProcess che il servizio SPUserCodeV4 in SharePoint e ai controlli. Non è necessario che il processo SPUCWorkerProcess riciclo per caricare la versione più recente della soluzione.  
  
## <a name="either-type-of-solution"></a>Entrambi i tipi di soluzione
 Con gli altri tipi di soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anche il debugger viene connesso al browser per abilitare il debug di script sul lato client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il motore a questo scopo di debug degli script. Per abilitare il debug degli script, è necessario modificare le impostazioni del browser predefinito quando viene richiesto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Collega il debugger solo per i processi di W3WP o SPUCWorkerProcess in esecuzione il sito corrente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] associa inoltre componenti gestiti COM Plus e flusso di lavoro di motori di debug.  
  
## <a name="see-also"></a>Vedere anche
 [Il debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilare ed eseguire il debug di soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md)  
