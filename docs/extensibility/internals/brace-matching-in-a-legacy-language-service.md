---
title: Corrispondenza delle parentesi graffe in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulla corrispondenza delle parentesi graffe in un servizio di linguaggio legacy, che consente di tenere traccia degli elementi del linguaggio che devono verificarsi insieme, ad esempio parentesi e parentesi graffe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e63f9c065e629d768e73cc0c9433c4467883597f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159152"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Corrispondenza parentesi graffe in un servizio di linguaggio legacy
La corrispondenza delle parentesi graffe consente allo sviluppatore di tenere traccia degli elementi del linguaggio che devono essere presenti insieme, ad esempio parentesi e parentesi graffe. Quando uno sviluppatore immette una parentesi graffa di chiusura, la parentesi graffa di apertura viene evidenziata.

 È possibile trovare la corrispondenza con due o tre elementi coesistere, denominati coppie e triple. Le triple sono set di tre elementi coesistere. In C#, ad esempio, `foreach` l'istruzione forma una tripla: `foreach()` `{` , e `}` . Tutti e tre gli elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare la corrispondenza delle parentesi graffe, vedere Procedura dettagliata: Visualizzare le [parentesi graffe corrispondenti.](../../extensibility/walkthrough-displaying-matching-braces.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe supporta sia coppie che triple con i metodi e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> .

## <a name="implementation"></a>Implementazione
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in genere eseguita implementando per rilevare una lingua corrispondente e quindi <xref:Microsoft.VisualStudio.Package.IScanner> usando il metodo per trovare le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> corrispondenze con gli elementi.

 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama lo scanner per tokenizzare la riga e restituire il token appena prima del segno di chiodato. Lo scanner indica che è stata trovata una coppia di elementi di linguaggio impostando un valore del trigger del token <xref:Microsoft.VisualStudio.Package.TokenTriggers> su nel token corrente. Il metodo chiama il metodo che a sua volta chiama il metodo con il valore <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> del motivo di analisi di per individuare <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> l'elemento di linguaggio corrispondente. Quando viene trovato l'elemento di linguaggio corrispondente, entrambi gli elementi vengono evidenziati.

 Per una descrizione completa del modo in cui la digitazione di una parentesi graffa attiva l'evidenziazione delle parentesi graffe, vedere la sezione *Esempio* di operazione di analisi nell'articolo Parser e scanner del servizio [di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Abilitare il supporto per la corrispondenza tra parentesi graffe
 L'attributo può impostare le voci del Registro di sistema <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> **MatchBraces**, **MatchBracesAtCaret** e **ShowMatchingBrace** che impostano le proprietà corrispondenti della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe . Le proprietà delle preferenze di lingua possono essere impostate anche dall'utente.

|Voce del Registro di sistema|Proprietà|Descrizione|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Abilita la corrispondenza tra parentesi graffe.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Abilita la corrispondenza delle parentesi graffe quando il cursore si sposta.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|

## <a name="match-conditional-statements"></a>Trovare la corrispondenza con le istruzioni condizionali
 È possibile associare istruzioni condizionali, ad esempio , e o , , , , , allo stesso modo dei `if` `else if` `else` `#if` `#elif` `#else` `#endif` delimitatori corrispondenti. È possibile creare una sottoclasse della classe e fornire un metodo in grado di aggiungere intervalli di testo e delimitatori alla matrice <xref:Microsoft.VisualStudio.Package.AuthoringSink> interna di elementi corrispondenti.

## <a name="set-the-trigger"></a>Impostare il trigger
 L'esempio seguente illustra come rilevare le parentesi corrispondenti, le parentesi graffe e le parentesi quadre e impostare il trigger nello scanner. Il metodo nella classe rileva il trigger e chiama il parser per trovare la coppia corrispondente (vedere la sezione Ricerca della corrispondenza <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> in questo articolo).  Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contenga un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Trova la corrispondenza con le parentesi graffe
 Di seguito è riportato un esempio semplificato per la corrispondenza degli elementi del linguaggio `{ }` , e e per l'aggiunta dei relativi `( )` `[ ]` intervalli <xref:Microsoft.VisualStudio.Package.AuthoringSink> all'oggetto . Questo approccio non è un approccio consigliato per l'analisi del codice sorgente. è solo a scopo illustrativo.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Vedi anche
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
