---
title: 'Procedura: A livello di codice impostare le opzioni di ricerca in Word'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7443a4789008f3bb5992695761dff228bd32298
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601408"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedura: A livello di codice impostare le opzioni di ricerca in Word
  Esistono due modi per impostare le opzioni di ricerca per le selezioni in documenti di Microsoft Office Word:

- Impostare singole proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.

- Usare gli argomenti del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usare le proprietà di un oggetto Find
 Il codice seguente imposta le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, ritorno a capo e testo per la ricerca, sono proprietà del <xref:Microsoft.Office.Interop.Word.Find> oggetto.

 Ognuna delle proprietà di impostazione la <xref:Microsoft.Office.Interop.Word.Find> oggetto non è utile quando si scrive codice c# perché è necessario specificare le stesse proprietà dei parametri in di <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (metodo). Pertanto in questo esempio contiene solo il codice Visual Basic.

### <a name="to-set-search-options-using-a-find-object"></a>Per impostare le opzioni di ricerca utilizzando un oggetto di ricerca

1.  Impostare le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto da ricercare in avanti attraverso una selezione per il testo **trovarmi**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Usare gli argomenti del metodo Execute
 Il codice seguente usa il <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, ritorno a capo e testo per la ricerca, vengono passati come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> (metodo).

### <a name="to-set-search-options-using-execute-method-arguments"></a>Per impostare le opzioni di ricerca usando gli argomenti del metodo Execute

1.  Passare ai criteri di ricerca come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo per eseguire la ricerca tramite una selezione per il testo **trovarmi**.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Vedere anche
- [Procedura: Cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: Ciclo a livello di programmazione tramite gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: A livello di programmazione ripristinare le selezioni dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
