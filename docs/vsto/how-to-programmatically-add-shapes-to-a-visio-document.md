---
title: 'Procedura: Aggiungere forme a un documento di Visio a livello di codice'
description: Informazioni su come aggiungere forme a un documento Microsoft Office Visio recuperando i master da uno stencil e rilasciando le forme nella pagina attiva.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5eabd18ac915e6cc10ff05de3d13d0263fa1eee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828410"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Procedura: Aggiungere forme a un documento di Visio a livello di codice
  È possibile aggiungere forme a un documento di Microsoft Office Visio recuperando i master da uno stencil e rilasciando le forme nella pagina attiva.

 Per altre informazioni, vedere la documentazione di riferimento di VBA per il metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) , la proprietà [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) e il metodo [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Aggiungere forme a un documento di Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Per aggiungere forme a un documento di Visio

- Con un documento attivo, recuperare i master dalla raccolta Documents.Masters e rilasciare le forme nel documento attivo. È possibile recuperare un master usando l'indice o il nome del master.

     L'esempio di codice seguente crea un documento di Visio vuoto e quindi lo apre con lo stencil **Forme base** ancorato. Il codice recupera quindi diverse forme e le inserisce nella pagina attiva.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Vedi anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Usare le forme di Visio](../vsto/working-with-visio-shapes.md)
- [Procedura: Copiare e incollare forme in un documento di Visio a livello di codice](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
