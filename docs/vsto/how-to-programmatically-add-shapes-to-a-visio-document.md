---
title: 'Procedura: a livello di codice aggiungere forme a un documento di Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32fc1b61505711cbcf353819372bcd1452bf3716
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256669"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Procedura: a livello di codice aggiungere forme a un documento di Visio
  È possibile aggiungere forme a un documento di Microsoft Office Visio recuperando i master da uno stencil e rilasciando le forme nella pagina attiva.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA per il metodo [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) , la proprietà [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) e il metodo [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) .  
  
## <a name="add-shapes-to-a-visio-document"></a>Aggiungere forme a un documento di Visio  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Per aggiungere forme a un documento di Visio  
  
-   Con un documento attivo, recuperare i master dalla raccolta Documents.Masters e rilasciare le forme nel documento attivo. È possibile recuperare un master usando l'indice o il nome del master.  
  
     L'esempio di codice seguente crea un documento di Visio vuoto e quindi lo apre con lo stencil **Forme base** ancorato. Il codice recupera quindi diverse forme e le inserisce nella pagina attiva.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)   
 [Procedura: copiare e incollare forme in un documento di Visio a livello di codice](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  