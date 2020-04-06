---
title: Corrispondenza delle parentesi graffe in un servizio di linguaggio Legacy Documenti Microsoft
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
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709812"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Associare la corrispondenza in un servizio di linguaggio legacy
La corrispondenza delle parentesi graffe consente allo sviluppatore di tenere traccia degli elementi del linguaggio che devono verificarsi insieme, ad esempio parentesi e parentesi graffe. Quando uno sviluppatore immette una parentesi graffa di chiusura, la parentesi graffa di apertura viene evidenziata.

 È possibile abbinare due o tre elementi co-legati, chiamati coppie e triple. Le triple sono insiemi di tre elementi co-presentinti. Ad esempio, in C, `foreach` l'istruzione `foreach()` `{`forma `}`una tripla: , , e . Tutti e tre gli elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare la corrispondenza tra parentesi graffe, vedere Procedura dettagliata: visualizzazione di [parentesi graffe corrispondenti](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe supporta sia coppie che <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> triple con i metodi e .

## <a name="implementation"></a>Implementazione
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in <xref:Microsoft.VisualStudio.Package.IScanner> genere eseguita implementando per <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> rilevare un linguaggio corrispondente e quindi utilizzando il metodo per abbinare gli elementi.

 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama lo scanner per suddividere in token la riga e restituire il token appena prima del punto di inserimento. Lo scanner indica che è stata trovata una coppia di <xref:Microsoft.VisualStudio.Package.TokenTriggers> elementi del linguaggio impostando un valore di trigger di token su un token corrente. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> chiama il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> che a sua volta <xref:Microsoft.VisualStudio.Package.ParseReason> chiama il metodo con il valore di parse reason di per individuare l'elemento del linguaggio corrispondente. Quando viene trovato l'elemento di linguaggio corrispondente, entrambi gli elementi vengono evidenziati.

 Per una descrizione completa del modo in cui la digitazione di una parentesi graffa attiva l'evidenziazione delle parentesi graffe, vedere la sezione Operazione di analisi di *esempio* nell'articolo Parser e scanner del [servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Abilitare il supporto per la corrispondenza delle parentesi graffeEnable support for brace matching
 L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> può impostare le voci del Registro di sistema **MatchBraces**, **MatchBracesAtCaret**e **ShowMatchingBrace** che impostano le proprietà corrispondenti della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe . Le proprietà delle preferenze di lingua possono anche essere impostate dall'utente.

|Voce del Registro di sistema|Proprietà|Descrizione|
|--------------------|--------------|-----------------|
|Parentesi corrispondenti|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Abilita la corrispondenza tra parentesi graffe.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Abilita la corrispondenza del parente della parentesi graffa durante lo spostamento del riquadro di inserimento.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|

## <a name="match-conditional-statements"></a>Associare istruzioni condizionali
 È possibile associare istruzioni `if`condizionali, `#if`ad `#elif` `#else`esempio `#endif`, `else if`e , o `else`, , , , allo stesso modo dei delimitatori corrispondenti. È possibile creare <xref:Microsoft.VisualStudio.Package.AuthoringSink> una sottoclasse della classe e fornire un metodo che può aggiungere intervalli di testo e delimitatori alla matrice interna di elementi corrispondenti.

## <a name="set-the-trigger"></a>Impostare il trigger
 Nell'esempio seguente viene illustrato come rilevare parentesi corrispondenti, parentesi graffe e parentesi graffe e impostando il trigger per tale parentesi nello scanner. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo <xref:Microsoft.VisualStudio.Package.Source> nella classe rileva il trigger e chiama il parser per trovare la coppia corrispondente (vedere la sezione *Ricerca della corrispondenza* in questo articolo). Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner `GetNextToken` contenga un metodo che identifica e restituisce i token da una riga di testo.

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

## <a name="match-the-braces"></a>Abbina le parentesi graffe
 Di seguito è riportato un `{ }` `( )`esempio `[ ]`semplificato per la corrispondenza degli elementi del linguaggio , , e , e per aggiungere gli intervalli all'oggetto. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Questo approccio non è consigliato per l'analisi del codice sorgente. è solo a scopo illustrativo.

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
- [Funzionalità del servizio di linguaggio legacyLegacy language service features](../../extensibility/internals/legacy-language-service-features1.md)
- [Parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
