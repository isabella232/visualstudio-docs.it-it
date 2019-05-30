---
title: Supporto per la finestra Auto in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2842cb7a11765f0d460681dee0187c62ff31061c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309832"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio legacy
Il **Auto** finestra vengono visualizzate le espressioni, ad esempio variabili e parametri che rientrano nell'ambito quando il programma in fase di debug viene sospeso (a causa di un punto di interruzione o un'eccezione). Le espressioni possono includere variabili, locali o globali e i parametri che sono stati modificati nell'ambito locale. Il **Auto** finestra può includere anche le creazioni di istanze di una classe, struttura o un altro tipo. Tutto ciò che un analizzatore di espressioni può valutare potenzialmente possono essere visualizzati nei **Auto** finestra.

 Il framework di pacchetto gestito (MPF) è incluso alcun supporto diretto per il **Auto** finestra. Tuttavia, se esegue l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo, è possibile restituire un elenco delle espressioni devono essere presentati nel **Auto** finestra.

## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra Auto
 È sufficiente per supportare le **Auto** finestra consiste nell'implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Occorre decidere se l'implementazione, dato un percorso nel file di origine, le espressioni devono visualizzare nel **Auto** finestra. Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Un valore restituito pari <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica che l'elenco contiene espressioni, anche se <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica che non sono presenti espressioni da visualizzare.

 Le espressioni effettive restituite sono i nomi delle variabili o parametri che vengono visualizzati in tale posizione nel codice. Questi nomi vengono passati per l'analizzatore di espressioni per ottenere i valori e tipi che vengono quindi visualizzati nei **Auto** finestra.

### <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo che ottiene un elenco di espressioni dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo utilizzando il motivo per l'analisi <xref:Microsoft.VisualStudio.Package.ParseReason>. Ciascuna delle espressioni viene inclusa come un `TestVsEnumBSTR` che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaccia.

 Si noti che il `GetAutoExpressionsCount` e `GetAutoExpression` metodi sono metodi personalizzati nel `TestAuthoringSink` dell'oggetto e sono stati aggiunti per supportare questo esempio. Rappresentano un modo nel quale le espressioni aggiunte alle `TestAuthoringSink` oggetto dal parser (chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> (metodo)) è accessibile di fuori del parser.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
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
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
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