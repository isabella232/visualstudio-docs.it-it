---
title: 'Procedura: salvare i documenti a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 00ad8f91e738cb98aeba93b69cb47c6ab644aa3f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671887"
---
# <a name="how-to-programmatically-save-documents"></a>Procedura: salvare i documenti a livello di codice
  Esistono diversi modi per salvare i documenti di Microsoft Office Word. È possibile salvare un documento senza modificare il nome del documento, oppure è possibile salvare un documento con un nuovo nome.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Salvare un documento senza modificare il nome  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Per salvare il documento associato a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>Per salvare il documento attivo  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodo per il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Se non si è certi se il documento che si desidera salvare il documento attivo, è possibile fare riferimento ad esso in base al nome.  
  
### <a name="to-save-a-document-specified-by-name"></a>Per salvare un documento specificato in base al nome  
  
1.  Usare il nome del documento come argomento per il <xref:Microsoft.Office.Interop.Word.Documents> raccolta. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Salvare un documento con un nuovo nome  
 Usare il metodo SaveAs per salvare un documento con un nuovo nome. È possibile usare questo metodo per la <xref:Microsoft.Office.Tools.Word.Document> elemento host in un progetto di Word a livello di documento o di nativo <xref:Microsoft.Office.Interop.Word.Document> oggetto in qualsiasi progetto di Word. Questo metodo richiede che si specifica il nuovo nome file, ma gli altri argomenti sono facoltativi.  
  
> [!NOTE]  
>  Se si visualizza il **SaveAs** all'interno della finestra di dialogo il <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> gestore dell'evento di `ThisDocument` e impostare il *Annulla* parametro **false**, l'applicazione potrebbe chiusura imprevista. Se si impostano i *annullare* parametro per **true**, viene visualizzato un messaggio di errore che indicherà che è stata disabilitata.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Per salvare il documento associato a una personalizzazione a livello di documento con un nuovo nome  
  
1.  Chiamare il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo di `ThisDocument` classe nel progetto, utilizzando un nome di file e percorso completo. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .  
  
    > [!NOTE]  
    >  Il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo genera un'eccezione se una directory di destinazione non esiste o se sono presenti altri problemi di salvataggio di un file. È buona norma usare un **try... catch** blocca tutto il <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodo o all'interno di un metodo di chiamata.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Per salvare un documento nativo con un nuovo nome  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo di <xref:Microsoft.Office.Interop.Word.Document> che si desidera salvare, usando un nome di file e percorso completo. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.  
  
     Esempio di codice seguente salva il documento attivo con un nuovo nome. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo genera un'eccezione se una directory di destinazione non esiste o se sono presenti altri problemi di salvataggio di un file. È buona norma usare un **try... catch** blocca tutto il <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodo o all'interno di un metodo di chiamata.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Per salvare un documento in base al nome, un documento denominato *NewDocument. doc* deve essere presente in una directory denominata *Test* nell'unità C.  
  
-   Per salvare un documento con un nuovo nome, una directory denominata *Test* deve esistere nell'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: chiudere i documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)   
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  