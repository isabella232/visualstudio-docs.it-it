---
title: Usare le funzionalità di Office all'interno di Visual Studio
description: Informazioni sul modo in cui il documento e l'applicazione associata da un progetto a livello di documento sono ospitati all'interno di Visual Studio, in modo da poter lavorare direttamente con il documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c93994b233990e2362c62445909adb66a0eeeb9b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528402"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usare le funzionalità di Office all'interno di Visual Studio
  Quando si crea un progetto a livello di documento, il documento e l'applicazione associata sono ospitati all'interno di Visual Studio in modo da poter progettare e utilizzare direttamente il documento. Quando si dispone di un'applicazione Microsoft Office aperta in Visual Studio, in genere funziona come previsto. Tuttavia, alcune delle funzionalità dell'applicazione sono diverse o inaccessibili.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protezione di documenti
 Microsoft Office Word e Microsoft Office Excel offrono funzionalità di protezione dei documenti che è possibile usare nei progetti. Tuttavia, se la protezione dei documenti è abilitata mentre il documento è aperto in Visual Studio, può impedire di apportare alcune modifiche alla progettazione. Per altre informazioni, vedere [protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Information Rights Management
 Information Rights Management (IRM) è disponibile in Microsoft Office Word e Microsoft Office Excel. IRM consente di impedire a utenti non autorizzati di visualizzare o modificare le informazioni riservate. Tuttavia, IRM può anche impedire l'esecuzione del codice. Per ulteriori informazioni, vedere la [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Password di protezione
 È possibile impostare Microsoft Office documenti di Word e Microsoft Office cartelle di lavoro di Excel in modo che non possano essere aperti da un utente che non conosce la password. La protezione con password viene gestita in modo diverso in Word ed Excel e può influire sul processo di sviluppo. Per ulteriori informazioni, vedere la pagina [relativa alla protezione delle password nei documenti di Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Vedere anche
- [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione delle password nei documenti di Office](../vsto/password-protection-on-office-documents.md)
- [Procedura: aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md)
