---
title: 'Procedura: Impostare le opzioni di ricerca in Word a livello di codice'
description: Informazioni su come usare Visual Studio per impostare le opzioni di ricerca per le selezioni in Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8916affc89cdf179cf3981e5900d155731ded6c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046438"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedura: Impostare le opzioni di ricerca in Word a livello di codice
  Esistono due modi per impostare le opzioni di ricerca per le selezioni Microsoft Office documenti di Word:

- Impostare le singole proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto .

- Usare gli argomenti del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un oggetto <xref:Microsoft.Office.Interop.Word.Find> .

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usare le proprietà di un oggetto Find
 Nel codice seguente vengono impostate le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per la ricerca di testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, il ritorno a capo e il testo da cercare, sono proprietà <xref:Microsoft.Office.Interop.Word.Find> dell'oggetto .

 L'impostazione di ognuna delle proprietà dell'oggetto non è utile quando si scrive codice C# perché è necessario specificare le stesse proprietà <xref:Microsoft.Office.Interop.Word.Find> dei parametri nel metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> . Di conseguenza, questo esempio contiene solo Visual Basic codice.

### <a name="to-set-search-options-using-a-find-object"></a>Per impostare le opzioni di ricerca usando un oggetto Find

1. Impostare le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per eseguire la ricerca in avanti in una selezione del testo **trovami**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Usare gli argomenti del metodo Execute
 Nel codice seguente viene utilizzato il <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un oggetto per cercare testo all'interno della selezione <xref:Microsoft.Office.Interop.Word.Find> corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, il ritorno a capo e il testo da cercare, vengono passati come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Per impostare le opzioni di ricerca usando gli argomenti del metodo Execute

1. Passare i criteri di ricerca come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo per eseguire la ricerca in avanti tramite una selezione del testo find **me**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: Scorrere a livello di codice gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
