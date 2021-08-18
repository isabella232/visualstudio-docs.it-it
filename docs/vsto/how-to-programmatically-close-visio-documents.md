---
title: 'Procedura: Chiudere documenti di Visio a livello di codice'
description: Informazioni su come chiudere il Microsoft Office Visio attivo usando il Microsoft.Office.Interop.Visio.Docpubblicazione. Metodo Close.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c48b814629e01e370696bb30f8ee15af60098ec3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046646"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedura: Chiudere documenti di Visio a livello di codice
  Per chiudere il documento attivo di Microsoft Office Visio, è possibile usare il metodo `Microsoft.Office.Interop.Visio.Document.Close`.

 Per informazioni dettagliate su questo metodo, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Chiudere il documento attivo

### <a name="to-close-the-active-document"></a>Per chiudere il documento attivo

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Close` per chiudere il documento attivo.

     Per usare l'esempio di codice seguente, eseguirlo nella classe in un progetto VSTO componente aggiuntivo per `ThisAddIn` Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Procedura: Creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)
