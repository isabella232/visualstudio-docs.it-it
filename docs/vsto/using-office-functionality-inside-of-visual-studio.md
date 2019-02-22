---
title: Usare funzionalità Office in Visual Studio
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
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628663"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usare funzionalità Office in Visual Studio
  Quando si crea un progetto a livello di documento, documento e l'applicazione associato sono ospitati all'interno di Visual Studio in modo che sia possibile progettare e modificare direttamente il documento. Quando si dispone di un'applicazione aperta in Visual Studio di Microsoft Office, in genere funzioni come previsto. Tuttavia, alcune delle funzionalità dell'applicazione è diversa o non accessibile.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protezione di documenti
 Microsoft Office Word e Microsoft Office Excel offrono le funzionalità di protezione che è possibile usare nei progetti di documento. Ma, se è abilitata la protezione del documento mentre il documento è aperto in Visual Studio, può impedire di apportare alcune modifiche di progettazione. Per altre informazioni, vedere [documentare la protezione nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Servizio Information rights management
 Information Rights Management (IRM) è disponibile in Microsoft Office Word e Microsoft Office Excel. IRM contribuisce a impedire agli utenti non autorizzati di visualizzare o modificare le informazioni riservate. Tuttavia, IRM può inoltre impedire il codice in esecuzione. Per altre informazioni, vedere [Information rights management e panoramica sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Protezione con password
 Documenti di Microsoft Office Word e cartelle di lavoro di Microsoft Office Excel possono essere impostati in modo che non può essere aperto da chi non conosce la password. La protezione con password viene gestita in modo diverso in Word ed Excel e può influire sul processo di sviluppo. Per altre informazioni, vedere [Password di protezione nei documenti di Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Vedere anche
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Information rights management e panoramica sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Password di protezione nei documenti di Office](../vsto/password-protection-on-office-documents.md)
- [Procedura: Aprire soluzioni Office senza eseguire codice](../vsto/how-to-open-office-solutions-without-running-code.md)
