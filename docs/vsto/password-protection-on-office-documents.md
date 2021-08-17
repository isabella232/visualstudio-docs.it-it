---
title: Protezione della password nei Office dati
description: Informazioni su come impostare una password nei documenti Microsoft Word e nelle cartelle di lavoro Excel in modo che non possano essere aperte da utenti non autorizzati.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 80e89d5907fca8d4896ba0349bf26b527c11b1cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099607"
---
# <a name="password-protection-on-office-documents"></a>Protezione della password nei Office dati
  È possibile impostare una password per i documenti di Microsoft Office Word e le cartelle di lavoro di Microsoft Office Excel in modo che non siano aperte da un utente che non conosce la password. Questa opzione è denominata **Password all'apertura** di .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile creare progetti a livello di documento usando documenti e cartelle di lavoro esistenti per cui è **abilitata l'opzione Password all'apertura.** Il comportamento in Visual Studio è diverso per i documenti di Word e Excel in cui è abilitata l'opzione **Password all'apertura.**

 Per informazioni **sull'abilitazione della password all'apertura** di , vedere La Guida in Word o Excel.

## <a name="behavior-of-excel-and-word"></a>Comportamento di Excel e Word
 Ogni volta che si apre Excel cartella di lavoro di Visual Studio in cui è abilitata l'opzione **Password** all'apertura, Excel richiede la password. Quando si compila la soluzione, verrà richiesta nuovamente la password, perché il documento viene aperto durante la compilazione.

 La prima volta che si apre un documento di Word in Visual Studio in cui è abilitata l'opzione **Password** all'apertura, Word richiede la password. Dopo aver immesso correttamente la password, **la password** all'apertura viene rimossa dal documento e l'apertura del documento non richiederà più una password. Se si vuole che il documento nella soluzione richieda una password prima di poterlo aprire, è necessario abilitare **Password** all'apertura dopo la compilazione finale e prima di distribuire la soluzione.

## <a name="see-also"></a>Vedi anche
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Procedura: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
