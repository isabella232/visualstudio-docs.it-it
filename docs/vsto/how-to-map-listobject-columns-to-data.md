---
title: 'Procedura: Eseguire il mapping di colonne ListObject ai dati'
description: Informazioni su come eseguire il mapping delle colonne da visualizzare in ListObject quando si chiama il metodo SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e611ebd51428b91311dade00b42095ba0501d276b2dfe91f7a407593894348fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394654"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Procedura: Eseguire il mapping di colonne ListObject ai dati
  Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un oggetto <xref:System.Data.DataTable>, è possibile che non si voglia visualizzare tutte le colonne in un elenco o che alcune colonne non siano associate a dati. È possibile mappare le colonne da visualizzare nel <xref:Microsoft.Office.Tools.Excel.ListObject> quando si chiama il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapping delle colonne

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Per mappare una tabella dati alle colonne in un elenco

1. Creare l'oggetto <xref:System.Data.DataTable> a livello di classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Aggiungere colonne e dati di esempio nel gestore eventi della classe (in un progetto a livello di documento) o della classe (in un `Startup` progetto VSTO componente aggiuntivo `Sheet1` `ThisAddIn` personalizzato).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. L'oggetto elenco verrà associato all'oggetto appena creato, ma l'ordine delle colonne nell'oggetto elenco sarà diverso da quello <xref:System.Data.DataTable> visualizzato in <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Specificare colonne non mappate
 Quando si mappano le colonne a un oggetto <xref:System.Data.DataTable>, si può anche specificare che alcune colonne non devono essere associate a dati passando una stringa vuota. Viene quindi aggiunta una nuova colonna non associata a dati al controllo <xref:Microsoft.Office.Tools.Excel.ListObject> .

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Per specificare una colonna non mappata durante il mapping delle colonne ListObject

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> e passare i nomi delle colonne nell'ordine in cui dovrebbero essere visualizzate. Usare una stringa vuota per indicare dove viene aggiunta una colonna non mappata, in questo caso tra la colonna del titolo e la colonna del cognome.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word Excel cartelle di lavoro VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Compilare controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Controllo ListObject](../vsto/listobject-control.md)
