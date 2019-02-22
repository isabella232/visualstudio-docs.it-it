---
title: 'Procedura: A livello di programmazione chiudere documenti di Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9059e0f066cbd1dc6ced5f11f1139d7687afacf3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597207"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedura: A livello di programmazione chiudere documenti di Visio
  Per chiudere il documento attivo di Microsoft Office Visio, è possibile usare il metodo `Microsoft.Office.Interop.Visio.Document.Close`.

 Per informazioni dettagliate su questo metodo, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Chiudere il documento attivo

### <a name="to-close-the-active-document"></a>Per chiudere il documento attivo

-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Close` per chiudere il documento attivo.

     Per usare il codice seguente, eseguirlo `ThisAddIn` classe in un progetto di componente aggiuntivo VSTO per Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Vedere anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)
- [Procedura: Creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: A livello di codice aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: A livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: A livello di programmazione stampare documenti di Visio](../vsto/how-to-programmatically-print-visio-documents.md)
