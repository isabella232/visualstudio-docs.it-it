---
title: 'Procedura: impostare le opzioni di ricerca in Word a livello di codice'
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
ms.workload:
- office
ms.openlocfilehash: e583b7deb9fbe37f40e582d2c8a946332dd00ffa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913461"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedura: impostare le opzioni di ricerca in Word a livello di codice
  Esistono due modi per impostare le opzioni di ricerca per le selezioni nei documenti Microsoft Office Word:

- Impostare le singole proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.

- Usare gli argomenti del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usare le proprietà di un oggetto Find
 Il codice seguente imposta le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto in modo da cercare il testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in anticipo, il ritorno a capo e il testo da cercare, sono proprietà dell' <xref:Microsoft.Office.Interop.Word.Find> oggetto.

 L'impostazione di ognuna delle proprietà dell' <xref:Microsoft.Office.Interop.Word.Find> oggetto non è utile quando si scrive codice C# perché è necessario specificare le stesse proprietà dei parametri nel <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo. Questo esempio contiene quindi solo Visual Basic codice.

### <a name="to-set-search-options-using-a-find-object"></a>Per impostare le opzioni di ricerca usando un oggetto Find

1. Consente di impostare le proprietà di un oggetto in modo che esegua la <xref:Microsoft.Office.Interop.Word.Find> ricerca tramite una selezione per il testo **Find me**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Usare gli argomenti del metodo Execute
 Il codice seguente usa il <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare il testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in anticipo, il ritorno a capo e il testo da ricercare, vengono passati come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Per impostare le opzioni di ricerca utilizzando gli argomenti del metodo Execute

1. Passare i criteri di ricerca come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo per eseguire la ricerca in un secondo momento tramite una selezione per il testo **Find me**.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Vedi anche
- [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: scorrere in ciclo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)
