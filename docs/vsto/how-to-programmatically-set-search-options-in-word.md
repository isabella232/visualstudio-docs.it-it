---
title: 'Procedura: Impostare le opzioni di ricerca a livello di codice in Word'
description: Informazioni su come usare Visual Studio per impostare a livello di codice le opzioni di ricerca per le selezioni in Microsoft Word.
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
ms.openlocfilehash: c96533e9b6adf6367a8980f8315f84cc1c3ffe24cc8177ba799983e03bd9852e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394225"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedura: Impostare le opzioni di ricerca a livello di codice in Word
  Esistono due modi per impostare le opzioni di ricerca per le selezioni nei documenti Microsoft Office Word:

- Impostare singole proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.

- Usare gli argomenti del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un oggetto <xref:Microsoft.Office.Interop.Word.Find> .

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usare le proprietà di un oggetto Find
 Il codice seguente imposta le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, il ritorno a capo e il testo da cercare, sono proprietà <xref:Microsoft.Office.Interop.Word.Find> dell'oggetto .

 L'impostazione di ognuna delle proprietà dell'oggetto non è utile quando si scrive codice C#, perché è necessario specificare le stesse proprietà dei <xref:Microsoft.Office.Interop.Word.Find> parametri nel <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo . Questo esempio contiene quindi solo Visual Basic codice.

### <a name="to-set-search-options-using-a-find-object"></a>Per impostare le opzioni di ricerca usando un oggetto Find

1. Impostare le proprietà di un oggetto per cercare in avanti una selezione <xref:Microsoft.Office.Interop.Word.Find> per il testo find **me**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Usare gli argomenti del metodo Execute
 Il codice seguente usa il <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un oggetto per cercare testo <xref:Microsoft.Office.Interop.Word.Find> all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, il ritorno a capo e il testo da cercare, vengono passati come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Per impostare le opzioni di ricerca usando gli argomenti del metodo Execute

1. Passare i criteri di ricerca come parametri del metodo per eseguire la ricerca <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> in avanti tramite una selezione del testo find **me**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: Eseguire un ciclo a livello di codice tra gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
