---
title: Informazioni sui parametri in un servizio di linguaggio Legacy2 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706739"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sui parametri in un servizio di linguaggio legacy
Informazioni sui parametri IntelliSense è una descrizione comando che visualizza la firma di un metodo quando l'utente digita il carattere iniziale dell'elenco di parametri (in genere una parentesi aperta) per l'elenco di parametri del metodo. Quando viene immesso ogni parametro e viene digitato il separatore di parametro (in genere una virgola), la descrizione comando viene aggiornata per visualizzare il parametro successivo in grassetto.

 Le classi del framework di pacchetto gestito (MPF) forniscono il supporto per la gestione della descrizione comando Informazioni sui parametri. Il parser deve rilevare i caratteri di inizio parametro, parametro successivo e fine parametro e deve fornire un elenco delle firme del metodo e dei parametri associati.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'editor e](../../extensibility/extending-the-editor-and-language-services.md)dei servizi di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Il parser deve impostare il valore <xref:Microsoft.VisualStudio.Package.TokenTriggers> del trigger viene impostato quando trova un carattere di inizio dell'elenco di parametri (spesso una parentesi aperta). Dovrebbe impostare <xref:Microsoft.VisualStudio.Package.TokenTriggers> un trigger quando trova un separatore di parametro (spesso una virgola). In questo modo una descrizione comando Informazioni parametro da aggiornare e visualizzare il parametro successivo in grassetto. Il parser deve impostare il valore <xref:Microsoft.VisualStudio.Package.TokenTriggers> del trigger quando se trova il carattere finale dell'elenco di parametri (spesso una parentesi chiusa).

 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> valore trigger avvia una <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> chiamata al metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> , che a sua <xref:Microsoft.VisualStudio.Package.ParseReason>volta chiama il parser del metodo con un motivo di analisi di . Se il parser determina che l'identificatore prima del carattere iniziale dell'elenco <xref:Microsoft.VisualStudio.Package.AuthoringScope> di parametri è un nome di metodo riconosciuto, restituisce un elenco di firme di metodo corrispondenti nell'oggetto. Se sono state trovate firme del metodo, viene visualizzata la descrizione comando Informazioni parametro con la prima firma nell'elenco. Questa descrizione comando viene quindi aggiornata man mano che viene digitata una parte maggiore della firma. Quando viene digitato il carattere finale dell'elenco di parametri, la descrizione comando Informazioni parametro viene rimossa dalla vista.

> [!NOTE]
> Per assicurarsi che la descrizione comando Informazioni parametro sia <xref:Microsoft.VisualStudio.Package.Methods> formattata correttamente, è necessario eseguire l'override delle proprietà della classe per fornire i caratteri appropriati. La <xref:Microsoft.VisualStudio.Package.Methods> classe di base presuppone una firma del metodo di tipo C. Vedere <xref:Microsoft.VisualStudio.Package.Methods> la classe per informazioni dettagliate su come eseguire questa operazione.

## <a name="enabling-support-for-the-parameter-info"></a>Abilitazione del supporto per le informazioni sui parametriEnabling Support for the Parameter Info
 Per supportare le descrizioni comandi `ShowCompletion` Di Informazioni <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true`parametro, è necessario impostare il parametro denominato di su . Il servizio di linguaggio legge il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> valore di questa voce del Registro di sistema dalla proprietà .

 Inoltre, la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> proprietà deve `true` essere impostata su per la descrizione comando Informazioni parametro da visualizzare.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio semplificato di rilevamento dei caratteri dell'elenco di parametri e dell'impostazione dei trigger appropriati. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner `GetNextToken` contenga un metodo che identifica e restituisce i token da una riga di testo. Il codice di esempio imposta semplicemente i trigger ogni volta che viene visualizzato il tipo di carattere corretto.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Supporto della descrizione comando delle informazioni sui parametri nel parserSupporting the Parameter Info ToolTip in the Parser
 La <xref:Microsoft.VisualStudio.Package.Source> classe fa alcune ipotesi <xref:Microsoft.VisualStudio.Package.AuthoringScope> sul <xref:Microsoft.VisualStudio.Package.AuthoringSink> contenuto delle classi e quando la descrizione comando Informazioni parametro viene visualizzata e aggiornata.

- Il parser <xref:Microsoft.VisualStudio.Package.ParseReason> viene fornito quando viene digitato il carattere iniziale dell'elenco di parametri.

- La posizione specificata <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto è immediatamente successiva al carattere iniziale dell'elenco di parametri. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo <xref:Microsoft.VisualStudio.Package.AuthoringScope> disponibili in tale posizione e archiviarle in un elenco nella versione dell'oggetto. Questo elenco include il nome del metodo, il tipo di metodo (o tipo restituito) e un elenco di parametri possibili. In questo elenco viene successivamente eseguita la ricerca della firma o delle firme del metodo da visualizzare nella descrizione comando Informazioni parametro.

  Il parser deve quindi analizzare <xref:Microsoft.VisualStudio.Package.ParseRequest> la riga specificata dall'oggetto per raccogliere il nome del metodo immesso e la distanza dell'utente nei parametri di digitazione. Questa operazione viene eseguita passando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> nome del <xref:Microsoft.VisualStudio.Package.AuthoringSink> metodo al <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metodo sull'oggetto e quindi chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metodo quando viene analizzato il carattere <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> iniziale dell'elenco di parametri, chiamando il metodo quando viene analizzato il carattere successivo dell'elenco di parametri e infine chiamando il metodo quando viene analizzato il carattere finale dell'elenco di parametri. I risultati di queste chiamate <xref:Microsoft.VisualStudio.Package.Source> al metodo vengono utilizzati dalla classe per aggiornare la descrizione comando Informazioni parametro in modo appropriato.

### <a name="example"></a>Esempio
 Ecco una riga di testo che l'utente potrebbe immettere. I numeri sotto la riga indicano quale passaggio viene eseguito dal parser in quella posizione nella riga (presupponendo che l'analisi si sposti da sinistra a destra). Il presupposto è che tutto ciò che precede la riga è già stato analizzato per le firme del metodo, inclusa la firma del metodo "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 I passaggi eseguiti dal parser sono descritti di seguito:The steps that the parser takes are outlined below:

1. Il parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> chiama con il testo "testfunc".

2. Il parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>chiama .

3. Il parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>chiama .

4. Il parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>chiama .
