---
title: 'Procedura: a livello di programmazione salvare documenti di Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673194"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Procedura: a livello di programmazione salvare documenti di Visio
  Esistono varie modalità per salvare documenti di Microsoft Office Visio:  
  
-   Salvare le modifiche in un documento esistente.  
  
-   Salvare un nuovo documento oppure salvare un documento con un nuovo nome.  
  
-   Salvare un documento con gli argomenti specificati.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA per i metodi [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) e [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="save-an-existing-document"></a>Salvare un documento esistente  
  
### <a name="to-save-a-document"></a>Per salvare un documento  
  
-   Chiamare il `Microsoft.Office.Interop.Visio.Document.Save` metodo di `Microsoft.Office.Tools.Visio.Document` classe di un documento che è stato salvato in precedenza.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Il `Microsoft.Office.Interop.Visio.Document.Save` metodo genera un'eccezione se non è ancora stato salvato un nuovo documento di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Salvare un documento con un nuovo nome  
 Usare il `Microsoft.Office.Interop.Visio.Document.SaveAs` metodo per salvare un nuovo documento o un documento con un nuovo nome. Con questo metodo è necessario specificare il nuovo nome del file.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Per salvare il documento attivo con un nuovo nome  
  
-   Chiamare il `Microsoft.Office.Interop.Visio.Document.SaveAs` metodo di `Microsoft.Office.Tools.Visio.Document` che si desidera salvare usando un percorso completo include un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Salvare un documento con un nuovo nome e gli argomenti specificati  
 Usare il `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodo per salvare un documento con un nuovo nome e specificare qualsiasi argomento applicabile da applicare al documento.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Per salvare un documento con un nuovo nome e argomenti specificati  
  
-   Chiamare il `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodo di `Microsoft.Office.Tools.Visio.Document` che si desidera salvare usando un percorso completo include un nome file. Se un file con quel nome già esiste in quella cartella, viene generata un'eccezione.  
  
     L'esempio di codice seguente salva il documento attivo con un nuovo nome, lo contrassegna come di sola lettura e visualizza il documento nell'elenco di documenti Usati di recente. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Per salvare un documento con un nuovo nome, una directory denominata `Test` deve avere sede nel *documenti* cartella (per Windows XP e versioni precedenti) oppure il *documenti* cartella (per Windows Vista).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: stampa di documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  