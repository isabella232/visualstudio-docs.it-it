---
title: Corrispondenza tra parentesi graffe in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulla corrispondenza tra parentesi graffe in un servizio di linguaggio legacy, che consente di tenere traccia degli elementi del linguaggio che devono essere eseguiti insieme, ad esempio le parentesi e le parentesi graffe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d9f93f0081d45e986ab6845cdaee53209b84e13
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190005"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Corrispondenza tra parentesi graffe in un servizio di linguaggio legacy
La corrispondenza tra parentesi graffe consente allo sviluppatore di tenere traccia degli elementi del linguaggio che devono essere eseguiti insieme, ad esempio tra parentesi e parentesi graffe. Quando uno sviluppatore immette una parentesi graffa di chiusura, viene evidenziata la parentesi graffa di apertura.

 È possibile trovare la corrispondenza con due o tre elementi coesistenti, detti coppie e triple. Triple sono set di tre elementi coesistenti. In C#, ad esempio, l' `foreach` istruzione forma una tripla: `foreach()` , `{` e `}` . Tutti e tre gli elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare la corrispondenza delle parentesi graffe, vedere [procedura dettagliata: visualizzare le parentesi graffe corrispondenti](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe supporta sia coppie che triple con i <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> metodi e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> .

## <a name="implementation"></a>Implementazione
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in genere eseguita implementando <xref:Microsoft.VisualStudio.Package.IScanner> per rilevare una lingua corrispondente e quindi utilizzando il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo per trovare la corrispondenza con gli elementi.

 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama lo scanner per tokenize la riga e restituisce il token immediatamente prima del punto di inserimento. Lo scanner indica che è stata rilevata una coppia di elementi di linguaggio impostando il valore del trigger del token <xref:Microsoft.VisualStudio.Package.TokenTriggers> sul token corrente. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodo con il valore del motivo dell'analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> per individuare l'elemento del linguaggio corrispondente. Quando viene trovato l'elemento di linguaggio corrispondente, vengono evidenziati entrambi gli elementi.

 Per una descrizione completa del modo in cui la digitazione di una parentesi graffa attiva l'evidenziazione della parentesi graffa, vedere la sezione *esempio di operazione di analisi* nell'articolo [parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Abilita il supporto per la corrispondenza tra parentesi graffe
 L' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo può impostare le voci del registro di sistema **MatchBraces**, **MatchBracesAtCaret** e **ShowMatchingBrace** che impostano le proprietà corrispondenti della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Le proprietà delle preferenze della lingua possono essere impostate anche dall'utente.

|Voce del Registro di sistema|Proprietà|Descrizione|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Abilita la corrispondenza tra parentesi graffe.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Abilita la corrispondenza tra parentesi graffe come spostamento del cursore.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|

## <a name="match-conditional-statements"></a>Corrisponde a istruzioni condizionali
 È possibile associare le istruzioni condizionali, ad esempio `if` , `else if` e `else` , o,,, allo `#if` `#elif` `#else` `#endif` stesso modo dei delimitatori corrispondenti. È possibile creare una sottoclasse della <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe e fornire un metodo in grado di aggiungere intervalli di testo e delimitatori alla matrice interna di elementi corrispondenti.

## <a name="set-the-trigger"></a>Imposta il trigger
 Nell'esempio seguente viene illustrato come rilevare le parentesi corrispondenti, le parentesi graffe e le parentesi quadre e impostare il trigger per l'oggetto nello scanner. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metodo sulla <xref:Microsoft.VisualStudio.Package.Source> classe rileva il trigger e chiama il parser per trovare la coppia corrispondente. vedere la sezione *ricerca della corrispondenza* in questo articolo. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contenga un metodo `GetNextToken` che identifica e restituisce token da una riga di testo.

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

## <a name="match-the-braces"></a>Corrispondenza tra parentesi graffe
 Di seguito è riportato un esempio semplificato per la corrispondenza tra gli elementi del linguaggio `{ }` , e e l' `( )` `[ ]` aggiunta dei relativi intervalli all' <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto. Questo approccio non è consigliato per l'analisi del codice sorgente. è solo a scopo illustrativo.

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
- [Parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
