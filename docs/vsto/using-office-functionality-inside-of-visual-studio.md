---
title: Utilizzare la funzionalità di Office in Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a1db785b4758236c4a50e694d868cecc269324a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767507"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Utilizzare la funzionalità di Office in Visual Studio
  Quando si crea un progetto a livello di documento, il documento e l'applicazione associata sono ospitati all'interno di Visual Studio in modo sia possibile progettare e lavorare direttamente con il documento. Quando si dispone di un'applicazione aperta in Visual Studio di Microsoft Office, in genere funziona come previsto. Tuttavia, alcune delle funzionalità dell'applicazione è diverso o non è accessibile.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Protezione di documenti  
 Microsoft Office Word e Microsoft Office Excel offrono le funzionalità di protezione che è possibile utilizzare nei progetti di documento. Tuttavia, se è attivata la sicurezza, mentre il documento è aperto in Visual Studio, è possibile impedire è apportare alcune modifiche di progettazione. Per altre informazioni, vedere [protezione nelle soluzioni a livello di documento di documenti](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Servizio Information rights management  
 Information Rights Management (IRM) è disponibile in Microsoft Office Word e Microsoft Office Excel. IRM consentono di evitare che utenti non autorizzati di visualizzare o modificare le informazioni riservate. Tuttavia, IRM può inoltre impedire al codice in esecuzione. Per altre informazioni, vedere [Information rights management e Cenni preliminari sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Protezione con password  
 Documenti di Microsoft Office Word e cartelle di lavoro di Microsoft Office Excel può essere impostati in modo che non può essere aperto da un utente che non conoscono la password. Password di protezione è gestita in modo diverso in Word ed Excel e può influire sul processo di sviluppo. Per altre informazioni, vedere [protezione con Password nei documenti di Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management e Cenni preliminari sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protezione con password nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: soluzioni di Office aperte senza eseguire il codice](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  