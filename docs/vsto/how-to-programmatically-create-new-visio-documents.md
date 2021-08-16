---
title: 'Procedura: Creare nuovi documenti di Visio a livello di codice'
description: Informazioni su come creare un nuovo documento di disegno di Microsoft Visio a livello di codice e aggiungerlo alla raccolta Documenti di documenti Visio aperti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a195996684334cbc658d75f82a5f81f1d69109af45174b3ce6b2f6c996c38ae8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384327"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Procedura: Creare nuovi documenti di Visio a livello di codice
  Quando si crea un nuovo disegno di Microsoft Office Visio, viene aggiunto alla raccolta `Microsoft.Office.Interop.Visio.Documents` di documenti di Visio aperti. Il metodo `Microsoft.Office.Interop.Visio.Documents.Add` crea quindi un nuovo documento di disegno di Visio. Per altre informazioni, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Creare nuovi documenti vuoti

### <a name="to-create-a-new-document"></a>Per creare un nuovo documento

- Usare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` per creare un nuovo documento vuoto che non si basa su un modello.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Creare documenti copiati da documenti esistenti
 Il metodo `Microsoft.Office.Interop.Visio.Documents.Add` può creare un nuovo documento che è una copia di un documento di Visio esistente. È necessario specificare il nome file e il percorso completo del diagramma.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Per creare un nuovo documento copiato da un documento esistente

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso del diagramma di Visio.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Creare stencil copiati da stencil esistenti
 Il metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) può creare un nuovo stencil che è una copia di uno stencil di Visio esistente. È necessario specificare il nome file e il percorso completo dello stencil.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Per creare un nuovo stencil copiato da uno stencil esistente

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso dello stencil.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Creare documenti basati su modelli esistenti
 Il metodo può creare un nuovo documento (un file con estensione vsd) basato su un modello Visio esistente (un file con estensione `Microsoft.Office.Interop.Visio.Documents.Add` *vst).*  Questo metodo copia gli stencil, gli stili e le impostazioni che fanno parte dell'area di lavoro modello. È necessario specificare il nome file e il percorso completo del modello.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Per creare un nuovo documento basato su un modello esistente

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso del modello.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Un Visio denominato deve trovarsi in una directory denominata nella cartella Documenti (per Windows XP e versioni precedenti) o nella cartella Documenti `myDrawing.vsd` `Test` (per Windows Vista).  

- Un Visio denominato deve trovarsi in una directory denominata nella cartella Documenti (per Windows XP e versioni precedenti) o nella cartella Documenti `myStencil.vss` `Test` (per Windows Vista).  

- Un Visio denominato deve trovarsi in una directory denominata nella cartella Documenti (per Windows XP e versioni precedenti) o nella cartella Documenti `myTemplate.vst` `Test` (per Windows Vista).  

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)
