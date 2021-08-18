---
title: Convalida dei punti di interruzione in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come eseguire l'override del metodo ValidateBreakpointLocation in un servizio di linguaggio legacy per convalidare i punti di interruzione prima dell'avvio del debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 29ab2cc7d33dc4ec94759fce2ddb9d2335688ed4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034539"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Convalida dei punti di interruzione in un servizio di linguaggio legacy
Un punto di interruzione indica che l'esecuzione del programma deve essere interrotta in un determinato punto mentre è in esecuzione in un debugger. Un utente può inserire un punto di interruzione in qualsiasi riga del file di origine, poiché l'editor non è a conoscenza di ciò che costituisce una posizione valida per un punto di interruzione. All'avvio del debugger, tutti i punti di interruzione contrassegnati (denominati punti di interruzione in sospeso) vengono associati alla posizione appropriata nel programma in esecuzione. Allo stesso tempo, i punti di interruzione vengono convalidati per assicurarsi che contrassegnino percorsi di codice validi. Ad esempio, un punto di interruzione in un commento non è valido perché non è presente codice in tale posizione nel codice sorgente. Il debugger disabilita i punti di interruzione non validi.

 Poiché il servizio di linguaggio è a conoscenza del codice sorgente visualizzato, può convalidare i punti di interruzione prima dell'avvio del debugger. È possibile eseguire l'override <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> del metodo per restituire un intervallo che specifica una posizione valida per un punto di interruzione. La posizione del punto di interruzione viene comunque convalidata all'avvio del debugger, ma l'utente viene informato dei punti di interruzione non validi senza attendere il caricamento del debugger.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementazione del supporto per la convalida dei punti di interruzione

- Al <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo viene data la posizione del punto di interruzione. L'implementazione deve decidere se la posizione è valida e indicarlo tramite la restituzione di un intervallo di testo che identifica il codice associato alla posizione della riga del punto di interruzione.

- Restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> se il percorso è valido o se non è <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> valido.

- Se il punto di interruzione è valido, l'intervallo di testo viene evidenziato insieme al punto di interruzione.

- Se il punto di interruzione non è valido, sulla barra di stato viene visualizzato un messaggio di errore.

### <a name="example"></a>Esempio
 In questo esempio viene illustrata un'implementazione del metodo che chiama il parser per ottenere l'eventuale intervallo di codice <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> nella posizione specificata.

 In questo esempio si presuppone che sia stato aggiunto un metodo alla classe che convalida l'intervallo di testo e restituisce se si tratta di una posizione `GetCodeSpan` valida del punto di <xref:Microsoft.VisualStudio.Package.AuthoringSink> `true` interruzione.

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

## <a name="see-also"></a>Vedi anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
