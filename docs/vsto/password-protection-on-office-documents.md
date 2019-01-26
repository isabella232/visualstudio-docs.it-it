---
title: Password di protezione nei documenti di Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 062196206d881ebb5a10f4bd7b14d892dbbbe0e9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872208"
---
# <a name="password-protection-on-office-documents"></a>Password di protezione nei documenti di Office
  È possibile impostare una password per i documenti di Microsoft Office Word e cartelle di lavoro di Microsoft Office Excel in modo che non può essere aperto da chi non conosce la password. Questa opzione, detta **Password all'apertura**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile creare progetti a livello di documento con i documenti esistenti e le cartelle di lavoro che hanno **Password all'apertura** abilitata. Il comportamento in Visual Studio è diverso per i documenti di Word ed Excel che hanno **Password all'apertura** abilitata.  
  
 Per informazioni sull'abilitazione **Password all'apertura**, vedere la Guida di Word o Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamento di Excel e Word  
 Ogni volta che si apre una cartella di lavoro di Excel in Visual Studio dotato **Password all'apertura** abilitata, viene richiesta la password. Quando si compila la soluzione richiederà la password anche in questo caso, poiché il documento viene aperto durante la compilazione.  
  
 La prima volta che si apre un documento di Word in Visual Studio dotato **Password all'apertura** abilitata, viene richiesta la password. Dopo aver immesso correttamente la password **Password all'apertura** viene rimosso dal documento e apertura del documento non è più necessaria una password. Se si desidera che il documento nella soluzione per richiedere una password prima che può essere aperto, è necessario abilitare **Password all'apertura** dopo la compilazione finale e prima di distribuire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management e panoramica sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Procedura: Consentire l'esecuzione dietro i documenti con autorizzazioni limitate codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
