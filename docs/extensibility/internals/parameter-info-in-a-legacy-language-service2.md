---
title: Informazioni sui parametri in un servizio di linguaggio legacy2 | Microsoft Docs
description: Informazioni su come supportare l'operazione IntelliSense Parameter Info per la visualizzazione di una firma del metodo durante la digitazione del metodo in un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e5e7c2e39ad5cd1068c49001b2803297277d39e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102402"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Informazioni sui parametri in un servizio di linguaggio legacy 2
Informazioni sui parametri di IntelliSense è una descrizione comando che visualizza la firma di un metodo quando l'utente tipizza il carattere iniziale dell'elenco di parametri (in genere una parentesi aperta) per l'elenco di parametri del metodo. Quando viene immesso ogni parametro e viene digitato il separatore dei parametri (in genere una virgola), la descrizione comando viene aggiornata per visualizzare il parametro successivo in grassetto.

 Le classi MPF (Managed Package Framework) forniscono il supporto per la gestione della descrizione comando informazioni sui parametri. Il parser deve rilevare i caratteri di inizio, successivo e finale del parametro e deve fornire un elenco delle firme del metodo e dei relativi parametri associati.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Estensione dell'editor e di Servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Il parser deve impostare il valore del trigger quando trova un carattere iniziale dell'elenco di <xref:Microsoft.VisualStudio.Package.TokenTriggers> parametri (spesso una parentesi aperta). Deve impostare un <xref:Microsoft.VisualStudio.Package.TokenTriggers> trigger quando trova un separatore di parametri (spesso una virgola). In questo modo viene aggiornata una descrizione comando informazioni parametro e viene visualizzato il parametro successivo in grassetto. Il parser deve impostare il valore del trigger quando trova il carattere finale dell'elenco di parametri <xref:Microsoft.VisualStudio.Package.TokenTriggers> (spesso una parentesi chiusa).

 Il valore del trigger avvia una chiamata al metodo , che a sua volta chiama il parser del <xref:Microsoft.VisualStudio.Package.TokenTriggers> metodo con un motivo di analisi di <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> . Se il parser determina che l'identificatore prima del carattere iniziale dell'elenco di parametri è un nome di metodo riconosciuto, restituisce un elenco di firme di metodo corrispondenti <xref:Microsoft.VisualStudio.Package.AuthoringScope> nell'oggetto . Se sono state trovate firme di metodo, viene visualizzata la descrizione comando Informazioni parametro con la prima firma nell'elenco. Questa descrizione comando viene quindi aggiornata quando viene digitata una parte maggiore della firma. Quando viene digitato il carattere finale dell'elenco di parametri, la descrizione comando Informazioni parametro viene rimossa dalla visualizzazione.

> [!NOTE]
> Per assicurarsi che la descrizione comando Informazioni parametro sia formattata correttamente, è necessario eseguire l'override delle proprietà della classe per <xref:Microsoft.VisualStudio.Package.Methods> fornire i caratteri appropriati. La classe di base <xref:Microsoft.VisualStudio.Package.Methods> presuppone una firma del metodo in stile C#. Per informazioni <xref:Microsoft.VisualStudio.Package.Methods> dettagliate su come eseguire questa operazione, vedere la classe .

## <a name="enabling-support-for-the-parameter-info"></a>Abilitazione del supporto per le informazioni sui parametri
 Per supportare le descrizioni comando relative alle informazioni sui parametri, è necessario impostare il `ShowCompletion` parametro denominato di su <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . Il servizio di linguaggio legge il valore di questa voce del Registro di sistema dalla <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà .

 Inoltre, la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> deve essere impostata su per visualizzare la descrizione comando `true` Informazioni parametro.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio semplificato di rilevamento dei caratteri dell'elenco di parametri e dell'impostazione dei trigger appropriati. Questo esempio è solo a scopo illustrativo. Presuppone che lo scanner contenga un metodo che identifica e `GetNextToken` restituisce token da una riga di testo. Il codice di esempio imposta semplicemente i trigger ogni volta che vede il tipo di carattere giusto.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Supporto della descrizione comando informazioni parametro nel parser
 La classe presuppone il contenuto delle classi e quando la descrizione comando Informazioni <xref:Microsoft.VisualStudio.Package.Source> parametro viene visualizzata e <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> aggiornata.

- Il parser viene specificato quando viene digitato il carattere <xref:Microsoft.VisualStudio.Package.ParseReason> iniziale dell'elenco di parametri.

- La posizione specificata nell'oggetto è immediatamente dopo il carattere di inizio <xref:Microsoft.VisualStudio.Package.ParseRequest> dell'elenco di parametri. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo disponibili in tale posizione e archiviarle in un elenco nella versione <xref:Microsoft.VisualStudio.Package.AuthoringScope> dell'oggetto. Questo elenco include il nome del metodo, il tipo di metodo (o il tipo restituito) e un elenco di parametri possibili. Questo elenco viene successivamente cercato per la firma o le firme del metodo da visualizzare nella descrizione comando Informazioni parametro.

  Il parser deve quindi analizzare la riga specificata dall'oggetto per raccogliere il nome del metodo immesso e la distanza tra i parametri di <xref:Microsoft.VisualStudio.Package.ParseRequest> digitazione dell'utente. Questa operazione viene eseguita passando il nome del metodo al metodo sull'oggetto e quindi chiamando il metodo quando viene analizzato il carattere iniziale dell'elenco di parametri, chiamando il metodo quando viene analizzato il carattere successivo dell'elenco di parametri e infine chiamando il metodo quando viene analizzato il carattere finale dell'elenco di <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> parametri. I risultati di queste chiamate al metodo vengono usati dalla classe per aggiornare in modo appropriato <xref:Microsoft.VisualStudio.Package.Source> la descrizione comando Informazioni parametro.

### <a name="example"></a>Esempio
 Ecco una riga di testo che l'utente potrebbe immettere. I numeri sotto la riga indicano quale passaggio viene effettuato dal parser in tale posizione nella riga (presupponendo che l'analisi si smuova da sinistra a destra). Il presupposto in questo caso è che tutti gli elementi precedenti alla riga siano già stati analizzati per le firme del metodo, inclusa la firma del metodo "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 I passaggi esersi dal parser sono descritti di seguito:

1. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con il testo "testfunc".

2. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Il parser chiama <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
