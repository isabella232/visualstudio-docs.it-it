---
title: Associazione tardiva nelle soluzioni Office
description: Informazioni sul modo in cui alcuni tipi nei modelli a oggetti all'interno di Microsoft Office applicazioni forniscono funzionalità disponibili tramite le funzionalità di associazione tardiva.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 201b850d8a577f8cc76aff97e2370998b6f885ed
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523565"
---
# <a name="late-binding-in-office-solutions"></a>Associazione tardiva nelle soluzioni Office
  Alcuni tipi nei modelli a oggetti delle applicazioni di Office forniscono funzionalità disponibili tramite le funzionalità di associazione tardiva. Alcuni metodi e proprietà, ad esempio, possono restituire tipi diversi di oggetti a seconda del contesto dell'applicazione di Office e alcuni tipi possono esporre metodi o proprietà diversi in contesti diversi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic progetti in cui **Option Strict** è disattivato e i progetti Visual C# destinati [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] possono funzionare direttamente con i tipi che usano queste funzionalità di associazione tardiva.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Cast implicito ed esplicito dei valori restituiti dell'oggetto
 Molti metodi e proprietà in Microsoft Office gli assembly di interoperabilità primari (PIA) restituiscono <xref:System.Object> valori, perché possono restituire diversi tipi di oggetti. Ad esempio, la <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> proprietà restituisce un <xref:System.Object> oggetto perché il valore restituito può essere <xref:Microsoft.Office.Interop.Excel.Worksheet> un <xref:Microsoft.Office.Interop.Excel.Chart> oggetto o, a seconda del foglio attivo.

 Quando un metodo o una proprietà restituisce un <xref:System.Object> oggetto, è necessario convertire in modo esplicito (in Visual Basic) l'oggetto nel tipo corretto nei progetti Visual Basic in cui **Option Strict** è on. Non è necessario eseguire il cast esplicito <xref:System.Object> dei valori restituiti nei progetti Visual Basic in cui **Option Strict** è disattivato.

 Nella maggior parte dei casi, nella documentazione di riferimento sono elencati i possibili tipi del valore restituito per un membro che restituisce <xref:System.Object> . La conversione o il cast dell'oggetto Abilita IntelliSense per l'oggetto nell'editor di codice.

 Per informazioni sulla conversione in Visual Basic, vedere [conversioni implicite ed esplicite &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e la [funzione CType &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;.

### <a name="examples"></a>Esempi
 Nell'esempio di codice riportato di seguito viene illustrato come eseguire il cast di un oggetto a un tipo specifico in un progetto Visual Basic in cui **Option Strict** è on. In questo tipo di progetto, è necessario eseguire il cast esplicito della <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> proprietà a un oggetto <xref:Microsoft.Office.Interop.Excel.Range> . Questo esempio richiede un progetto di Excel a livello di documento con una classe Worksheet denominata `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 Nell'esempio di codice seguente viene illustrato come eseguire il cast implicito di un oggetto a un tipo specifico in un progetto Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual C# destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In questi tipi di progetti, <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> viene eseguito il cast implicito della proprietà a un oggetto <xref:Microsoft.Office.Interop.Excel.Range> . Questo esempio richiede un progetto di Excel a livello di documento con una classe Worksheet denominata `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Accesso ai membri disponibili solo tramite associazione tardiva
 Alcune proprietà e metodi negli assembly di interoperabilità primari di Office sono disponibili solo tramite associazione tardiva. Nei progetti Visual Basic in cui **Option Strict** è disattivato o nei progetti Visual C# destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , è possibile usare le funzionalità di associazione tardiva in questi linguaggi per accedere ai membri ad associazione tardiva. Nei progetti Visual Basic in cui **Option Strict** è impostata su on, è necessario utilizzare la reflection per accedere a questi membri.

### <a name="examples"></a>Esempi
 Nell'esempio di codice riportato di seguito viene illustrato come accedere a membri ad associazione tardiva in un progetto Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual C# destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Questo esempio accede alla proprietà **nome** ad associazione tardiva della finestra di dialogo **Apri file** in Word. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` in un progetto di Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare la reflection per eseguire la stessa attività in un progetto Visual Basic in cui **Option Strict** è on.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vedere anche
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Usare la Guida di programmazione di tipo Dynamic &#40;C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
