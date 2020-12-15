---
title: 'Procedura: ricerca di testo negli intervalli dei fogli di testo a livello di codice'
description: Informazioni su come usare Visual Studio per eseguire la ricerca a livello di codice di testo negli intervalli dei fogli di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01ce01e76aa56a834f4f63cd2bd0f6f16c4ab03a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524560"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Procedura: ricerca di testo negli intervalli dei fogli di testo a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> metodo dell' <xref:Microsoft.Office.Interop.Excel.Range> oggetto consente di cercare testo compreso nell'intervallo. Questo testo può essere costituito anche da qualsiasi stringa di errore che può essere presente in una cella di un foglio di foglio, ad esempio `#NULL!` o `#VALUE!` . Per ulteriori informazioni sulle stringhe di errore, vedere la pagina relativa ai [valori di errore della cella](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Nell'esempio seguente viene eseguita la ricerca di un intervallo denominato `Fruits` e viene modificato il tipo di carattere per le celle che contengono la parola "mele". Questa procedura usa anche il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo, che usa le impostazioni di ricerca impostate in precedenza per ripetere la ricerca. Si specifica la cella dopo la quale eseguire la ricerca e il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo gestisce il resto.

> [!NOTE]
> La <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> ricerca del metodo esegue il ritorno all'inizio dell'intervallo di ricerca dopo che ha raggiunto la fine dell'intervallo. Il codice deve assicurarsi che la ricerca non venga incapsulata in un ciclo infinito. Nella procedura di esempio viene illustrato un modo per gestire questa operazione utilizzando la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Proprietà.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Per cercare il testo in un intervallo del foglio di testo

1. Dichiarare le variabili per il rilevamento dell'intero intervallo, il primo intervallo trovato e l'intervallo trovato corrente.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Cercare la prima corrispondenza, specificando tutti i parametri eccetto la cella in cui eseguire la ricerca.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Continua la ricerca finché sono presenti corrispondenze.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Confrontare il primo intervallo trovato ( `firstFind` ) con **Nothing**. Se `firstFind` non contiene alcun valore, il codice archivia l'intervallo trovato ( `currentFind` ).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Uscire dal ciclo se l'indirizzo dell'intervallo trovato corrisponde all'indirizzo del primo intervallo trovato.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Imposta l'aspetto dell'intervallo trovato.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Eseguire un'altra ricerca.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   L'esempio seguente mostra il metodo completo.

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
