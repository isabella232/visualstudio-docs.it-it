---
title: Convalida dati quando viene aggiunta una nuova riga al controllo ListObject
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
ms.openlocfilehash: f65bbc374c1d0ec2a940ff98fcc6f04e5391b2db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255673"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Procedura: Convalida dati quando viene aggiunta una nuova riga a un controllo ListObject
  Gli utenti possono aggiungere nuove righe a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato ai dati. È possibile convalidare i dati dell'utente prima del commit delle modifiche all'origine dati.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Convalida dei dati
 Ogni volta che viene aggiunta una riga a <xref:Microsoft.Office.Tools.Excel.ListObject> associata ai dati, viene generato l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . È possibile gestire questo evento per eseguire la convalida dei dati. Se, ad esempio, l'applicazione richiede che solo i dipendenti di età compresa tra 18 e 65 possano essere aggiunti all'origine dati, verificare che l'età immessa sia compresa nell'intervallo prima di aggiungere la riga.

> [!NOTE]
> È sempre opportuno verificare l'input dell'utente non solo nel client ma anche nel server. Per altre informazioni, vedere [proteggere le applicazioni client](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Per convalidare i dati quando una nuova riga viene aggiunta a un controllo ListObject associato ai dati

1. Creare variabili per l'ID e la classe <xref:System.Data.DataTable> a livello di classe.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Creare un nuovo <xref:System.Data.DataTable> e aggiungere le `Startup` colonne e i dati di esempio nel gestore eventi `Sheet1` della classe (in un progetto a livello di documento `ThisAddIn` ) o nella classe (in un progetto di componente aggiuntivo VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Aggiungere codice al gestore eventi `list1_BeforeAddDataBoundRow` per controllare se l'età immessa è compresa nell'intervallo appropriato.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .

## <a name="see-also"></a>Vedere anche
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
