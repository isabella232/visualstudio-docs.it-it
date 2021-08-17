---
title: Parser del servizio di linguaggio legacy e analisi | Microsoft Docs
description: Informazioni sul parser e sullo scanner del servizio di linguaggio legacy che selezionano le informazioni sul codice visualizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ac6c0a4a0facc68496a2d51b23b6979ba8d9359
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110475"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e parser dei servizi di linguaggio legacy
Il parser è il centro del servizio di linguaggio. Le classi del linguaggio MPF (Managed Package Framework) richiedono un parser del linguaggio per selezionare le informazioni sul codice visualizzato. Un parser separa il testo in token lessicali e quindi li identifica in base al tipo e alla funzionalità.

## <a name="discussion"></a>Discussione
 Di seguito è riportato un metodo C#.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 In questo esempio i token sono le parole e i segni di punteggiatura. I tipi di token sono i seguenti.

|Token Name (Nome del token)|Tipo di token|
|----------------|----------------|
|namespace, class, public, void, int|parola chiave|
|=|Operatore|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identificatore|
|MyNamespace|namespace|
|MyClass|classe|
|Myfunction|method|
|arg1|parameter|
|var1|variabile locale|

 Il ruolo del parser è identificare i token. Alcuni token possono avere più di un tipo. Dopo che il parser ha identificato i token, il servizio di linguaggio può usare le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e le operazioni IntelliSense.

## <a name="types-of-parsers"></a>Tipi di parser
 Un parser del servizio di linguaggio non corrisponde a un parser usato come parte di un compilatore. Tuttavia, questo tipo di parser deve usare sia uno scanner che un parser, allo stesso modo di un parser del compilatore.

- Uno scanner viene usato per identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e per l'identificazione rapida dei tipi di token che possono attivare altre operazioni, ad esempio la corrispondenza tra parentesi. Questo scanner è rappresentato <xref:Microsoft.VisualStudio.Package.IScanner> dall'interfaccia .

- Un parser viene usato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengono usate nelle operazioni IntelliSense per identificare elementi del linguaggio, ad esempio metodi, variabili, parametri e dichiarazioni, e per fornire elenchi di membri e firme di metodo in base al contesto. Questo parser viene usato anche per individuare coppie di elementi di linguaggio corrispondenti, ad esempio parentesi graffe e parentesi. A questo parser si accede tramite <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> il metodo nella classe <xref:Microsoft.VisualStudio.Package.LanguageService> .

  La modalità di implementazione di uno scanner e di un parser per il servizio di linguaggio è l'utente. Sono disponibili diverse risorse che descrivono il funzionamento dei parser e come scrivere un parser personalizzato. Sono inoltre disponibili diversi prodotti gratuiti e commerciali che consentono di creare un parser.

### <a name="the-parsesource-parser"></a>The ParseSource Parser
 A differenza di un parser usato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), un parser del servizio di linguaggio può essere chiamato per diversi motivi e in molti contesti diversi. La modalità di implementazione di questo approccio <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nel metodo nella classe è <xref:Microsoft.VisualStudio.Package.LanguageService> l'utente. È importante tenere presente che il metodo potrebbe <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> essere chiamato su un thread in background.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura contiene un riferimento all'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Questo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto non può essere utilizzato nel thread in background. Di fatto, molte delle classi MPF di base non possono essere usate nel thread in background. Sono incluse le classi , , e qualsiasi altra classe che comunica direttamente o <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> indirettamente con la visualizzazione.

 Questo parser analizza in genere l'intero file di origine la prima volta che viene chiamato o quando viene specificato il valore del motivo <xref:Microsoft.VisualStudio.Package.ParseReason> di analisi di . Le chiamate successive al metodo gestiscono una piccola parte del codice analizzato e possono essere eseguite molto più rapidamente usando i risultati <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> dell'operazione di analisi completa precedente. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo comunica i risultati dell'operazione di analisi tramite gli oggetti e <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> . L'oggetto viene utilizzato per raccogliere informazioni per un motivo di analisi specifico, ad esempio informazioni sugli intervalli di parentesi graffe corrispondenti o firme di metodo con elenchi <xref:Microsoft.VisualStudio.Package.AuthoringSink> di parametri. fornisce raccolte di dichiarazioni e firme di metodo e supporta anche l'opzione di modifica avanzata Vai a ( Vai a definizione , Vai a dichiarazione <xref:Microsoft.VisualStudio.Package.AuthoringScope> , Vai a **riferimento**). 

