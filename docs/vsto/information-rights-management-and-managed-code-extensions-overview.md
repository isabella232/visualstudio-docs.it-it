---
title: Information rights management e panoramica sulle estensioni di codice gestito
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a2020221ee086b23a8621112122acffb11beef62
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823830"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Information rights management e panoramica sulle estensioni di codice gestito
  Microsoft Office Word e Microsoft Office Excel forniscono Information Rights Management (IRM), una funzionalità che contribuisce di evitare che utenti non autorizzati di visualizzare o modificare le informazioni riservate. Per informazioni dettagliate sul funzionamento di Information Rights Management, vedere la Guida nell'applicazione di Office specifiche.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Eseguire il codice sottostante i documenti con autorizzazioni limitate  
 Se la soluzione contiene un documento o cartella di lavoro che utilizza il servizio IRM, per impostazione predefinita, Word ed Excel che consentono di eseguire qualsiasi codice. Se l'autore del documento o di accesso con controllo completo, è possibile modificare il valore predefinito in modo che la soluzione funzioni. Per altre informazioni, vedere [Procedura: Consentire l'esecuzione dietro i documenti con autorizzazioni limitate codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 Impedisce l'uso di IRM <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> da recuperare o modificare i dati memorizzati nella cache del documento.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Agli utenti finali di limitare le autorizzazioni per documenti che usano le estensioni di codice gestito  
 Chiunque abbia accesso controllo completo per il documento o la cartella di lavoro della soluzione può usare IRM per limitare le autorizzazioni. Ad esempio, se un utente finale nel reparto contabilità Usa una soluzione che popola automaticamente un foglio di lavoro con i dati da un database, che l'utente potrebbe essere necessario consentire la modifica accesso solo agli utenti del proprio reparto e accesso in lettura ad altri utenti. Quando l'utente aggiunge le autorizzazioni limitate, per impostazione predefinita, non è possibile eseguire il code-behind del foglio di lavoro e il foglio di lavoro non viene popolato con i dati.  
  
 Per risolvere il problema, un utente con accesso con controllo completo al documento o cartella di lavoro è necessario modificare le impostazioni di autorizzazione predefiniti per consentire l'accesso a livello di codice per il modello a oggetti. Per altre informazioni, vedere [Procedura: Consentire l'esecuzione dietro i documenti con autorizzazioni limitate codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Password di protezione nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
