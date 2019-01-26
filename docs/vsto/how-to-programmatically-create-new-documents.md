---
title: 'Procedura: Creazione di nuovi documenti a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 94f39c80fc2b9294afb172c58fa62ef17f06516d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874653"
---
# <a name="how-to-programmatically-create-new-documents"></a>Procedura: Creazione di nuovi documenti a livello di codice
  Quando si crea un documento a livello di programmazione, il nuovo documento è un oggetto <xref:Microsoft.Office.Interop.Word.Document> nativo. Questo oggetto non ha le funzionalità di data binding e gli eventi aggiuntivi di un elemento host <xref:Microsoft.Office.Tools.Word.Document>. Per altre informazioni, vedere [limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Quando si sviluppa un progetto a livello di documento, non è possibile aggiungere a livello di codice elementi host <xref:Microsoft.Office.Tools.Word.Document> al progetto. In un progetto di componente aggiuntivo VSTO è possibile convertire qualsiasi oggetto <xref:Microsoft.Office.Interop.Word.Document> in elemento host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Per creare un nuovo documento basato sul modello Normal  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> per creare un nuovo documento basato sul modello Normal. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="use-custom-templates"></a>Usare i modelli personalizzati  
 Il <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodo ha facoltativo *modello* argomento per creare un nuovo documento basato su un modello diverso dal modello Normal. È necessario specificare il nome file e il percorso completo del modello.  
  
### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Per creare un nuovo documento basato su un modello personalizzato  
  
-   Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> e specificare il percorso del modello. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: A livello di codice aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
