---
title: 'Procedura: chiudere a livello di programmazione di documenti di Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671573"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedura: chiudere a livello di programmazione di documenti di Visio
  Per chiudere il documento attivo di Microsoft Office Visio, è possibile usare il metodo `Microsoft.Office.Interop.Visio.Document.Close`.  
  
 Per informazioni dettagliate su questo metodo, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .  
  
## <a name="close-the-active-document"></a>Chiudere il documento attivo  
  
### <a name="to-close-the-active-document"></a>Per chiudere il documento attivo  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Close` per chiudere il documento attivo.  
  
     Per usare il codice seguente, eseguirlo `ThisAddIn` classe in un progetto di componente aggiuntivo VSTO per Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: a livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: stampa di documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  