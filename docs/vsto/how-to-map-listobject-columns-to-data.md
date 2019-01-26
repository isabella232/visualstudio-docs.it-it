---
title: 'Procedura: Eseguire il mapping delle colonne ListObject ai dati'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 276b606bbd4f87898916a6e7ca1dbf57ce3d6716
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873782"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Procedura: Eseguire il mapping delle colonne ListObject ai dati
  Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un oggetto <xref:System.Data.DataTable>, è possibile che non si voglia visualizzare tutte le colonne in un elenco o che alcune colonne non siano associate a dati. È possibile mappare le colonne da visualizzare nel <xref:Microsoft.Office.Tools.Excel.ListObject> quando si chiama il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Creare un elenco in Excel connesso a un elenco di SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="map-columns"></a>Eseguire il mapping di colonne  
  
### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Per mappare una tabella dati alle colonne in un elenco  
  
1.  Creare l'oggetto <xref:System.Data.DataTable> a livello di classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Aggiungere le colonne di esempio e i dati nel `Startup` gestore dell'evento del `Sheet1` classe (in un progetto a livello di documento) o `ThisAddIn` classe (in un progetto di componente aggiuntivo VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. L'oggetto elenco verrà associato all'oggetto appena creato <xref:System.Data.DataTable>, ma l'ordine delle colonne nell'oggetto elenco sarà diverso dall'ordine vengono visualizzati nei <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specify-unmapped-columns"></a>Specificare le colonne senza mapping  
 Quando si mappano le colonne a un oggetto <xref:System.Data.DataTable>, si può anche specificare che alcune colonne non devono essere associate a dati passando una stringa vuota. Viene quindi aggiunta una nuova colonna non associata a dati al controllo <xref:Microsoft.Office.Tools.Excel.ListObject> .  
  
### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Per specificare una colonna non mappata durante il mapping delle colonne ListObject  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. Usare una stringa vuota per indicare dove viene aggiunta una colonna non mappata, in questo caso tra la colonna del titolo e la colonna del cognome.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: Riempire controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject (controllo)](../vsto/listobject-control.md)  
