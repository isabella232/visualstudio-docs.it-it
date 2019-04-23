---
title: 'Procedura: A livello di codice aggiungere forme a un documento di Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e172ff57fb784d6ae768dde1e705ef645b3f9a9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117785"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Procedura: A livello di codice aggiungere forme a un documento di Visio
  È possibile aggiungere forme a un documento di Microsoft Office Visio recuperando i master da uno stencil e rilasciando le forme nella pagina attiva.

 Per altre informazioni, vedere la documentazione di riferimento di VBA per il metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) , la proprietà [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) e il metodo [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Aggiungere forme a un documento di Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Per aggiungere forme a un documento di Visio

- Con un documento attivo, recuperare i master dalla raccolta Documents.Masters e rilasciare le forme nel documento attivo. È possibile recuperare un master usando l'indice o il nome del master.

     L'esempio di codice seguente crea un documento di Visio vuoto e quindi lo apre con lo stencil **Forme base** ancorato. Il codice recupera quindi diverse forme e le inserisce nella pagina attiva.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Vedere anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)
- [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)
- [Procedura: Copiare e incollare forme in un documento di Visio a livello di codice](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
