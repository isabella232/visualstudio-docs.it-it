---
title: Usare Office funzionalità all'interno di Visual Studio
description: Informazioni su come il documento e l'applicazione associata da un progetto a livello di documento sono ospitati all'interno di Visual Studio in modo da poter lavorare direttamente con il documento.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1e08f5a0189b50ee37c240ad32556e4efd7d3fa00c759f37e54cf5d9e73de368
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226050"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usare Office funzionalità all'interno di Visual Studio
  Quando si crea un progetto a livello di documento, il documento e l'applicazione associata sono ospitati all'interno di Visual Studio in modo da poter progettare e lavorare direttamente con il documento. Quando un'applicazione Microsoft Office aperta in Visual Studio, funziona in genere come previsto. Tuttavia, alcune delle funzionalità dell'applicazione sono diverse o inaccessibili.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protezione dei documenti
 Microsoft Office Word e Microsoft Office Excel offrono funzionalità di protezione dei documenti che è possibile usare nei progetti. Tuttavia, se la protezione dei documenti è abilitata mentre il documento è aperto in Visual Studio, può impedire di apportare alcune modifiche di progettazione. Per altre informazioni, vedere [Protezione dei documenti nelle soluzioni a livello di documento.](../vsto/document-protection-in-document-level-solutions.md)

## <a name="information-rights-management"></a>Information Rights Management
 Information Rights Management (IRM) è disponibile in Microsoft Office Word e Microsoft Office Excel. IRM consente di impedire a utenti non autorizzati di visualizzare o modificare informazioni riservate. Tuttavia, IRM può anche impedire l'esecuzione del codice. Per altre informazioni, vedere [Panoramica di Information Rights Management e delle estensioni di codice gestito.](../vsto/information-rights-management-and-managed-code-extensions-overview.md)

## <a name="password-protection"></a>Password di protezione
 Microsoft Office I documenti di Word Microsoft Office Excel cartelle di lavoro possono essere impostate in modo che non possano essere aperte da un utente che non conosce la password. La protezione con password viene gestita in modo diverso in Word e Excel e può influire sul processo di sviluppo. Per altre informazioni, vedere [Password protection on Office documents](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Vedi anche
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione con password per Office documenti](../vsto/password-protection-on-office-documents.md)
- [Procedura: Aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md)
