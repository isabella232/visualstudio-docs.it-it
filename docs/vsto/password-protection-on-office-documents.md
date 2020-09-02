---
title: Protezione delle password nei documenti di Office
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
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977900"
---
# <a name="password-protection-on-office-documents"></a>Protezione delle password nei documenti di Office
  È possibile impostare una password nei documenti Microsoft Office Word e Microsoft Office cartelle di lavoro di Excel in modo che non possano essere aperte da un utente che non conosce la password. Questa opzione è denominata **password all'apertura**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile creare progetti a livello di documento usando documenti e cartelle di lavoro esistenti per i quali è abilitata la **password per l'apertura** . Il comportamento in Visual Studio è diverso per i documenti di Word ed Excel per i quali è abilitata la **password per l'apertura** .

 Per informazioni sull'abilitazione della **password all'apertura**, vedere la Guida in Word o Excel.

## <a name="behavior-of-excel-and-word"></a>Comportamento di Excel e Word
 Ogni volta che si apre una cartella di lavoro di Excel in Visual Studio in cui è abilitata la **password in Open** , in Excel viene richiesta la password. Quando si compila la soluzione, verrà richiesta di nuovo la password, perché il documento viene aperto durante la compilazione.

 La prima volta che si apre un documento di Word in Visual Studio con la password abilitata per l' **apertura** , Word richiede la password. Dopo aver immesso correttamente la password, la **password all'apertura** verrà rimossa dal documento e l'apertura del documento non richiederà più una password. Se si vuole che il documento nella soluzione richieda una password prima di poterla aprire, è necessario abilitare la **password all'apertura** dopo la compilazione finale e prima di distribuire la soluzione.

## <a name="see-also"></a>Vedere anche
- [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Procedura: consentire l'esecuzione del codice dietro i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
