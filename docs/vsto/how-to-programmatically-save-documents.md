---
title: 'Procedura: salvare documenti a livello di codice'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 464d131261ecfb0a64a3ca279007ff9332cdb2e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537592"
---
# <a name="how-to-programmatically-save-documents"></a>Procedura: salvare documenti a livello di codice

Esistono diversi modi per salvare Microsoft Office documenti di Word. È possibile salvare un documento senza modificare il nome del documento oppure è possibile salvare un documento con un nuovo nome.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Salvare un documento senza modificare il nome

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Per salvare il documento associato a una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> della classe <xref:Microsoft.Office.Tools.Word.Document> . Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Per salvare il documento attivo

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodo per il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Se non si è certi che il documento che si desidera salvare sia il documento attivo, è possibile farvi riferimento tramite il relativo nome.

### <a name="to-save-a-document-specified-by-name"></a>Per salvare un documento specificato in base al nome

1. Usare il nome del documento come argomento per la <xref:Microsoft.Office.Interop.Word.Documents> raccolta. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Salvare un documento con un nuovo nome

Usare il `SaveAs` metodo per salvare un documento con un nuovo nome. È possibile utilizzare questo metodo dell' <xref:Microsoft.Office.Tools.Word.Document> elemento host in un progetto di Word a livello di documento o di un <xref:Microsoft.Office.Interop.Word.Document> oggetto nativo in qualsiasi progetto di Word. Per questo metodo è necessario specificare il nuovo nome di file, ma altri argomenti sono facoltativi.

> [!NOTE]
> Se si visualizza la finestra di dialogo **SaveAs** all'interno del <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> gestore eventi di `ThisDocument` e si imposta il parametro *Cancel* su **false**, l'applicazione potrebbe uscire in modo imprevisto. Se si imposta il parametro *Cancel* su **true**, viene visualizzato un messaggio di errore che indica che il salvataggio automatico è stato disabilitato.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Per salvare il documento associato a una personalizzazione a livello di documento con un nuovo nome

1. Chiamare il `SaveAs` metodo della `ThisDocument` classe nel progetto, usando un percorso completo e un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .

    > [!NOTE]
    > Il `SaveAs` metodo genera un'eccezione se non esiste una directory di destinazione o se si verificano altri problemi durante il salvataggio di un file. È consigliabile usare un `try...catch` blocco intorno al `SaveAs` metodo o all'interno di un metodo chiamante.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Per salvare un documento nativo con un nuovo nome

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole salvare usando un percorso completo e un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.

     L'esempio di codice seguente salva il documento attivo con un nuovo nome. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

    > [!NOTE]
    > Il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo genera un'eccezione se non esiste una directory di destinazione o se si verificano altri problemi durante il salvataggio di un file. È consigliabile usare un **try... blocco catch** intorno al <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo o all'interno di un metodo chiamante.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Compilare il codice

Questo esempio di codice presenta i requisiti seguenti:

- Per salvare un documento in base al nome, è necessario che esista un documento denominato *NewDocument.doc* in una directory denominata *test* sull'unità C.

- Per salvare un documento con un nuovo nome, è necessario che esista una directory denominata *test* nell'unità C.

## <a name="see-also"></a>Vedere anche

- [Procedura: chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)
- [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elemento host Document](../vsto/document-host-item.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
