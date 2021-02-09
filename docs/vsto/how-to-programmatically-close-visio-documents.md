---
title: 'Procedura: chiudere documenti di Visio a livello di codice'
description: Informazioni su come chiudere il documento attivo Microsoft Office Visio usando il Microsoft.Office.Interop.Visio.Document. Metodo Close.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c1592bd500103a2db42934ab8f81392a5f1fa0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903683"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedura: chiudere documenti di Visio a livello di codice
  Per chiudere il documento attivo di Microsoft Office Visio, è possibile usare il metodo `Microsoft.Office.Interop.Visio.Document.Close`.

 Per informazioni dettagliate su questo metodo, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Chiudere il documento attivo

### <a name="to-close-the-active-document"></a>Per chiudere il documento attivo

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Close` per chiudere il documento attivo.

     Per usare l'esempio di codice seguente, eseguirlo nella `ThisAddIn` classe in un progetto di componente aggiuntivo VSTO per Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Vedi anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Procedura: creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)
