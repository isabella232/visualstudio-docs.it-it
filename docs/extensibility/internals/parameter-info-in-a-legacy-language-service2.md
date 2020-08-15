---
title: Informazioni sui parametri in un Service2 di linguaggio legacy | Microsoft Docs
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
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2020
ms.locfileid: "88237958"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Informazioni sui parametri in un servizio di linguaggio Legacy 2
Informazioni sul parametro IntelliSense è una descrizione comando che visualizza la firma di un metodo quando l'utente digita il carattere iniziale dell'elenco di parametri, in genere una parentesi aperta, per l'elenco dei parametri del metodo. Quando viene immesso ogni parametro e viene digitato il separatore di parametro (in genere una virgola), la descrizione comando viene aggiornata per mostrare il parametro successivo in grassetto.

 Le classi del Framework di pacchetto gestito (MPF) forniscono supporto per la gestione della descrizione comando informazioni parametri. Il parser deve rilevare i caratteri di inizio, parametro successivo e parametro finale del parametro e deve fornire un elenco delle firme del metodo e dei parametri associati.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [estensione dei servizi di editor e di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Il parser deve impostare il valore del trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando trova un carattere iniziale dell'elenco di parametri (spesso una parentesi aperta). Deve impostare un <xref:Microsoft.VisualStudio.Package.TokenTriggers> trigger quando trova un separatore di parametri (spesso una virgola). In questo modo viene aggiornata una descrizione comando per informazioni sul parametro e il parametro successivo viene visualizzato in grassetto. Il parser deve impostare il valore del trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando se trova il carattere finale dell'elenco di parametri (spesso una parentesi di chiusura).

 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> valore del trigger avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodo, che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser del metodo con un motivo di analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Se il parser determina che l'identificatore prima del carattere iniziale dell'elenco di parametri è un nome di metodo riconosciuto, restituisce un elenco di firme del metodo corrispondenti nell' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Se sono state trovate firme di metodi, la descrizione comando informazioni sul parametro viene visualizzata con la prima firma nell'elenco. Questa descrizione comando viene quindi aggiornata quando viene digitato un numero maggiore di firme. Quando il carattere finale dell'elenco di parametri è tipizzato, la descrizione comando informazioni parametri viene rimossa dalla visualizzazione.

> [!NOTE]
> Per assicurarsi che la descrizione comando informazioni parametri sia formattata correttamente, è necessario eseguire l'override delle proprietà nella <xref:Microsoft.VisualStudio.Package.Methods> classe per fornire i caratteri appropriati. La <xref:Microsoft.VisualStudio.Package.Methods> classe base presuppone una firma del metodo di tipo C#. <xref:Microsoft.VisualStudio.Package.Methods>Per informazioni dettagliate su come eseguire questa operazione, vedere la classe.

## <a name="enabling-support-for-the-parameter-info"></a>Abilitazione del supporto per le informazioni sul parametro
 Per supportare le descrizioni comandi delle informazioni sui parametri, è necessario impostare il `ShowCompletion` parametro denominato di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> su `true` . Il servizio di linguaggio legge il valore di questa voce del registro di sistema dalla <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Proprietà.

 Inoltre, la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> proprietà deve essere impostata su `true` per visualizzare la descrizione comando per informazioni sul parametro.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio semplificato di rilevamento dei caratteri dell'elenco di parametri e dell'impostazione dei trigger appropriati. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contenga un metodo `GetNextToken` che identifica e restituisce token da una riga di testo. Il codice di esempio imposta semplicemente i trigger ogni volta che viene visualizzato il tipo di carattere corretto.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Supporto della descrizione comando per informazioni sul parametro nel parser
 La <xref:Microsoft.VisualStudio.Package.Source> classe fa alcune ipotesi sul contenuto delle <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> classi e quando viene visualizzata e aggiornata la descrizione comando informazioni sul parametro.

- Il parser viene specificato <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato il carattere iniziale dell'elenco di parametri.

- Il percorso specificato nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto si trova immediatamente dopo il carattere iniziale dell'elenco dei parametri. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo disponibili in tale posizione e archiviarle in un elenco della versione dell' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Questo elenco include il nome del metodo, il tipo di metodo (o il tipo restituito) e un elenco di parametri possibili. Questo elenco viene successivamente cercato la firma o le firme del metodo da visualizzare nella descrizione comando informazioni parametri.

  Il parser deve quindi analizzare la riga specificata dall' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per raccogliere il nome del metodo immesso, oltre a quanto lungo l'utente è nella digitazione dei parametri. Questa operazione viene eseguita passando il nome del metodo al <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodo sull' <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto e quindi chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metodo quando viene analizzato il carattere iniziale dell'elenco di parametri, chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metodo quando viene analizzato il carattere successivo dell'elenco di parametri e infine chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodo quando viene analizzato il carattere finale dell'elenco dei parametri. I risultati di queste chiamate al metodo vengono usati dalla <xref:Microsoft.VisualStudio.Package.Source> classe per aggiornare la descrizione comando informazioni parametri in modo appropriato.

### <a name="example"></a>Esempio
 Ecco una riga di testo che l'utente può immettere. I numeri sotto la riga indicano quale passaggio viene assunto dal parser in tale posizione nella riga (presupponendo che l'analisi venga spostata da sinistra a destra). Il presupposto è che tutto ciò che precede la riga è già stato analizzato per le firme dei metodi, inclusa la firma del metodo "TestFunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 I passaggi eseguiti dal parser sono descritti di seguito:

1. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con il testo "TestFunc".

2. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
