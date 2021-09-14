---
title: Gestione dei diritti di & estensioni di codice gestito
description: Informazioni su Information Rights Management (IRM), una funzionalità che consente di impedire a utenti non autorizzati di visualizzare o modificare informazioni riservate.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fb32bc23de2335a912d1f2f6d3047af140961404
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710043"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Panoramica di Information Rights Management e delle estensioni di codice gestito
  Microsoft Office Word e Microsoft Office Excel forniscono Information Rights Management (IRM), una funzionalità che consente di impedire a utenti non autorizzati di visualizzare o modificare informazioni riservate. Per informazioni dettagliate sul funzionamento di Information Rights Management, vedere la Guida nell'applicazione Office specifica.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Eseguire documenti code-behind con autorizzazioni limitate
 Se la soluzione contiene un documento o una cartella di lavoro che usa IRM, per impostazione predefinita Word e Excel non consentono l'esecuzione di codice. Se si è l'autore del documento o si dispone dell'accesso Controllo completo, è possibile modificare l'impostazione predefinita in modo che la soluzione funzioni. Per altre informazioni, vedere [Procedura: Consentire l'esecuzione di codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)dietro documenti con autorizzazioni limitate.

 IRM impedisce <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> l'uso di per recuperare o modificare i dati memorizzati nella cache del documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Utenti finali per limitare le autorizzazioni ai documenti che usano estensioni di codice gestito
 Chiunque abbia accesso controllo completo al documento o alla cartella di lavoro nella soluzione può usare IRM per limitare le autorizzazioni. Ad esempio, se un utente finale del reparto contabilità usa una soluzione che popola automaticamente un foglio di lavoro con i dati di un database, l'utente potrebbe voler consentire l'accesso Modifica solo alle persone del proprio reparto e l'accesso in lettura ad altri utenti. Quando l'utente aggiunge le autorizzazioni limitate, per impostazione predefinita non è possibile eseguire il codice dietro il foglio di lavoro e il foglio di lavoro non verrà popolato con i dati.

 Per risolvere il problema, un utente con accesso controllo completo al documento o alla cartella di lavoro deve modificare le impostazioni di autorizzazione predefinite per consentire l'accesso a livello di codice al modello a oggetti. Per altre informazioni, vedere [Procedura: Consentire l'esecuzione di codice](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)dietro documenti con autorizzazioni limitate.

## <a name="see-also"></a>Vedi anche
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione della password nei Office documenti](../vsto/password-protection-on-office-documents.md)
- [Proteggere Office soluzioni](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
