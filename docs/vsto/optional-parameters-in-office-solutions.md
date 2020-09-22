---
title: Parametri facoltativi nelle soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8684ad4b9429a5499660ef4ad6fdd8133dccaa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839931"
---
# <a name="optional-parameters-in-office-solutions"></a>Parametri facoltativi nelle soluzioni Office
  Molti dei metodi nei modelli a oggetti delle applicazioni di Microsoft Office accettano parametri facoltativi. Se si utilizza Visual Basic per sviluppare una soluzione Office in Visual Studio, non è necessario passare un valore per i parametri facoltativi. Infatti, per ogni parametro mancante vengono utilizzati automaticamente i valori predefiniti. Nella maggior parte dei casi, è anche possibile omettere i parametri facoltativi nei progetti Visual C#. Tuttavia, non è possibile omettere i parametri di **riferimento** facoltativi della `ThisDocument` classe nei progetti Word a livello di documento.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per ulteriori informazioni sull'utilizzo dei parametri facoltativi nei progetti Visual C# e Visual Basic, vedere [argomenti denominati e facoltativi &#40;Guida alla programmazione di&#35; C&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) e [parametri facoltativi &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> Nelle versioni precedenti di Visual Studio è necessario passare un valore per ogni parametro facoltativo nei progetti Visual C#. Per comodità, questi progetti includono una variabile globale denominata `missing` che è possibile passare a un parametro facoltativo quando si desidera utilizzare il valore predefinito del parametro. I progetti Visual C# per Office in Visual Studio includono ancora la `missing` variabile, ma in genere non è necessario usarla quando si sviluppano soluzioni Office in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , eccetto quando si chiamano metodi con parametri **ref** facoltativi nella `ThisDocument` classe nei progetti a livello di documento per Word.

## <a name="example-in-excel"></a>Esempio in Excel
 Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito. In questo esempio è richiesto un progetto a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Esempio in Word
 Il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito.

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Usare i parametri facoltativi dei metodi nella classe ThisDocument nei progetti a livello di documento di Visual C# per Word
 Il modello a oggetti di Word contiene molti metodi con parametri di **riferimento** facoltativi che accettano <xref:System.Object> valori. Tuttavia, non è possibile omettere i parametri di **riferimento** facoltativi dei metodi della `ThisDocument` classe generata nei progetti a livello di documento di Visual C# per Word. Visual C# consente di omettere i parametri di **riferimento** facoltativi solo per i metodi delle interfacce, non per le classi. Ad esempio, l'esempio di codice seguente non viene compilato, perché non è possibile omettere i parametri di **riferimento** facoltativi del <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodo della `ThisDocument` classe.

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 Quando si chiamano metodi della classe `ThisDocument`, attenersi le linee guida seguenti:

- Per accettare il valore predefinito di un parametro **ref** facoltativo, passare la `missing` variabile al parametro. La variabile `missing` viene definita automaticamente nei progetti Office di Visual C# e viene assegnata al valore <xref:System.Type.Missing> nel codice di progetto generato.

- Per specificare un valore personalizzato per un parametro **ref** facoltativo, dichiarare un oggetto assegnato al valore che si desidera specificare, quindi passare l'oggetto al parametro.

  Nell'esempio di codice seguente viene illustrato come chiamare il <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodo specificando un valore per il parametro *IgnoreUppercase* e accettando il valore predefinito per gli altri parametri.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  Se si desidera scrivere codice che omette parametri **ref** facoltativi di un metodo nella `ThisDocument` classe, è possibile chiamare in alternativa lo stesso metodo sull' <xref:Microsoft.Office.Interop.Word.Document> oggetto restituito dalla <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> proprietà e omettere i parametri da tale metodo. È possibile eseguire questa operazione perché <xref:Microsoft.Office.Interop.Word.Document> è un'interfaccia, non una classe.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  Per altre informazioni sui parametri di tipo value e Reference, vedere [passare gli argomenti per valore e per riferimento &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (per Visual Basic) e [passare i parametri &#40;C&#35; guida alla programmazione&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
