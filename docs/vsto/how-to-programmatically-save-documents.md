---
title: 'Procedura: Salvare documenti a livello di codice'
description: Informazioni su come usare Visual Studio salvare un documento a livello di codice senza modificare il nome del documento o con un nuovo nome.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2b1e00d60709d506ae0d3ee2d4bd6842be43be19
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046464"
---
# <a name="how-to-programmatically-save-documents"></a>Procedura: Salvare documenti a livello di codice

Esistono diversi modi per salvare Microsoft Office documenti di Word. È possibile salvare un documento senza modificare il nome del documento oppure è possibile salvare un documento con un nuovo nome.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Salvare un documento senza modificare il nome

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Per salvare il documento associato a una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> della classe <xref:Microsoft.Office.Tools.Word.Document> . Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>Per salvare il documento attivo

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodo per il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   Se non si è certi che il documento da salvare sia il documento attivo, è possibile fare riferimento a esso in base al nome.

### <a name="to-save-a-document-specified-by-name"></a>Per salvare un documento specificato in base al nome

1. Usare il nome del documento come argomento per la <xref:Microsoft.Office.Interop.Word.Documents> raccolta. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>Salvare un documento con un nuovo nome

Usare il `SaveAs` metodo per salvare un documento con un nuovo nome. È possibile usare questo metodo dell'elemento host in un progetto Word a livello di documento o di <xref:Microsoft.Office.Tools.Word.Document> un oggetto nativo in qualsiasi progetto <xref:Microsoft.Office.Interop.Word.Document> Word. Questo metodo richiede di specificare il nuovo nome file, ma altri argomenti sono facoltativi.

> [!NOTE]
> Se si visualizza la **finestra di dialogo SaveAs** all'interno del gestore eventi di e si imposta il parametro Cancel su false , l'applicazione <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> potrebbe `ThisDocument` chiudersi in modo imprevisto.   Se si imposta il *parametro Cancel* su **true**, viene visualizzato un messaggio di errore che indica che il salvataggio automatico è stato disabilitato.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Per salvare il documento associato a una personalizzazione a livello di documento con un nuovo nome

1. Chiamare il `SaveAs` metodo della classe nel `ThisDocument` progetto, usando un percorso completo e un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .

    > [!NOTE]
    > Il metodo genera un'eccezione se non esiste una directory di destinazione o se si verificano `SaveAs` altri problemi durante il salvataggio di un file. È consigliabile usare un blocco intorno al metodo o `try...catch` all'interno di un metodo `SaveAs` chiamante.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>Per salvare un documento nativo con un nuovo nome

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo <xref:Microsoft.Office.Interop.Word.Document> dell'oggetto da salvare, usando un percorso completo e un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.

     Nell'esempio di codice seguente il documento attivo viene salvato con un nuovo nome. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

    > [!NOTE]
    > Il metodo genera un'eccezione se non esiste una directory di destinazione o se si verificano <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> altri problemi durante il salvataggio di un file. È consigliabile usare una **prova... Blocco catch** intorno al <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo o all'interno di un metodo chiamante.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>Compilare il codice

Questo esempio di codice presenta i requisiti seguenti:

- Per salvare un documento in base al nome, un documento denominato *NewDocument.doc* deve esistere in una directory denominata *Test* nell'unità C.

- Per salvare un documento con un nuovo nome, è necessario che nell'unità C sia presente una directory denominata *Test.*

## <a name="see-also"></a>Vedi anche

- [Procedura: Chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elemento host del documento](../vsto/document-host-item.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
