---
title: Parametri facoltativi nelle soluzioni Office
description: Informazioni su come non è necessario passare un valore per i parametri facoltativi perché i valori predefiniti vengono usati automaticamente per ogni parametro mancante.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c95842ac2c6d77a2312ac5c4c197ba22ed2020e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825420"
---
# <a name="optional-parameters-in-office-solutions"></a>Parametri facoltativi nelle soluzioni Office
  Molti dei metodi nei modelli a oggetti delle applicazioni di Microsoft Office accettano parametri facoltativi. Se si utilizza Visual Basic per sviluppare una soluzione Office in Visual Studio, non è necessario passare un valore per i parametri facoltativi. Infatti, per ogni parametro mancante vengono utilizzati automaticamente i valori predefiniti. Nella maggior parte dei casi, è anche possibile omettere i parametri facoltativi nei progetti Visual C#. Non è tuttavia possibile omettere parametri **ref** facoltativi della `ThisDocument` classe nei progetti Word a livello di documento.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per altre informazioni sull'uso dei parametri facoltativi nei progetti Visual C# e Visual Basic, vedere Argomenti denominati e facoltativi [&#40;C&#35; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) guida per la programmazione&#41;e Parametri [facoltativi &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).

> [!NOTE]
> Nelle versioni precedenti di Visual Studio è necessario passare un valore per ogni parametro facoltativo nei progetti Visual C#. Per comodità, questi progetti includono una variabile globale denominata `missing` che è possibile passare a un parametro facoltativo quando si desidera utilizzare il valore predefinito del parametro. I progetti Visual C# per Office in Visual Studio includono comunque la variabile , ma in genere non è necessario usarla quando si sviluppano soluzioni Office in , tranne quando si chiamano metodi con parametri ref facoltativi nella classe nei progetti a livello di documento per `missing` [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]  `ThisDocument` Word.

## <a name="example-in-excel"></a>Esempio in Excel
 Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito. In questo esempio è richiesto un progetto a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Esempio in Word
 Il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Usare parametri facoltativi dei metodi nella classe ThisDocument nei progetti a livello di documento di Visual C# per Word
 Il modello a oggetti di Word contiene molti metodi con parametri **ref** facoltativi che accettano <xref:System.Object> valori. Tuttavia, non è possibile omettere parametri **di** riferimento facoltativi dei metodi della classe generata nei progetti a livello di documento `ThisDocument` di Visual C# per Word. Visual C# consente di omettere parametri **di riferimento** facoltativi solo per i metodi delle interfacce, non per le classi. Ad esempio, l'esempio di codice seguente non viene compilato, perché non è possibile omettere parametri **ref** facoltativi del <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodo della classe `ThisDocument` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 Quando si chiamano metodi della classe `ThisDocument`, attenersi le linee guida seguenti:

- Per accettare il valore predefinito di un parametro **ref** facoltativo, passare la `missing` variabile al parametro . La variabile `missing` viene definita automaticamente nei progetti Office di Visual C# e viene assegnata al valore <xref:System.Type.Missing> nel codice di progetto generato.

- Per specificare un valore personalizzato per un parametro **di** riferimento facoltativo, dichiarare un oggetto assegnato al valore che si desidera specificare e quindi passare l'oggetto al parametro .

  Nell'esempio di codice seguente viene illustrato come chiamare il metodo specificando un valore per il <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> *parametro ignoreUppercase* e accettando il valore predefinito per gli altri parametri.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  Se si vuole scrivere codice che  omette parametri ref facoltativi di un metodo nella classe, è possibile chiamare in alternativa lo stesso metodo sull'oggetto restituito dalla proprietà e omettere i parametri da tale `ThisDocument` <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> metodo. È possibile eseguire questa operazione perché <xref:Microsoft.Office.Interop.Word.Document> è un'interfaccia, non una classe.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Per altre informazioni sui parametri di tipo valore e riferimento, vedere Passare argomenti per valore e per &#40;Visual Basic&#41;di riferimento [(per ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) Visual Basic) e Passare parametri [&#40;C&#35; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)&#41;.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
