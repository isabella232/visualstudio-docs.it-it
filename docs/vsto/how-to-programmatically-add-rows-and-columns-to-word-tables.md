---
title: 'Procedura: A livello di codice aggiungere righe e colonne alle tabelle di Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55a755ccdd7f14af5a38fc516cdb9f76e936e10d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804578"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Procedura: A livello di codice aggiungere righe e colonne alle tabelle di Word
  In una tabella di Microsoft Office Word le celle sono organizzate in righe e colonne. È possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Rows> per aggiungere righe alla tabella e il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Columns> per aggiungere colonne.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Esempi di personalizzazione a livello di documento  
 Gli esempi di codice seguenti possono essere usati in una personalizzazione a livello di documento. Per usare questi esempi, eseguirli dalla classe `ThisDocument` nel progetto. Gli esempi presuppongono che il documento associato alla personalizzazione contenga già almeno una tabella.  
  
> [!IMPORTANT]
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:  
> 
> - Documento di Word 2013  
> - Modello di Word 2013  
> - Documento di Word 2010  
> - Modello di Word 2010  
> 
>   Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento per la **Interop** assembly, quindi è necessario usare le classi da tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Esempi di componente aggiuntivo VSTO  
 Gli esempi di codice seguenti possono essere usati in un componente aggiuntivo VSTO. Per usare gli esempi, eseguirli dalla classe `ThisAddIn` nel progetto. Gli esempi presuppongono che il documento attivo contenga già almeno una tabella.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando modelli di componente aggiuntivo VSTO per Word.  
>   
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento per la **Interop** assembly, quindi è necessario usare le classi da tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: A livello di codice, creare tabelle di Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: A livello di codice aggiungere il testo e formattazione alle celle delle tabelle di Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: A livello di codice compilare tabelle di Word con le proprietà documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  