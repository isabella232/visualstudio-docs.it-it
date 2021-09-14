---
title: 'Procedura: Cercare testo negli intervalli di fogli di lavoro a livello di codice'
description: Informazioni su come usare i Visual Studio per cercare testo in intervalli Microsoft Excel foglio di lavoro.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dd001c197f9c64c5d0fa5c89a3920a40f427cf58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633907"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Procedura: Cercare testo negli intervalli di fogli di lavoro a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> metodo <xref:Microsoft.Office.Interop.Excel.Range> dell'oggetto consente di cercare testo all'interno dell'intervallo. Questo testo può anche essere qualsiasi stringa di errore che può essere visualizzata in una cella del foglio di lavoro, ad esempio `#NULL!` o `#VALUE!` . Per altre informazioni sulle stringhe di errore, vedere [Valori di errore delle celle](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Nell'esempio seguente viene eseguita una ricerca in un intervallo denominato e viene modificato il tipo di carattere per le celle `Fruits` contenenti la parola "apples". Questa procedura usa anche il metodo , che usa le impostazioni di ricerca impostate in precedenza <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> per ripetere la ricerca. Si specifica la cella dopo la quale eseguire la ricerca e il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo gestisce il resto.

> [!NOTE]
> La ricerca del metodo torna all'inizio dell'intervallo di ricerca dopo che ha <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> raggiunto la fine dell'intervallo. Il codice deve garantire che la ricerca non eserciti il wrapping in un ciclo infinito. La procedura di esempio illustra un modo per gestirlo usando la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> proprietà .

## <a name="to-search-for-text-in-a-worksheet-range"></a>Per cercare testo in un intervallo di fogli di lavoro

1. Dichiarare le variabili per tenere traccia dell'intero intervallo, del primo intervallo trovato e dell'intervallo trovato corrente.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Cercare la prima corrispondenza, specificando tutti i parametri tranne la cella in cui eseguire la ricerca.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Continuare la ricerca fino a quando sono presenti corrispondenze.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Confrontare il primo intervallo trovato ( `firstFind` ) con **Nothing**. Se `firstFind` non contiene alcun valore, il codice archivia l'intervallo trovato ( `currentFind` ).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Uscire dal ciclo se l'indirizzo dell'intervallo trovato corrisponde all'indirizzo del primo intervallo trovato.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Impostare l'aspetto dell'intervallo trovato.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Eseguire un'altra ricerca.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   L'esempio seguente mostra il metodo completo.

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
