---
title: Convalidare i dati quando viene aggiunta una nuova riga al controllo ListObject
description: Informazioni su come usare Visual Studio convalida dei dati quando viene aggiunta una nuova riga a un controllo ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0b9b70630708ebc558a798371a6d39ff30aed6f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082933"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Procedura: Convalidare i dati quando viene aggiunta una nuova riga a un controllo ListObject
  Gli utenti possono aggiungere nuove righe a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato ai dati. È possibile convalidare i dati dell'utente prima del commit delle modifiche all'origine dati.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Convalida dei dati
 Ogni volta che viene aggiunta una riga a <xref:Microsoft.Office.Tools.Excel.ListObject> associata ai dati, viene generato l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . È possibile gestire questo evento per eseguire la convalida dei dati. Ad esempio, se l'applicazione richiede che solo i dipendenti di età compresa tra i 18 e i 65 anni possano essere aggiunti all'origine dati, verificare che l'età immessa sia compresa in tale intervallo prima dell'aggiunta della riga.

> [!NOTE]
> È sempre opportuno verificare l'input dell'utente non solo nel client ma anche nel server. Per altre informazioni, vedere [Proteggere le applicazioni client.](/dotnet/framework/data/adonet/secure-client-applications)

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Per convalidare i dati quando una nuova riga viene aggiunta a un controllo ListObject associato ai dati

1. Creare variabili per l'ID e la classe <xref:System.Data.DataTable> a livello di classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Creare una nuova classe e aggiungere colonne e dati di esempio nel gestore eventi della classe (in un progetto a livello di documento) o della classe (in un progetto VSTO <xref:System.Data.DataTable> `Startup` componente `Sheet1` `ThisAddIn` aggiuntivo).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Aggiungere codice al gestore eventi `list1_BeforeAddDataBoundRow` per controllare se l'età immessa è compresa nell'intervallo appropriato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che nel foglio di lavoro in cui appare il codice sia già presente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `list1` .

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word Excel cartelle di lavoro in VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli sui Office di lavoro](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli per Office documenti in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Controllo ListObject](../vsto/listobject-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Eseguire il mapping di colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
