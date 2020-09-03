---
title: Information Rights Management & estensioni di codice gestito
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68872055"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Panoramica di Information Rights Management e delle estensioni di codice gestito
  Microsoft Office Word e Microsoft Office Excel forniscono informazioni Rights Management (IRM), una funzionalità che consente di impedire a utenti non autorizzati di visualizzare o modificare le informazioni riservate. Per informazioni dettagliate sul funzionamento delle informazioni Rights Management, vedere la guida nell'applicazione di Office specifica.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Eseguire codice dietro documenti con autorizzazioni limitate
 Se la soluzione contiene un documento o una cartella di lavoro che utilizza IRM, per impostazione predefinita Word ed Excel non consentono l'esecuzione di codice. Se si è l'autore del documento o si ha l'accesso con controllo completo, è possibile modificare l'impostazione predefinita in modo che la soluzione funzioni. Per altre informazioni, vedere [procedura: consentire l'esecuzione di codice dietro i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM impedisce l'utilizzo di <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per recuperare o modificare i dati memorizzati nella cache del documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Utenti finali per limitare le autorizzazioni ai documenti che usano le estensioni di codice gestito
 Chiunque disponga dell'accesso completo al documento o alla cartella di lavoro nella soluzione può utilizzare IRM per limitare le autorizzazioni. Se, ad esempio, un utente finale del reparto contabilità utilizza una soluzione che popola automaticamente un foglio di calcolo con i dati di un database, è possibile che l'utente desideri consentire l'accesso alle modifiche solo alle persone nel suo reparto e all'accesso in lettura agli altri. Quando l'utente aggiunge le autorizzazioni limitate, per impostazione predefinita non è possibile eseguire il codice sottostante al foglio di esecuzione e il foglio di dati non verrà popolato con i dati.

 Per risolvere il problema, un utente con accesso completo al documento o alla cartella di lavoro deve modificare le impostazioni di autorizzazione predefinite per consentire l'accesso a livello di codice al modello a oggetti. Per altre informazioni, vedere [procedura: consentire l'esecuzione di codice dietro i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Vedere anche
- [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione delle password nei documenti di Office](../vsto/password-protection-on-office-documents.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
