---
title: Supporto per la finestra auto in un servizio di linguaggio legacy | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704889"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio legacy
Nella finestra **auto** vengono visualizzate espressioni come variabili e parametri nell'ambito quando il programma di cui è in corso il debug viene sospeso (a causa di un punto di interruzione o di un'eccezione). Le espressioni possono includere variabili, locali o globali e parametri modificati nell'ambito locale. La finestra **auto** può includere anche le creazioni di istanze di una classe, di una struttura o di un altro tipo. Qualsiasi elemento che può essere valutato da un analizzatore di espressioni può essere potenzialmente visualizzato nella finestra **auto** .

 Il Framework di pacchetto gestito (MPF) non fornisce il supporto diretto per la finestra **auto** . Tuttavia, se si esegue l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo, è possibile restituire un elenco di espressioni da presentare nella finestra **auto** .

## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra auto
 Per supportare la finestra **auto** è sufficiente implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe. L'implementazione deve decidere, data una posizione nel file di origine, in cui le espressioni devono essere visualizzate nella finestra **auto** . Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Un valore restituito di <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica che l'elenco contiene espressioni, mentre <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica che non sono presenti espressioni da visualizzare.

 Le espressioni effettive restituite sono i nomi delle variabili o dei parametri visualizzati in tale posizione nel codice. Questi nomi vengono passati all'analizzatore di espressioni per ottenere i valori e i tipi che vengono quindi visualizzati nella finestra **auto** .

### <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo che ottiene un elenco di espressioni dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo utilizzando il motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Ogni espressione viene racchiusa come oggetto `TestVsEnumBSTR` che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaccia.

 Si noti che `GetAutoExpressionsCount` i `GetAutoExpression` metodi e sono metodi personalizzati per l' `TestAuthoringSink` oggetto e sono stati aggiunti per supportare questo esempio. Rappresentano un modo in cui è possibile accedere alle espressioni aggiunte all' `TestAuthoringSink` oggetto dal parser (chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metodo) all'esterno del parser.

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
