---
title: 'Procedura: Creare nuovi documenti a livello di codice'
description: Informazioni su come creare nuovi documenti in Microsoft Word a livello di codice usando Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c52a1cffee3d87a6cd8461024c0ae7e8fab7aa08
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633948"
---
# <a name="how-to-programmatically-create-new-documents"></a>Procedura: Creare nuovi documenti a livello di codice
  Quando si crea un documento a livello di programmazione, il nuovo documento è un oggetto <xref:Microsoft.Office.Interop.Word.Document> nativo. Questo oggetto non ha le funzionalità di data binding e gli eventi aggiuntivi di un elemento host <xref:Microsoft.Office.Tools.Word.Document>. Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi host e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Quando si sviluppa un progetto a livello di documento, non è possibile aggiungere a livello di codice elementi host <xref:Microsoft.Office.Tools.Word.Document> al progetto. In un progetto di componente aggiuntivo VSTO è possibile convertire qualsiasi oggetto <xref:Microsoft.Office.Interop.Word.Document> in elemento host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione. Per altre informazioni, vedere Estendere documenti di Word Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Per creare un nuovo documento basato sul modello Normal

- Usare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> per creare un nuovo documento basato sul modello Normal. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet1":::

## <a name="use-custom-templates"></a>Usare modelli personalizzati
 Il <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodo dispone di un argomento *Template* facoltativo per creare un nuovo documento basato su un modello diverso dal modello Normal. È necessario specificare il nome file e il percorso completo del modello.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Per creare un nuovo documento basato su un modello personalizzato

- Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> e specificare il percorso del modello. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
