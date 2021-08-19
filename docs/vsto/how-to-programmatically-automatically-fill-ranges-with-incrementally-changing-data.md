---
title: Riempimento automatico degli intervalli di dati a livello di codice
description: Informazioni su come il metodo AutoFill dell'oggetto Range consente di riempire automaticamente un intervallo in un foglio di lavoro con valori.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 589feff2d70d2681898212df33d7b3ec468e6231
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099984"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Procedura: Riempire automaticamente gli intervalli con dati che cambiano in modo incrementale
  Il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo <xref:Microsoft.Office.Interop.Excel.Range> dell'oggetto consente di riempire automaticamente un intervallo in un foglio di lavoro. In genere, il metodo viene usato per archiviare valori in aumento o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> decrescente in modo incrementale in un intervallo. È possibile specificare il comportamento specificando una costante facoltativa <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> dall'enumerazione .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È necessario specificare due intervalli quando si usa <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Intervallo che chiama il metodo , che specifica il punto iniziale del riempimento <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> e contiene un valore iniziale.

- Intervallo da riempire, passato come parametro al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo . Questo intervallo di destinazione deve includere l'intervallo che contiene il valore iniziale.

    > [!NOTE]
    > Non è possibile passare <xref:Microsoft.Office.Tools.Excel.NamedRange> un controllo al posto di <xref:Microsoft.Office.Interop.Excel.Range> . Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi host e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>Compilare il codice
 La prima cella dell'intervallo da riempire deve contenere un valore iniziale.

 L'esempio richiede di riempire tre aree:

- La colonna B deve includere cinque giorni feriali. Per il valore iniziale, digitare **Monday** nella cella B1.

- La colonna C deve includere cinque mesi. Per il valore iniziale, digitare **Gennaio** nella cella C1.

- La colonna D include una serie di numeri, incrementando di due per ogni riga. Per i valori iniziali, digitare **4** nella cella D1 e **6** nella cella D2.

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Eseguire calcoli Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
