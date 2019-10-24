---
title: Riformattazione del codice in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae48e1b97b5c9194cf3081687ab31ea9f857e6c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724762"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Riformattazione del codice in un servizio di linguaggio legacy

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] codice sorgente può essere riformattato normalizzando l'uso dei rientri e degli spazi vuoti. Ciò può includere l'inserimento o la rimozione di spazi o tabulazioni all'inizio di ogni riga, l'aggiunta di nuove righe tra le linee o la sostituzione di spazi con tabulazioni o tabulazioni con spazi.

> [!NOTE]
> L'inserimento o l'eliminazione di caratteri di nuova riga può influire su marcatori quali punti di interruzione e segnalibri, ma l'aggiunta o la rimozione di spazi o tabulazioni non influisce sui marcatori

Gli utenti possono avviare un'operazione di riformattazione selezionando **Formatta selezione** o **Formatta documento** dal menu **Avanzate** del menu **modifica** . Un'operazione di riformattazione può essere attivata anche quando viene inserito un frammento di codice o un particolare carattere. Ad esempio, quando si digita una parentesi graffa di chiusura C#in, tutto ciò che intercorre tra la parentesi graffa di apertura corrispondente e la parentesi graffa di chiusura viene rientrato automaticamente al livello corretto.

Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] invia il comando **Format Selection** o **Format Document** al servizio di linguaggio, la classe <xref:Microsoft.VisualStudio.Package.ViewFilter> chiama il metodo <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> nella classe <xref:Microsoft.VisualStudio.Package.Source>. Per supportare la formattazione, è necessario eseguire l'override del metodo <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> e fornire il proprio codice di formattazione.

## <a name="enabling-support-for-reformatting"></a>Abilitazione del supporto per la riformattazione

Per supportare la formattazione, è necessario impostare il parametro `EnableFormatSelection` del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> su `true` quando si registra il pacchetto VSPackage. In questo modo la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> viene impostata su `true`. Il metodo <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> restituisce il valore di questa proprietà. Se restituisce true, la classe <xref:Microsoft.VisualStudio.Package.ViewFilter> chiama l'<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

## <a name="implementing-reformatting"></a>Implementazione della riformattazione

Per implementare la riformattazione, è necessario derivare una classe dalla classe <xref:Microsoft.VisualStudio.Package.Source> ed eseguire l'override del metodo <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>. L'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> descrive l'intervallo da formattare e l'oggetto <xref:Microsoft.VisualStudio.Package.EditArray> contiene le modifiche apportate sull'intervallo. Si noti che questo intervallo può essere l'intero documento. Tuttavia, poiché è probabile che siano state apportate più modifiche all'intervallo, tutte le modifiche devono essere reversibili in un'unica azione. A tale scopo, eseguire il wrapping di tutte le modifiche in un oggetto <xref:Microsoft.VisualStudio.Package.CompoundAction> (vedere la sezione "uso della classe CompoundAction" in questo argomento).

### <a name="example"></a>Esempio

Nell'esempio seguente viene verificato che sia presente un solo spazio dopo ogni virgola nella selezione, a meno che la virgola non sia seguita da una scheda o si trovi alla fine della riga. Gli spazi finali dopo l'ultima virgola in una riga vengono eliminati. Vedere la sezione "uso della classe CompoundAction" in questo argomento per vedere come viene chiamato questo metodo dal metodo <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

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

Tutte le riformattazioni eseguite in una sezione di codice devono essere reversibili in un'unica azione. Questa operazione può essere eseguita usando una classe <xref:Microsoft.VisualStudio.Package.CompoundAction>. Questa classe esegue il wrapping di un set di operazioni di modifica nel buffer di testo in una singola operazione di modifica.

### <a name="example"></a>Esempio

Di seguito è riportato un esempio di come usare la classe <xref:Microsoft.VisualStudio.Package.CompoundAction>. Vedere l'esempio nella sezione "implementazione del supporto per la formattazione" in questo argomento per un esempio del metodo `DoFormatting`.

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