### <a name="the-iscanner-scanner"></a>The IScanner Scanner
 È inoltre necessario implementare uno scanner che implementa <xref:Microsoft.VisualStudio.Package.IScanner> . Tuttavia, poiché questo scanner opera riga per riga tramite la classe , è in genere più <xref:Microsoft.VisualStudio.Package.Colorizer> facile da implementare. All'inizio di ogni riga, MPF assegna alla classe un valore da usare come variabile di stato <xref:Microsoft.VisualStudio.Package.Colorizer> passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornata. MPF memorizza nella cache queste informazioni sullo stato per ogni riga in modo che lo scanner possa iniziare l'analisi da qualsiasi riga senza dover iniziare dall'inizio del file di origine. Questa analisi veloce di una singola riga consente all'editor di fornire feedback rapido all'utente.

## <a name="parsing-for-matching-braces"></a>Analisi per le parentesi graffe corrispondenti
 In questo esempio viene illustrato il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura digitata dall'utente. In questo processo, lo scanner usato per la colorazione viene usato anche per determinare il tipo di token e se il token può attivare un'operazione di corrispondenza tra parentesi graffe. Se il trigger viene trovato, viene chiamato <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> il metodo per trovare la parentesi graffa corrispondente. Infine, le due parentesi graffe sono evidenziate.

 Anche se le parentesi graffe vengono usate nei nomi dei trigger e nei motivi di analisi, questo processo non è limitato alle parentesi graffe effettive. È supportata qualsiasi coppia di caratteri specificata come coppia corrispondente. Gli esempi includono ( e ), \< and > e [ e ].

 Si supponga che il servizio di linguaggio supporti le parentesi graffe corrispondenti.

1. L'utente tipizza una parentesi graffa di chiusura (}).

2. La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore viene avanzato di uno.

3. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo nella classe viene chiamato con la parentesi <xref:Microsoft.VisualStudio.Package.Source> graffa di chiusura tipizzata.

4. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama il metodo nella classe per ottenere il token nella posizione subito prima della posizione corrente <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> del <xref:Microsoft.VisualStudio.Package.Source> cursore. Questo token corrisponde alla parentesi graffa di chiusura tipizzata.

    1. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo chiama il metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> <xref:Microsoft.VisualStudio.Package.Colorizer> sull'oggetto per ottenere tutti i token nella riga corrente.

    2. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama il metodo <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> <xref:Microsoft.VisualStudio.Package.IScanner> sull'oggetto con il testo della riga corrente.

    3. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama ripetutamente il metodo <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> <xref:Microsoft.VisualStudio.Package.IScanner> sull'oggetto per raccogliere tutti i token dalla riga corrente.

    4. Il metodo chiama un metodo privato nella classe per ottenere il token che contiene la posizione desiderata e passa l'elenco <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> di token ottenuti dal metodo <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> .

5. Il metodo cerca un flag del trigger del token di nel token restituito dal metodo , cio' il token che rappresenta la parentesi <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> graffa di chiusura).

6. Se viene trovato il flag <xref:Microsoft.VisualStudio.Package.TokenTriggers> di trigger di , viene chiamato il metodo nella classe <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.Source> .

7. Il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo avvia un'operazione di analisi con il valore del motivo di analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Questa operazione chiama infine il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo sulla <xref:Microsoft.VisualStudio.Package.LanguageService> classe . Se l'analisi asincrona è abilitata, questa chiamata <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> al metodo si verifica in un thread in background.

8. Al termine dell'operazione di analisi, nella classe viene chiamato un gestore di completamento interno (noto anche come metodo di `HandleMatchBracesResponse` <xref:Microsoft.VisualStudio.Package.Source> callback). Questa chiamata viene eseguita automaticamente dalla <xref:Microsoft.VisualStudio.Package.LanguageService> classe di base, non dal parser.

9. Il `HandleMatchBracesResponse` metodo ottiene un elenco di intervalli dall'oggetto archiviato <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto . Un intervallo è una <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struttura che specifica un intervallo di righe e caratteri nel file di origine. Questo elenco di intervalli contiene in genere due intervalli, uno per le parentesi graffe di apertura e chiusura.

10. Il `HandleBracesResponse` metodo chiama il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sull'oggetto archiviato <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto . In questo modo vengono evidenziati gli intervalli.

11. Se la proprietà è abilitata, il metodo ottiene il testo incomprensito dall'intervallo corrispondente e visualizza i primi 80 caratteri dell'intervallo nella <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> barra di `HandleBracesResponse` stato. Questa soluzione funziona meglio se il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo include l'elemento di linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. La conversione è stata completata.

