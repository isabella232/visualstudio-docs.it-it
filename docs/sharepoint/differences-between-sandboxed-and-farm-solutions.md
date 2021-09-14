---
title: Differenze tra soluzioni sandbox e farm | Microsoft Docs
description: Comprendere le differenze tra soluzioni sandbox e farm. Sapere come Visual Studio il debug con entrambi i tipi di soluzione.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7f6cc328c33f4aca45833bf5fd61977cef571c58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625272"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Differenze tra soluzioni sandbox e farm
  Quando si compila una SharePoint, viene distribuita nel server SharePoint e un debugger si collega per eseguirne il debug. Il processo usato per eseguire il debug della soluzione dipende dall'impostazione della proprietà Soluzione in modalità sandbox: soluzione in modalità sandbox o soluzione farm.

 Per altre informazioni, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

## <a name="farm-solutions"></a>Soluzioni farm
 Le soluzioni farm, ospitate nel processo di lavoro IIS (W3WP.exe), eseguono codice che può influire sull'intera farm. Quando si esegue il debug di un progetto SharePoint la cui proprietà Soluzione sandbox è impostata su "soluzione farm", il pool di applicazioni IIS del sistema viene riciclato prima che SharePoint ritiri o distribuisca la funzionalità in modo da rilasciare tutti i file bloccati dal processo di lavoro IIS. Viene riciclato solo il pool di applicazioni IIS che SharePoint'URL del sito del progetto.

## <a name="sandboxed-solutions"></a>Soluzioni in modalità sandbox
 Le soluzioni in modalità sandbox, ospitate nel processo di lavoro della soluzione SharePoint codice utente (SPUCWorkerProcess.exe), eseguono codice che può influire solo sulla raccolta siti della soluzione. Poiché le soluzioni sandbox non vengono eseguite nel processo di lavoro IIS, né il pool di applicazioni IIS né il server IIS devono essere riavviati. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]collega il debugger al processo SPUCWorkerProcess che il servizio SPUserCodeV4 in SharePoint attiva e controlla automaticamente. Non è necessario che il processo SPUCWorkerProcess ricicli per caricare la versione più recente della soluzione.

## <a name="either-type-of-solution"></a>Entrambi i tipi di soluzione
 Con entrambi i tipi di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] soluzione, collega anche il debugger al browser per abilitare il debug degli script sul lato client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa il motore di debug degli script a questo scopo. Per abilitare il debug degli script, è necessario modificare le impostazioni predefinite del browser quando richiesto.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] collega il debugger solo ai processi W3WP o SPUCWorkerProcess che eseguono il sito corrente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] collega anche i motori di debug COM Plus e del flusso di lavoro gestiti.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug SharePoint soluzioni](../sharepoint/debugging-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Considerazioni sulla soluzione in modalità sandbox](../sharepoint/sandboxed-solution-considerations.md)
