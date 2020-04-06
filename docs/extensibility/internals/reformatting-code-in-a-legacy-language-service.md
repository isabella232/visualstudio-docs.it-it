---
title: Riformattazione del codice in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705915"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Riformattazione del codice in un servizio di linguaggio legacy

Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] codice sorgente può essere riformattato normalizzando l'uso di rientri e spazi vuoti. Ciò può includere l'inserimento o la rimozione di spazi o tabulazioni all'inizio di ogni riga, l'aggiunta di nuove righe tra le righe o la sostituzione di spazi con tabulazioni o tabulazioni con spazi.

> [!NOTE]
> L'inserimento o l'eliminazione di caratteri di nuova riga può influire sui marcatori, ad esempio punti di interruzione e segnalibri, ma l'aggiunta o la rimozione di spazi o tabulazioni non influisce sui marcatori.

Gli utenti possono avviare un'operazione di riformattazione scegliendo **Formato selezione** o **Formato documento** dal menu **Avanzate** dal menu **Modifica.** Un'operazione di riformattazione può essere attivata anche quando viene inserito un frammento di codice o un particolare carattere. Ad esempio, quando si digita una parentesi graffa di chiusura in C, tutti gli elementi compresi tra la parentesi graffa aperta corrispondente e la parentesi graffa chiusa vengono automaticamente rientrati al livello corretto.

Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] invia il **comando Format Selection** o Format **Document** al servizio di linguaggio, la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chiama il <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo nella <xref:Microsoft.VisualStudio.Package.Source> classe . Per supportare la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> formattazione è necessario eseguire l'override del metodo e fornire il proprio codice di formattazione.

## <a name="enabling-support-for-reformatting"></a>Abilitazione del supporto per la riformattazione

Per supportare `EnableFormatSelection` la formattazione, il parametro del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> deve essere impostato `true` su quando si registra il pacchetto VSPackage. In questo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> modo `true`la proprietà viene impostata su . Il <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> metodo restituisce il valore di questa proprietà. Se restituisce true, <xref:Microsoft.VisualStudio.Package.ViewFilter> la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>classe chiama il metodo .

## <a name="implementing-reformatting"></a>Implementazione della riformattazioneImplementing Reformatting

Per implementare la <xref:Microsoft.VisualStudio.Package.Source> riformattazione, è necessario <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> derivare una classe dalla classe ed eseguire l'override del metodo. L'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> descrive l'intervallo <xref:Microsoft.VisualStudio.Package.EditArray> da formattare e l'oggetto contiene le modifiche apportate all'intervallo. Si noti che questo intervallo può essere l'intero documento. Tuttavia, poiché è probabile che siano apportate più modifiche all'intervallo, tutte le modifiche devono essere reversibili in una singola azione. A tale scopo, eseguire <xref:Microsoft.VisualStudio.Package.CompoundAction> il wrapping di tutte le modifiche in un oggetto (vedere la sezione "Utilizzo della classe CompoundAction" in questo argomento).

### <a name="example"></a>Esempio

L'esempio seguente garantisce la corrispondenza di ogni virgola dopo ogni virgola nella selezione, a meno che la virgola non sia seguita da una tabulazione o si trova alla fine della riga. Gli spazi finali dopo l'ultima virgola in una riga vengono eliminati. Vedere la sezione "Utilizzo della classe CompoundAction" in questo argomento <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> per vedere come questo metodo viene chiamato dal metodo.

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

## <a name="using-the-compoundaction-class"></a>Utilizzo della classe CompoundAction

Tutte le riformattazioni eseguite su una sezione di codice devono essere reversibili in un'unica azione. Questa operazione può essere <xref:Microsoft.VisualStudio.Package.CompoundAction> eseguita utilizzando una classe. Questa classe esegue il wrapping di un set di operazioni di modifica nel buffer di testo in una singola operazione di modifica.

### <a name="example"></a>Esempio

Ecco un esempio di come <xref:Microsoft.VisualStudio.Package.CompoundAction> usare la classe. Vedere l'esempio nella sezione "Implementazione del supporto per `DoFormatting` la formattazione" in questo argomento per un esempio del metodo.

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

## <a name="see-also"></a>Vedere anche

- [Funzionalità dei servizi di linguaggio legacy](legacy-language-service-features1.md)