### <a name="summary"></a>Riepilogo
 L'operazione con parentesi graffe corrispondenti è in genere limitata a semplici coppie di elementi del linguaggio. Gli elementi più complessi, ad esempio le triple corrispondenti (" ", " " e " ", o `if(...)` `{` " `}` `else` ", " " e " "), `{` possono essere evidenziati come parte di un'operazione `}` di completamento delle parole. Ad esempio, al termine della parola "else", è possibile evidenziare l'istruzione `if` " " corrispondente. Se è presente una serie di istruzioni, è possibile evidenziarle tutte usando lo stesso meccanismo delle parentesi `if` / `else if` graffe corrispondenti. La classe di base lo supporta già, come indicato di seguito: lo scanner deve restituire il valore del trigger del token combinato con il valore del trigger per il token che si trova <xref:Microsoft.VisualStudio.Package.Source> prima della posizione del <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> cursore.

 Per altre informazioni, vedere [Corrispondenza delle parentesi graffe in un servizio di linguaggio legacy.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

## <a name="parsing-for-colorization"></a>Analisi per la colorazione
 Colorare il codice sorgente è semplice, è sufficiente identificare il tipo di token e restituire informazioni sul colore relative a tale tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe funge da intermediario tra l'editor e lo scanner per fornire informazioni sui colori su ogni token. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa l'oggetto per colorare una linea e per raccogliere informazioni sullo stato per <xref:Microsoft.VisualStudio.Package.IScanner> tutte le righe nel file di origine. Nelle classi del servizio di linguaggio MPF non è necessario eseguire l'override della classe perché comunica con lo <xref:Microsoft.VisualStudio.Package.Colorizer> scanner solo tramite <xref:Microsoft.VisualStudio.Package.IScanner> l'interfaccia . Specificare l'oggetto che implementa <xref:Microsoft.VisualStudio.Package.IScanner> l'interfaccia eseguendo l'override <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> del metodo sulla classe <xref:Microsoft.VisualStudio.Package.LanguageService> .

 Allo <xref:Microsoft.VisualStudio.Package.IScanner> scanner viene data una riga di codice sorgente tramite il metodo <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> . Le chiamate al metodo vengono ripetute per ottenere il token successivo nella riga finché la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> riga non viene esaurita. Per la colorazione, MPF considera tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di gestire l'origine proveniente da esso come linee. Inoltre, qualsiasi riga può essere passata allo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceva la variabile di stato dalla riga prima che la riga sia in fase di analisi.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe viene usata anche per identificare i trigger di token. Questi trigger indicano all'MPF che un token specifico può avviare un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché l'identificazione di tali trigger deve essere veloce e deve verificarsi in qualsiasi posizione, lo scanner è più adatto per questa attività.

 Per altre informazioni, vedere [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analisi per funzionalità e ambito
 L'analisi della funzionalità e dell'ambito richiede più impegno rispetto alla semplice identificazione dei tipi di token rilevati. Il parser deve identificare non solo il tipo di token, ma anche la funzionalità per cui viene usato il token. Ad esempio, un identificatore è solo un nome, ma nel linguaggio in cui si trova un identificatore può essere il nome di una classe, uno spazio dei nomi, un metodo o una variabile, a seconda del contesto. Il tipo generale del token può essere un identificatore, ma l'identificatore può avere anche altri significati, a seconda di che cos'è e dove è definito. Questa identificazione richiede che il parser abbia una conoscenza più approfondita del linguaggio analizzato. È qui che <xref:Microsoft.VisualStudio.Package.AuthoringSink> entra in campo la classe . La classe raccoglie informazioni su identificatori, metodi, coppie di linguaggio corrispondenti (ad esempio parentesi graffe e parentesi graffe) e triple di linguaggio (simili alle coppie di linguaggi, ad eccezione del fatto che sono presenti tre parti, ad esempio <xref:Microsoft.VisualStudio.Package.AuthoringSink> " " " " e " `foreach()` `{` `}` "). È anche possibile eseguire l'override della classe per supportare l'identificazione del codice, usata nella convalida anticipata dei punti di interruzione in modo che non sia necessario caricare il debugger, e la finestra Debug automatico, che mostra automaticamente variabili locali e parametri durante il debug di un programma e richiede al parser di identificare le variabili e i parametri locali appropriati oltre a quelli presentati dal <xref:Microsoft.VisualStudio.Package.AuthoringSink> debugger. 

 L'oggetto viene passato al parser come parte dell'oggetto e viene creato un nuovo oggetto ogni volta che viene creato <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> un nuovo <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo deve restituire un oggetto , che viene usato per gestire diverse operazioni <xref:Microsoft.VisualStudio.Package.AuthoringScope> IntelliSense. L'oggetto gestisce un elenco per le dichiarazioni e un elenco per i metodi, uno dei quali viene popolato, a seconda del <xref:Microsoft.VisualStudio.Package.AuthoringScope> motivo dell'analisi. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve essere implementata.

## <a name="see-also"></a>Vedi anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
