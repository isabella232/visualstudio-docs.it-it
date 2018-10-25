---
title: Informazioni sui parametri in un tipo di linguaggio legacy2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b562f5dd2c7e4f3851f6ed16e0f0007ef65e14cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863256"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sui parametri in un servizio di linguaggio Legacy
Informazioni sul parametro di IntelliSense è una descrizione comando che consente di visualizzare la firma di un metodo quando l'utente digita l'elenco dei parametri start carattere (in genere una parentesi di apertura) per l'elenco di parametri di metodo. Quando si immette ogni parametro e il separatore di parametro (in genere una virgola) è tipizzato, la descrizione comando viene aggiornato per mostrare il parametro successivo in grassetto.  
  
 Le classi di framework (MPF) di pacchetto gestito forniscono supporto per la gestione di descrizione comando informazioni sul parametro. Il parser deve rilevare parametro start, parametro successivamente, e caratteri di fine dei parametri che deve fornire un elenco delle firme del metodo e i relativi parametri.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation"></a>Implementazione  
 Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> viene impostato quando rileva un carattere iniziale dell'elenco parametri (spesso una parentesi di apertura). Deve essere impostato un <xref:Microsoft.VisualStudio.Package.TokenTriggers> attivano quando rileva un separatore di parametro (spesso una virgola). In questo modo una descrizione comando informazioni sul parametro devono essere aggiornati e visualizzare il parametro successivo in grassetto. Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando se rileva che il carattere di fine elenco di parametri (spesso una parentesi di chiusura).  
  
 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> valore trigger avvia una chiamata ai <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodo, che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Se il parser rileva che l'identificatore prima che l'elenco dei parametri start carattere sia un nome di metodo riconosciuto, viene restituito un elenco di corrispondenza delle firme del metodo nel <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Se sono state trovate le firme di metodo, la descrizione comando informazioni sul parametro viene visualizzata con la firma prima nell'elenco. Questa descrizione comando viene quindi aggiornata con informazioni della firma è tipizzato. Quando si digita il carattere di fine elenco di parametri, la descrizione comando informazioni sul parametro viene rimosso dalla visualizzazione.  
  
> [!NOTE]
>  Per assicurarsi che la descrizione comando informazioni sul parametro sia formattata correttamente, è necessario eseguire l'override di proprietà nel <xref:Microsoft.VisualStudio.Package.Methods> classe per fornire i caratteri appropriati. La base <xref:Microsoft.VisualStudio.Package.Methods> classe presuppone c#-firma del metodo stile. Vedere il <xref:Microsoft.VisualStudio.Package.Methods> classe per informazioni dettagliate sul modo in cui questa operazione può essere eseguita.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Abilitazione del supporto per le informazioni di parametro  
 Per supportare le descrizioni comandi informazioni sui parametri, è necessario impostare il `ShowCompletion` del parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> a `true`. Il servizio di linguaggio legge il valore di questa voce del Registro di sistema dal <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà.  
  
 Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> proprietà deve essere impostata su `true` per la descrizione comando informazioni sul parametro da visualizzare.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio semplificato di rilevare i caratteri di elenco di parametri e impostando i trigger appropriati. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo. L'esempio di codice semplicemente imposta i trigger quando viene rilevato il tipo di carattere a destra.  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>La descrizione comando informazioni sul parametro di supporto nel Parser  
 Il <xref:Microsoft.VisualStudio.Package.Source> classe fa alcune supposizioni sul contenuto del <xref:Microsoft.VisualStudio.Package.AuthoringScope> e <xref:Microsoft.VisualStudio.Package.AuthoringSink> classi se la descrizione comando informazioni sul parametro viene visualizzata e aggiornata.  
  
- Il parser ha <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato il carattere iniziale dell'elenco parametri.  
  
- Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto viene immediatamente dopo che l'elenco dei parametri start carattere. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo disponibile all'indirizzo che posizionare e archiviano in un elenco nella versione del <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Questo elenco include il nome del metodo, tipo metodo (o tipo restituito) e un elenco di possibili parametri. Questo elenco viene cercato in un secondo momento per la firma del metodo o firme da visualizzare nella descrizione comando informazioni sul parametro.  
  
  La riga specificata da deve quindi analizzato dal parser di <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per raccogliere il nome del metodo l'immissione e la distanza lungo l'utente è nella digitazione di parametri. Questa operazione viene eseguita passando il nome del metodo dal <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodo sul <xref:Microsoft.VisualStudio.Package.AuthoringSink> e quindi chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metodo quando l'elenco dei parametri start carattere viene analizzato, la chiamata il <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> (metodo) quando l'elenco dei parametri carattere successivo viene analizzato e infine la chiamata di <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodo quando viene analizzato il carattere di fine elenco di parametri. I risultati di chiamate di questi metodi vengono usati per il <xref:Microsoft.VisualStudio.Package.Source> classe per aggiornare la descrizione comando informazioni sul parametro in modo appropriato.  
  
### <a name="example"></a>Esempio  
 Ecco una riga di testo, che l'utente potrebbe immettere. I numeri sotto la linea indicano quale passaggio proviene dal parser in tale posizione nella riga (presupponendo che l'analisi si sposta da sinistra a destra). Il presupposto è che tutto ciò che precede la riga è già stato analizzato delle firme dei metodi, tra cui la firma del metodo "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Di seguito sono illustrati i passaggi che il parser accetta:  
  
1.  Le chiamate del parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con il testo "testfunc".  
  
2.  Le chiamate del parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Le chiamate del parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Le chiamate del parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.