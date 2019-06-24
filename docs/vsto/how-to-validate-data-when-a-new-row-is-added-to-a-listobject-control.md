---
title: Convalidare i dati quando viene aggiunta al controllo ListObject di nuova riga
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cf302388b71174767d41cc8b1a7594f4223db2a
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328868"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Procedura: Convalidare i dati quando viene aggiunta una nuova riga a un controllo ListObject
  Gli utenti possono aggiungere nuove righe a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato ai dati. È possibile convalidare i dati dell'utente prima del commit delle modifiche all'origine dati.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Convalida dei dati
 Ogni volta che viene aggiunta una riga a <xref:Microsoft.Office.Tools.Excel.ListObject> associata ai dati, viene generato l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . È possibile gestire questo evento per eseguire la convalida dei dati. Ad esempio, se l'applicazione richiede che solo i dipendenti di età compresa tra 18 e 65 possano essere aggiunti all'origine dati, verificare che l'età immessa è all'interno dell'intervallo prima che la riga viene aggiunta.

> [!NOTE]
> È sempre opportuno verificare l'input dell'utente non solo nel client ma anche nel server. Per altre informazioni, vedere [applicazioni client sicure](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Per convalidare i dati quando una nuova riga viene aggiunta a un controllo ListObject associato ai dati

1. Creare variabili per l'ID e la classe <xref:System.Data.DataTable> a livello di classe.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Creare una nuova <xref:System.Data.DataTable> e aggiungere le colonne di esempio e i dati nel `Startup` gestore dell'evento delle `Sheet1` classe (in un progetto a livello di documento) o `ThisAddIn` classe (in un progetto di componente aggiuntivo VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Aggiungere codice al gestore eventi `list1_BeforeAddDataBoundRow` per controllare se l'età immessa è compresa nell'intervallo appropriato.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .

## <a name="see-also"></a>Vedere anche
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
