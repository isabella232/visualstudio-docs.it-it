---
title: Associazione tardiva nelle soluzioni Office
description: Informazioni sul modo in cui alcuni tipi nei modelli a oggetti all'interno Microsoft Office forniscono funzionalità disponibili tramite funzionalità di associazione tardiva.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823886"
---
# <a name="late-binding-in-office-solutions"></a>Associazione tardiva nelle soluzioni Office
  Alcuni tipi nei modelli a oggetti delle applicazioni di Office forniscono funzionalità disponibili tramite funzionalità di associazione tardiva. Ad esempio, alcuni metodi e proprietà possono restituire tipi diversi di oggetti a seconda del contesto dell'applicazione di Office e alcuni tipi possono esporre metodi o proprietà diversi in contesti diversi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic progetti in cui **Option Strict** è disattivato e i progetti Visual C# che hanno come destinazione o possono funzionare direttamente con i tipi che utilizzano queste funzionalità di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] associazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] tardiva.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Cast implicito ed esplicito dei valori restituiti dell'oggetto
 Molti metodi e proprietà nel Microsoft Office di interoperabilità primari restituiscono valori, perché possono restituire diversi <xref:System.Object> tipi di oggetti. Ad esempio, la proprietà restituisce perché il valore restituito può essere un oggetto o <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> , a seconda del foglio <xref:System.Object> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> attivo.

 Quando un metodo o una proprietà restituisce , è necessario convertire in modo esplicito (in Visual Basic) l'oggetto nel tipo corretto nei progetti Visual Basic in cui <xref:System.Object> **Option Strict** è attiva. Non è necessario eseguire il cast esplicito dei <xref:System.Object> valori restituiti nei Visual Basic in **cui Option Strict** è disattivato.

 Nella maggior parte dei casi, nella documentazione di riferimento sono elencati i tipi possibili del valore restituito per un membro che restituisce un oggetto <xref:System.Object> . La conversione o il cast dell'oggetto abilita IntelliSense per l'oggetto nell'editor di codice.

 Per informazioni sulla conversione in Visual Basic, vedere [Conversioni implicite ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) ed esplicite &#40;Visual Basic&#41;e funzione [CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come eseguire il cast di un oggetto a un tipo specifico in un Visual Basic in **cui Option Strict è** on. In questo tipo di progetto è necessario eseguire in modo esplicito il cast <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> della proprietà a un oggetto <xref:Microsoft.Office.Interop.Excel.Range> . Questo esempio richiede un progetto Excel a livello di documento con una classe foglio di lavoro denominata `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 Nell'esempio di codice seguente viene illustrato come eseguire il cast implicito di un oggetto a un tipo specifico in un progetto Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual C# destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In questi tipi di progetti viene eseguito il cast implicito della proprietà <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> a un oggetto <xref:Microsoft.Office.Interop.Excel.Range> . Questo esempio richiede un progetto Excel a livello di documento con una classe foglio di lavoro denominata `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Accedere ai membri disponibili solo tramite associazione tardiva
 Alcune proprietà e metodi negli elementi di interoperabilità personali di Office sono disponibili solo tramite l'associazione tardiva. Nei Visual Basic in cui **Option Strict** è disattivato o nei progetti Visual C# che hanno come destinazione o , è possibile usare le funzionalità di associazione tardiva in questi linguaggi per accedere ai membri ad associazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] tardiva. Nei Visual Basic in cui **Option Strict è** attiva, è necessario usare la reflection per accedere a questi membri.

### <a name="examples"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come accedere ai membri ad associazione tardiva in un progetto Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual C# destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Questo esempio accede alla proprietà **Nome** ad associazione tardiva della finestra di dialogo **Apri** file in Word. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o in un progetto `ThisAddIn` Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 L'esempio di codice seguente illustra come usare la reflection per eseguire la stessa attività in un progetto Visual Basic in **cui Option Strict** è attivata.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Vedi anche
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Usare la guida di programmazione &#40;C&#35; di programmazione&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
