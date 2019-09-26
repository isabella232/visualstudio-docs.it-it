---
title: 'Procedura: Riempire controlli ListObject con dati'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a0916ca11d4df5f6b69376d7223143afbb407f6e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255885"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Procedura: Riempire controlli ListObject con dati
  È possibile usare il data binding per aggiungere rapidamente dati al documento. Dopo aver associato i dati a un oggetto elenco, è possibile disconnetterlo in modo che visualizzi i dati senza tuttavia essere più associato all'origine dati.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![collegamento al video](../vsto/media/playvideo.gif "collegamento al video") Per una dimostrazione video correlata, [vedere Ricerca per categorie: Creare un elenco in Excel connesso a un elenco SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

### <a name="to-bind-data-to-a-listobject-control"></a>Per associare dati a un controllo ListObject

1. Creare un oggetto <xref:System.Data.DataTable> a livello di classe.

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2. Aggiungere colonne e dati di esempio nel gestore eventi `Startup` della classe `Sheet1` (in un progetto a livello di documento) oppure della classe `ThisAddIn` (in un progetto a livello di applicazione).

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. 'ordine delle colonne nell'oggetto elenco può differire dall'ordine in cui vengono visualizzate nell'oggetto <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Per disconnettere il controllo ListObject dall'origine dati

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> di `List1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .

## <a name="see-also"></a>Vedere anche
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: Popolamento di fogli di dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Procedura: Popola i documenti con i dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
