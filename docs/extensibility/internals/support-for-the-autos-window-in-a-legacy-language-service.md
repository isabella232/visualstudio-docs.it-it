---
title: Supporto per la finestra Auto in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704889"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio legacy
Nella finestra **Auto** vengono visualizzate espressioni quali variabili e parametri inclusi nell'ambito quando il programma in fase di debug viene sospeso (a causa di un punto di interruzione o di un'eccezione). Le espressioni possono includere variabili, locali o globali, e parametri che sono stati modificati nell'ambito locale. La finestra **Auto** può includere anche istanze di una classe, una struttura o un altro tipo. Tutto ciò che un analizzatore di espressioni può valutare può essere potenzialmente visualizzato nella finestra **Auto.**

 Il framework del pacchetto gestito (MPF) non fornisce supporto diretto per la finestra **Auto.** Tuttavia, se <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> si esegue l'override del metodo, è possibile restituire un elenco di espressioni da presentare nella finestra **Auto.**

## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra AutoImplementing Support for the Autos Window
 Tutto quello che dovete fare per supportare <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> il <xref:Microsoft.VisualStudio.Package.LanguageService> **Autos** finestra è quello di implementare il metodo nella classe. L'implementazione deve decidere, data una posizione nel file di origine, quali espressioni devono essere visualizzate nella finestra Auto.Your implementation must decide, given a location in the source file, which expressions should appear in the **Autos** window. Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Un valore <xref:Microsoft.VisualStudio.VSConstants.S_OK> restituito di indica che l'elenco contiene espressioni, mentre <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica che non sono presenti espressioni da visualizzare.

 Le espressioni effettive restituite sono i nomi delle variabili o dei parametri visualizzati in tale posizione nel codice. Questi nomi vengono passati all'analizzatore di espressioni per ottenere valori e tipi che vengono quindi visualizzati nella finestra **Auto.**

### <a name="example"></a>Esempio
 Nell'esempio seguente viene <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo che <xref:Microsoft.VisualStudio.Package.ParseReason>ottiene un elenco di espressioni dal metodo utilizzando il motivo dell'analisi . Ognuna delle espressioni viene `TestVsEnumBSTR` eseguito <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> il wrapping come un che implementa l'interfaccia.

 Si noti che i `GetAutoExpressionsCount` metodi e `GetAutoExpression` sono metodi personalizzati sull'oggetto `TestAuthoringSink` e sono stati aggiunti per supportare questo esempio. Rappresentano un modo in cui `TestAuthoringSink` le espressioni aggiunte all'oggetto dal parser (chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metodo ) sono accessibili all'esterno del parser.

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
