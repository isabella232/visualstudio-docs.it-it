---
title: 'Procedura: chiudere a livello di programmazione di documenti di Visio | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbb848c07828b8581a71e57fbeee411404632f31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedura: Chiudere documenti di Visio a livello di codice
  È possibile chiudere il documento di Microsoft Office Visio attivo tramite il metodo Close.  
  
 Per informazioni dettagliate su questo metodo, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) .  
  
## <a name="closing-the-active-document"></a>Chiusura del documento attivo  
  
#### <a name="to-close-the-active-document"></a>Per chiudere il documento attivo  
  
-   Chiamare il metodo Close per chiudere il documento attivo.  
  
     Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: salvare a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  