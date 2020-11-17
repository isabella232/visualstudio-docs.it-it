---
title: Differenze tra soluzioni create mediante sandbox e farm | Microsoft Docs
description: Comprendere le differenze tra le soluzioni in modalità sandbox e farm. Scopri in che modo Visual Studio si avvicina al debug con entrambi i tipi di soluzione.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25c1c9047ba9e38e3e652abcbe92ce6575d7b750
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672782"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Differenze tra soluzioni create mediante sandbox e farm
  Quando si compila una soluzione SharePoint, questa viene distribuita nel server SharePoint e un debugger si connette per eseguirne il debug. Il processo usato per eseguire il debug della soluzione dipende dall'impostazione della proprietà della soluzione creata mediante sandbox, ovvero dalla soluzione sandbox o dalla soluzione farm.

 Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Soluzioni farm
 Le soluzioni farm, ospitate nel processo di lavoro IIS (W3WP.exe), eseguono codice che può interessare l'intera farm. Quando si esegue il debug di un progetto SharePoint la cui proprietà della soluzione sandbox è impostata su "soluzione farm", il pool di applicazioni IIS del sistema viene riciclato prima che SharePoint ritragga o distribuisce la funzionalità per rilasciare i file bloccati dal processo di lavoro IIS. Solo il pool di applicazioni IIS che serve l'URL del sito del progetto SharePoint viene riciclato.

## <a name="sandboxed-solutions"></a>Soluzioni create mediante sandbox
 Le soluzioni in modalità sandbox, ospitate nel processo di lavoro della soluzione del codice utente di SharePoint (SPUCWorkerProcess.exe), eseguono codice che può influire solo sulla raccolta siti della soluzione. Poiché le soluzioni create mediante sandbox non vengono eseguite nel processo di lavoro IIS, non è necessario riavviare il pool di applicazioni IIS né il server IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette il debugger al processo SPUCWorkerProcess che il servizio SPUserCodeV4 in SharePoint attiva e controlla automaticamente. Non è necessario che il processo SPUCWorkerProcess venga riciclato per caricare la versione più recente della soluzione.

## <a name="either-type-of-solution"></a>Entrambi i tipi di soluzione
 Con entrambi i tipi di soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il debugger viene collegato al browser per abilitare il debug di script sul lato client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il motore di debug di script a questo scopo. Per abilitare il debug degli script, è necessario modificare le impostazioni del browser predefinite quando richiesto.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette il debugger solo ai processi W3WP o SPUCWorkerProcess che eseguono il sito corrente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette inoltre i motori di debug COM Plus e Workflow gestiti.

## <a name="see-also"></a>Vedere anche
- [Debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Considerazioni sulla soluzione sandbox](../sharepoint/sandboxed-solution-considerations.md)
