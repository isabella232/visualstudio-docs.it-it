---
title: Corrispondenza parentesi graffe in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03420aa0638fcf12fa36fb871b4a14d2695f0377
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968890"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Corrispondenza parentesi graffe in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Corrispondenza delle parentesi graffe consente allo sviluppatore di tenere traccia di elementi del linguaggio che si verificano insieme, ad esempio le parentesi tonde e parentesi graffe devono. Quando uno sviluppatore immette una parentesi graffa di chiusura, parentesi graffa di apertura viene evidenziata.  
  
 È possibile associare due o tre elementi che si verificano contemporaneamente, denominate coppie e Triple. Triple sono set di tre elementi che si verificano contemporaneamente. Ad esempio, in C#, il `foreach` istruzione costituisce una tripla: "`foreach()`","`{`", e "`}`". I tre elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare corrispondenza parentesi graffe, vedere [procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> supporta entrambe le coppie di classe e per triplica con il <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metodi.  
  
## <a name="implementation"></a>Implementazione  
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in genere eseguita mediante l'implementazione <xref:Microsoft.VisualStudio.Package.IScanner> per rilevare la lingua corrispondente e viene quindi utilizzato il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo corrispondere gli elementi.  
  
 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama lo scanner per suddividere in token di riga e restituire il token appena prima il punto di inserimento. Lo scanner indica che è stata trovata una coppia di elemento di linguaggio impostando un valore token trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> sul token corrente. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiamate al metodo il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodo con il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> per individuare l'elemento di linguaggio corrispondenti. Quando viene trovato l'elemento di linguaggio corrispondente, entrambi gli elementi vengono evidenziati.  
  
 Per una descrizione completa del modo in cui digitare una parentesi graffa attiva l'evidenziazione delle parentesi graffe, vedere la sezione "Operazione di analisi di esempio" nell'argomento [Scanner e Parser servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Abilitazione del supporto per la corrispondenza delle parentesi graffe  
 Il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> impostare l'attributo il `MatchBraces`, `MatchBracesAtCaret`, e `ShowMatchingBrace` parametri denominati che imposteranno le proprietà corrispondenti del <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Proprietà delle preferenze di lingua possono essere impostate anche dall'utente.  
  
|Voce del Registro di sistema|Proprietà|Descrizione|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Corrispondenza parentesi graffe Abilita|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Consente di corrispondenza tra parentesi graffe durante lo spostamento del punto di inserimento.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|  
  
## <a name="matching-conditional-statements"></a>Corrispondenza di istruzioni condizionali  
 È possibile far corrispondere le istruzioni condizionali, ad esempio `if`, `else if`, e `else`, o `#if`, `#elif`, `#else`, `#endif`, esattamente come i delimitatori di corrispondenza. È possibile creare una sottoclasse di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe e forniscono un metodo che è possibile aggiungere testo si estende oltre i delimitatori per la matrice interna di elementi corrispondenti.  
  
## <a name="setting-the-trigger"></a>Impostare il Trigger  
 Nell'esempio seguente viene illustrato come rilevare la corrispondenza tra parentesi, parentesi graffe e parentesi quadre e impostare il trigger per tale nello scanner. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo di <xref:Microsoft.VisualStudio.Package.Source> classe rileva il trigger e chiama il parser per trovare la coppia corrispondente (vedere la sezione "Trovare la corrispondenza" in questo argomento). Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo.  
  
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
  
## <a name="matching-the-braces"></a>Corrispondenza parentesi graffe  
 Ecco un esempio semplificato per la corrispondenza di {} elementi del linguaggio () e [] e i loro intervalli per l'aggiunta di <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto. Questo approccio non è un approccio consigliato per l'analisi del codice sorgente; è solo a scopo illustrativo.  
  
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
 [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
