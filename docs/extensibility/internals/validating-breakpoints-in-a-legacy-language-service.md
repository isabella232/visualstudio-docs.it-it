---
title: Convalida di punti di interruzione in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come è possibile eseguire l'override del metodo ValidateBreakpointLocation in un servizio di linguaggio legacy per convalidare i punti di interruzione prima dell'avvio del debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d48db7397e2f9a5921315036bea15551fb7baa9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488024"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Convalida dei punti di interruzione in un servizio di linguaggio legacy
Un punto di interruzione indica che l'esecuzione del programma dovrebbe arrestarsi in un determinato punto mentre è in esecuzione in un debugger. Un utente può inserire un punto di interruzione in qualsiasi riga del file di origine, poiché l'editor non è a conoscenza di ciò che costituisce una posizione valida per un punto di interruzione. Quando viene avviato il debugger, tutti i punti di interruzione contrassegnati (detti punti di interruzione in sospeso) vengono associati alla posizione appropriata nel programma in esecuzione. Allo stesso tempo, i punti di interruzione vengono convalidati per assicurarsi di contrassegnare percorsi di codice validi. Ad esempio, un punto di interruzione in un commento non è valido perché non esiste alcun codice in tale posizione nel codice sorgente. Il debugger Disabilita i punti di interruzione non validi.

 Poiché il servizio di linguaggio è a conoscenza del codice sorgente visualizzato, può convalidare i punti di interruzione prima di avviare il debugger. È possibile eseguire l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo per restituire un intervallo che specifica una posizione valida per un punto di interruzione. Il percorso del punto di interruzione viene ancora convalidato all'avvio del debugger, ma l'utente riceve una notifica dei punti di interruzione non validi senza attendere il caricamento del debugger.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementazione del supporto per la convalida dei punti di interruzione

- Al <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo viene assegnata la posizione del punto di interruzione. L'implementazione deve decidere se il percorso è valido e indicarlo restituendo un intervallo di testo che identifica il codice associato alla posizione della riga del punto di interruzione.

- Restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> se il percorso è valido o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> se non è valido.

- Se il punto di interruzione è valido, l'intervallo di testo viene evidenziato insieme al punto di interruzione.

- Se il punto di interruzione non è valido, nella barra di stato viene visualizzato un messaggio di errore.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo che chiama il parser per ottenere l'intervallo di codice, se presente, nella posizione specificata.

 In questo esempio si presuppone che sia stato aggiunto un `GetCodeSpan` metodo alla <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe che convalida l'intervallo di testo e restituisce `true` se si tratta di una posizione di punto di interruzione valida.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Vedere anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
