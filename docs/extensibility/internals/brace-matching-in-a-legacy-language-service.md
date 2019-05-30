---
title: Corrispondenza parentesi graffe in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a535fc479fe5cc398d09d7aa9e47a3c91fa97f38
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309178"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Corrispondenza parentesi graffe in un servizio di linguaggio legacy
Corrispondenza delle parentesi graffe consente allo sviluppatore di tenere traccia di elementi del linguaggio che si verificano insieme, ad esempio le parentesi tonde e parentesi graffe devono. Quando uno sviluppatore immette una parentesi graffa di chiusura, parentesi graffa di apertura viene evidenziata.

 È possibile associare due o tre elementi che si verificano contemporaneamente, denominate coppie e Triple. Triple sono set di tre elementi che si verificano contemporaneamente. Ad esempio, in c#, il `foreach` istruzione costituisce una tripla: `foreach()`, `{`, e `}`. I tre elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.

 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare corrispondenza parentesi graffe, vedere [procedura dettagliata: Visualizzare le parentesi graffe corrispondenti](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.

 Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> supporta entrambe le coppie di classe e per triplica con il <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metodi.

## <a name="implementation"></a>Implementazione
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in genere eseguita mediante l'implementazione <xref:Microsoft.VisualStudio.Package.IScanner> per rilevare la lingua corrispondente e viene quindi utilizzato il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo corrispondere gli elementi.

 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama lo scanner per suddividere in token di riga e restituire il token appena prima il punto di inserimento. Lo scanner indica che è stata trovata una coppia di elemento di linguaggio impostando un valore token trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> sul token corrente. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiamate al metodo il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodo con il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> per individuare l'elemento di linguaggio corrispondenti. Quando viene trovato l'elemento di linguaggio corrispondente, entrambi gli elementi vengono evidenziati.

 Per una descrizione completa del modo in cui digitare una parentesi graffa attiva l'evidenziazione delle parentesi graffe, vedere la *operazione di analisi di esempio* sezione dell'articolo [scanner e parser servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Abilitare il supporto per la corrispondenza delle parentesi graffe
 Il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo è possibile impostare il **MatchBraces**, **MatchBracesAtCaret**, e **ShowMatchingBrace** le voci del Registro di sistema che imposteranno le proprietà corrispondenti del <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Proprietà delle preferenze di lingua possono essere impostate anche dall'utente.

|Voce del Registro di sistema|Proprietà|Descrizione|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Corrispondenza parentesi graffe Abilita.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Consente di corrispondenza tra parentesi graffe durante lo spostamento del punto di inserimento.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|

## <a name="match-conditional-statements"></a>Corrispondenza di istruzioni condizionali
 È possibile far corrispondere le istruzioni condizionali, ad esempio `if`, `else if`, e `else`, o `#if`, `#elif`, `#else`, `#endif`, esattamente come i delimitatori di corrispondenza. È possibile creare una sottoclasse di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe e forniscono un metodo che è possibile aggiungere testo si estende oltre i delimitatori per la matrice interna di elementi corrispondenti.

## <a name="set-the-trigger"></a>Impostare il trigger
 Nell'esempio seguente viene illustrato come rilevare la corrispondenza tra parentesi, parentesi graffe e parentesi quadre e impostare il trigger per tale nello scanner. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo sul <xref:Microsoft.VisualStudio.Package.Source> classe rileva il trigger e chiama il parser per trovare la coppia corrispondente (vedere la *trovare la corrispondenza* sezione in questo articolo). Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo.

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

## <a name="match-the-braces"></a>Corrispondenza parentesi graffe
 Ecco un esempio semplificato per gli elementi del linguaggio di ricerca `{ }`, `( )`, e `[ ]`e aggiungendo i loro intervalli per la <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto. Questo approccio non è un approccio consigliato per l'analisi del codice sorgente; è solo a scopo illustrativo.

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

## <a name="see-also"></a>Vedere anche
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Scanner e parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)