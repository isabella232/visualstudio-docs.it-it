---
title: Supportare la finestra Auto in un servizio di linguaggio legacy
description: Informazioni su come implementare il supporto per la finestra Auto, che visualizza le espressioni nell'ambito quando il programma in fase di debug viene sospeso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d91cad3e47ca664cfb1f41215da3197774e3840e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086586"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio legacy

La **finestra Auto visualizza** espressioni come variabili e parametri che si trova nell'ambito quando il programma in fase di debug viene sospeso (a causa di un punto di interruzione o di un'eccezione). Le espressioni possono includere variabili, locali o globali e parametri che sono stati modificati nell'ambito locale. La **finestra Auto può** includere anche le istanze di una classe, una struttura o un altro tipo. Tutto ciò che un analizzatore di espressioni può valutare può essere potenzialmente visualizzato nella **finestra Auto.**

 Il framework del pacchetto gestito (MPF) non fornisce il supporto diretto per la **finestra Auto.** Tuttavia, se si esegue l'override del metodo , è possibile restituire un elenco di <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> espressioni da presentare nella finestra **Auto.**

## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra Auto

 Per supportare la finestra **Autos** è necessario implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo nella classe <xref:Microsoft.VisualStudio.Package.LanguageService> . L'implementazione deve decidere, dato un percorso nel file di origine, quali espressioni devono essere visualizzate **nella finestra Auto.** Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Il valore restituito di indica che l'elenco contiene espressioni, mentre indica che non sono <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> presenti espressioni da visualizzare.

 Le espressioni effettive restituite sono i nomi delle variabili o dei parametri visualizzati in tale posizione nel codice. Questi nomi vengono passati all'analizzatore di espressioni per ottenere valori e tipi che vengono quindi visualizzati nella **finestra Auto.**

### <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo che ottiene un elenco di espressioni dal metodo usando il motivo di analisi <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> . Ogni espressione viene incapsulata come oggetto che `TestVsEnumBSTR` implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> l'interfaccia .

 Si noti che `GetAutoExpressionsCount` i metodi e sono metodi personalizzati `GetAutoExpression` `TestAuthoringSink` nell'oggetto e sono stati aggiunti per supportare questo esempio. Rappresentano un modo in cui è possibile accedere alle espressioni aggiunte all'oggetto dal parser (chiamando il metodo `TestAuthoringSink` <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> ) all'esterno del parser.

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
