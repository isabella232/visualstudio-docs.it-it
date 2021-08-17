---
title: Riformattazione del codice in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sull'abilitazione del supporto per la riformattazione del codice sorgente per Visual Studio servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0af9dc7bf25e448a1e5a128276f55016a1049db49f55e14689fce9a6e8376972
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414493"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Riformattazione del codice in un servizio di linguaggio legacy

Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] codice sorgente è possibile riformattare normalizzando l'uso di rientri e spazi vuoti. Ciò può includere l'inserimento o la rimozione di spazi o tabulazioni all'inizio di ogni riga, l'aggiunta di nuove righe tra le righe o la sostituzione di spazi con tabulazioni o tabulazioni con spazi.

> [!NOTE]
> L'inserimento o l'eliminazione di caratteri di nuova riga può influire sui marcatori, ad esempio punti di interruzione e segnalibri, ma l'aggiunta o la rimozione di spazi o tabulazioni non influisce sui marcatori.

Gli utenti possono avviare un'operazione di riformattazione selezionando **Formatta** selezione o **Formatta** documento dal **menu** **Avanzate** del menu Modifica. Un'operazione di riformattazione può essere attivata anche quando viene inserito un frammento di codice o un particolare carattere. Ad esempio, quando si digita una parentesi graffa di chiusura in C#, tutti gli elementi compresi tra la parentesi graffa aperta corrispondente e la parentesi graffa di chiusura vengono automaticamente rientrati al livello appropriato.

Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] invia il comando **Formatta selezione** o **Formatta** documento al servizio di linguaggio, la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chiama il metodo nella classe <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> <xref:Microsoft.VisualStudio.Package.Source> . Per supportare la formattazione, è necessario eseguire <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> l'override del metodo e fornire il proprio codice di formattazione.

## <a name="enabling-support-for-reformatting"></a>Abilitazione del supporto per la riformattazione

Per supportare la `EnableFormatSelection` formattazione, il parametro di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> deve essere impostato su quando si registra il pacchetto `true` VSPackage. In questo modo la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> proprietà viene impostata su `true` . Il <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> metodo restituisce il valore di questa proprietà. Se restituisce true, la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chiama <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Implementazione della riformattazione

Per implementare la riformattazione, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override del <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo . <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>L'oggetto descrive l'intervallo da formattare e <xref:Microsoft.VisualStudio.Package.EditArray> l'oggetto contiene le modifiche apportate all'intervallo. Si noti che questo intervallo può essere l'intero documento. Tuttavia, poiché è probabile che siano state apportate più modifiche all'intervallo, tutte le modifiche devono essere reversibili in una singola azione. A tale scopo, eseguire il wrapping di tutte le modifiche in un <xref:Microsoft.VisualStudio.Package.CompoundAction> oggetto (vedere la sezione "Uso della classe CompoundAction" in questo argomento).

### <a name="example"></a>Esempio

Nell'esempio seguente viene garantito che sia presente uno spazio singolo dopo ogni virgola nella selezione, a meno che la virgola non sia seguita da una tabulazione o non sia alla fine della riga. Gli spazi finali dopo l'ultima virgola in una riga vengono eliminati. Vedere la sezione "Uso della classe CompoundAction" in questo argomento per vedere come questo metodo viene chiamato dal <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Uso della classe CompoundAction

Tutte le riformattazioni eseguite in una sezione di codice devono essere reversibili in una singola azione. Questa operazione può essere eseguita usando una <xref:Microsoft.VisualStudio.Package.CompoundAction> classe . Questa classe esegue il wrapping di un set di operazioni di modifica nel buffer di testo in una singola operazione di modifica.

### <a name="example"></a>Esempio

Di seguito è riportato un esempio di come usare la <xref:Microsoft.VisualStudio.Package.CompoundAction> classe . Vedere l'esempio nella sezione "Implementazione del supporto per la formattazione" in questo argomento per un esempio del `DoFormatting` metodo .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche

- [Funzionalità dei servizi di linguaggio legacy](legacy-language-service-features1.md)
