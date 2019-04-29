---
title: Associazione tardiva nelle soluzioni Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62224006d04e0a1e7447053e868dd9946f00c97e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583946"
---
# <a name="late-binding-in-office-solutions"></a>Associazione tardiva nelle soluzioni Office
  Alcuni tipi nei modelli a oggetti delle applicazioni di Office offrono funzionalità che è disponibile tramite le funzionalità di associazione tardiva. Ad esempio, alcuni metodi e proprietà può restituire diversi tipi di oggetti a seconda del contesto dell'applicazione di Office e alcuni tipi possono esporre diversi metodi o proprietà in contesti diversi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Progetti Visual Basic, dove **Option Strict** è disattivato e Visual C# che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o il [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] può lavorare direttamente con i tipi che utilizzano queste funzionalità di associazione tardiva.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>I valori restituiti implicite ed esplicite cast dell'oggetto
 Numerosi metodi e proprietà di Microsoft Office assembly di interoperabilità primari (PIA) restituiscono <xref:System.Object> valori, perché possono restituire diversi tipi di oggetti. Ad esempio, il <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> proprietà restituisce un <xref:System.Object> perché il relativo valore restituito può essere una <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart> oggetto, a seconda che cos'è il foglio attivo.

 Quando un metodo o la proprietà restituisce un <xref:System.Object>, è necessario convertire in modo esplicito (in Visual Basic) l'oggetto nel tipo corretto nei progetti Visual Basic in cui **Option Strict** si trova in. Non è necessario eseguire il cast esplicito <xref:System.Object> restituire i valori nei progetti Visual Basic in cui **Option Strict** è disattivata.

 Nella maggior parte dei casi, la documentazione di riferimento vengono elencati i possibili tipi di valore restituito per un membro che restituisce un <xref:System.Object>. La conversione o il cast dell'oggetto Abilita IntelliSense per l'oggetto nell'Editor del codice.

 Per informazioni sulla conversione in Visual Basic, vedere [conversioni implicite ed esplicite &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [CType function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Esempi
 Esempio di codice seguente viene illustrato come eseguire il cast di un oggetto a un tipo specifico in un progetto Visual Basic in cui **Option Strict** si trova in. In questo tipo di progetto, è necessario il cast esplicito di <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> proprietà su un <xref:Microsoft.Office.Interop.Excel.Range>. Questo esempio richiede un progetto di Excel a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 Esempio di codice seguente viene illustrato come eseguire il cast implicito un oggetto a un tipo specifico in un progetto Visual Basic in cui **Option Strict** sia disattivato o in un oggetto visivo C# progetto che usi il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questi tipi di progetti, la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> proprietà viene eseguito il cast implicito a un <xref:Microsoft.Office.Interop.Excel.Range>. Questo esempio richiede un progetto di Excel a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Accedere ai membri che sono disponibili solo tramite l'associazione tardiva
 Alcune proprietà e metodi in assembly di interoperabilità primari di Office sono disponibili solo tramite l'associazione tardiva. Nei progetti Visual Basic dove **Option Strict** sia disattivato o nell'oggetto visivo C# progetti destinati il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o il [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], è possibile usare le funzionalità di associazione tardiva nelle lingue seguenti per accedere ai membri di associazione tardiva. Nei progetti Visual Basic dove **Option Strict** è on, è necessario usare la reflection per accedere a questi membri.

### <a name="examples"></a>Esempi
 Esempio di codice seguente viene illustrato come accedere ai membri di associazione tardiva in un progetto Visual Basic in cui **Option Strict** sia disattivato o in un oggetto visivo C# progetto che usi il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. L'esempio accede l'associazione tardiva **Name** proprietà del **Apri File** finestra di dialogo di Word. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe in un progetto di Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Esempio di codice seguente viene illustrato come usare la reflection per eseguire la stessa attività in un progetto Visual Basic in cui **Option Strict** si trova in.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vedere anche
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Uso del tipo dinamico &#40;C&#35; Guida alla programmazione&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
