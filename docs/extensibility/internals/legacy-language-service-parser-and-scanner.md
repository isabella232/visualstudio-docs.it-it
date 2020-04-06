---
title: Parser e scanner del servizio di linguaggio legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707321"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e parser dei servizi di linguaggio legacy
Il parser è il cuore del servizio di linguaggio. Le classi di linguaggio Managed Package Framework (MPF) richiedono un parser del linguaggio per selezionare le informazioni sul codice visualizzato. Un parser separa il testo in token lessicali e quindi identifica tali token per tipo e funzionalità.

## <a name="discussion"></a>Discussione
 Di seguito è riportato un metodo di C.

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

 In questo esempio, i token sono le parole e i segni di punteggiatura. I tipi di token sono i seguenti.

|Nome token|Tipo di token|
|----------------|----------------|
|spazio dei nomi, classe, pubblico, void, int|parola chiave|
|=|operator|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identificatore|
|Spazio dei nomi|namespace|
|MyClass|classe|
|Myfunction|method|
|arg1|parametro|
|var1 (informazioni in base al t|variabile locale|

 Il ruolo del parser consiste nell'identificare i token. Alcuni token possono avere più di un tipo. Dopo che il parser ha identificato i token, il servizio di linguaggio può utilizzare le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e le operazioni intelliSense.After the parser has identified the tokens, the language service can use the information to provide helpful features, such as syntax highlighting, brace matching, and the IntelliSense operations.

## <a name="types-of-parsers"></a>Tipi di parser
 Un parser del servizio di linguaggio non corrisponde a un parser utilizzato come parte di un compilatore. Tuttavia, questo tipo di parser deve utilizzare sia uno scanner che un parser, allo stesso modo di un parser del compilatore.

- Uno scanner viene utilizzato per identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e per l'identificazione rapida dei tipi di token che possono attivare altre operazioni, ad esempio la corrispondenza tra parentesi. Questo scanner è <xref:Microsoft.VisualStudio.Package.IScanner> rappresentato dall'interfaccia.

- Un parser viene utilizzato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengono utilizzate nelle operazioni di IntelliSense per identificare gli elementi del linguaggio, ad esempio metodi, variabili, parametri e dichiarazioni, e per fornire elenchi di membri e firme di metodi in base al contesto. Questo parser viene utilizzato anche per individuare le coppie di elementi del linguaggio corrispondenti, ad esempio parentesi graffe e parentesi. Questo parser è <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> accessibile <xref:Microsoft.VisualStudio.Package.LanguageService> tramite il metodo nella classe.

  La modalità di implementazione di uno scanner e di un parser per il servizio di linguaggio è a vostra base. Sono disponibili diverse risorse che descrivono come funzionano i parser e come scrivere un parser personalizzato. Inoltre, sono disponibili diversi prodotti gratuiti e commerciali che aiutano nella creazione di un parser.

### <a name="the-parsesource-parser"></a>Il parser ParseSourceThe ParseSource Parser
 A differenza di un parser che viene utilizzato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), un parser del servizio di linguaggio può essere chiamato per molti motivi diversi e in molti contesti diversi. La modalità di <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> implementazione <xref:Microsoft.VisualStudio.Package.LanguageService> di questo approccio nel metodo nella classe spetta a te. È importante tenere presente che <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> il metodo potrebbe essere chiamato su un thread in background.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura contiene un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> riferimento all'oggetto. Questo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto non può essere utilizzato nel thread in background. Infatti, molte delle classi MPF di base non possono essere utilizzate nel thread in background. Sono incluse <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>le <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classi , , e qualsiasi altra classe che comunica direttamente o indirettamente con la visualizzazione.

 Questo parser analizza in genere l'intero file di origine la <xref:Microsoft.VisualStudio.Package.ParseReason> prima volta che viene chiamato o quando viene fornito il valore del motivo di analisi. Le chiamate <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> successive al metodo gestiscono una piccola parte del codice analizzato e possono essere eseguite molto più rapidamente utilizzando i risultati dell'operazione di analisi completa precedente. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo comunica i risultati dell'operazione <xref:Microsoft.VisualStudio.Package.AuthoringSink> di <xref:Microsoft.VisualStudio.Package.AuthoringScope> analisi tramite gli oggetti e . L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> viene utilizzato per raccogliere informazioni per un motivo di analisi specifico, ad esempio informazioni sugli intervalli di parentesi graffe o firme di metodo corrispondenti che dispongono di elenchi di parametri. Fornisce <xref:Microsoft.VisualStudio.Package.AuthoringScope> raccolte di dichiarazioni e firme di metodo e supporta anche l'opzione di modifica avanzata Vai a (**Vai a definizione**, **Vai a dichiarazione**, **Vai a riferimento**).

### <a name="the-iscanner-scanner"></a>Lo scanner IScanner
 È inoltre necessario implementare <xref:Microsoft.VisualStudio.Package.IScanner>uno scanner che implementa . Tuttavia, poiché questo scanner funziona riga per <xref:Microsoft.VisualStudio.Package.Colorizer> riga tramite la classe , è in genere più semplice da implementare. All'inizio di ogni riga, MPF assegna alla <xref:Microsoft.VisualStudio.Package.Colorizer> classe un valore da utilizzare come variabile di stato che viene passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornata. MPF memorizza nella cache queste informazioni sullo stato per ogni riga in modo che lo scanner possa iniziare l'analisi da qualsiasi riga senza dover iniziare all'inizio del file di origine. Questa scansione rapida di una singola riga consente all'editor di fornire un feedback rapido all'utente.

## <a name="parsing-for-matching-braces"></a>Analisi delle parentesi graffe corrispondenti
 Questo esempio mostra il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura digitata dall'utente. In questo processo, lo scanner utilizzato per la colorazione viene utilizzato anche per determinare il tipo di token e se il token può attivare un'operazione di corrispondenza parentesi graffe. Se il trigger viene <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> trovato, viene chiamato il metodo per trovare la parentesi graffa corrispondente. Infine, vengono evidenziate le due parentesi graffe.

 Anche se le parentesi graffe vengono utilizzate nei nomi dei trigger e dei motivi di analisi, questo processo non è limitato alle parentesi graffe effettive. È supportata qualsiasi coppia di caratteri specificata come coppia corrispondente. Gli esempi includono \< ( e ) e > e [ e ].

 Si supponga che il servizio di linguaggio supporta le parentesi graffe corrispondenti.

1. L'utente digita una parentesi graffa di chiusura (Sezione ).

2. La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore viene avanzato di uno.

3. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo <xref:Microsoft.VisualStudio.Package.Source> nella classe viene chiamato con la parentesi graffa di chiusura tipizzata.

4. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiama il <xref:Microsoft.VisualStudio.Package.Source> metodo nella classe per ottenere il token nella posizione appena prima della posizione corrente del cursore. Questo token corrisponde alla parentesi graffa di chiusura tipa).

    1. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chiama il <xref:Microsoft.VisualStudio.Package.Colorizer> metodo sull'oggetto per ottenere tutti i token nella riga corrente.

    2. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> chiama il <xref:Microsoft.VisualStudio.Package.IScanner> metodo sull'oggetto con il testo della riga corrente.

    3. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> ripetutamente <xref:Microsoft.VisualStudio.Package.IScanner> il metodo sull'oggetto per raccogliere tutti i token dalla riga corrente.

    4. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo chiama un <xref:Microsoft.VisualStudio.Package.Source> metodo privato nella classe per ottenere il token che contiene la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> posizione desiderata e passa l'elenco di token ottenuti dal metodo.

5. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo cerca un flag <xref:Microsoft.VisualStudio.Package.TokenTriggers> di trigger di token <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> di nel token restituito dal metodo; ovvero il token che rappresenta la parentesi graffa di chiusura).

6. Se viene trovato <xref:Microsoft.VisualStudio.Package.TokenTriggers> il flag <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> di <xref:Microsoft.VisualStudio.Package.Source> trigger di, viene chiamato il metodo nella classe .

7. Il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo avvia un'operazione di analisi <xref:Microsoft.VisualStudio.Package.ParseReason>con il valore del motivo di analisi di . Questa operazione chiama <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> infine il <xref:Microsoft.VisualStudio.Package.LanguageService> metodo sulla classe. Se l'analisi asincrona è abilitata, questa chiamata al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo si verifica in un thread in background.

8. Al termine dell'operazione di analisi, `HandleMatchBracesResponse` nella <xref:Microsoft.VisualStudio.Package.Source> classe viene chiamato un gestore di completamento interno (noto anche come metodo di callback). Questa chiamata viene effettuata automaticamente dalla classe <xref:Microsoft.VisualStudio.Package.LanguageService> base, non dal parser.

9. Il `HandleMatchBracesResponse` metodo ottiene un elenco di <xref:Microsoft.VisualStudio.Package.AuthoringSink> intervalli dall'oggetto archiviato nell'oggetto. <xref:Microsoft.VisualStudio.Package.ParseRequest> (Un intervallo <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> è una struttura che specifica un intervallo di righe e caratteri nel file di origine.) Questo elenco di intervalli contiene in genere due intervalli, uno per le parentesi graffe di apertura e chiusura.

10. Il `HandleBracesResponse` metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> metodo sull'oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest> archiviato nell'oggetto. Questo evidenzia le estensioni date.

11. Se <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> proprietà è `HandleBracesResponse` abilitata, il metodo ottiene il testo incluso nell'intervallo corrispondente e visualizza i primi 80 caratteri di tale intervallo nella barra di stato. Questo funziona meglio <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se il metodo include l'elemento del linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. La conversione è stata completata.

### <a name="summary"></a>Summary
 L'operazione di parentesi graffe corrispondenti è in genere limitata a semplici coppie di elementi del linguaggio. Elementi più complessi, come le`if(...)`triple`{`corrispondenti`}`(" "`else`" "`{`e`}`" " " " " " " " " e " "), possono essere evidenziati come parte di un'operazione di completamento delle parole. Ad esempio, quando la parola "else"`if`è terminata, l'istruzione corrispondente " " può essere evidenziata. Se fosse presente `if` / `else if` una serie di istruzioni, tutte potrebbero essere evidenziate utilizzando lo stesso meccanismo delle parentesi graffe corrispondenti. La <xref:Microsoft.VisualStudio.Package.Source> classe di base supporta già questo, come segue: <xref:Microsoft.VisualStudio.Package.TokenTriggers> lo scanner <xref:Microsoft.VisualStudio.Package.TokenTriggers> deve restituire il valore di trigger del token combinato con il valore di trigger per il token che si trova prima della posizione del cursore.

 Per ulteriori informazioni, vedere [Corrispondenza parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analisi per la colorazione
 Colorare il codice sorgente è semplice, basta identificare il tipo di token e restituire informazioni sul colore su quel tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe funge da intermediario tra l'editor e lo scanner per fornire informazioni sul colore di ogni token. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe <xref:Microsoft.VisualStudio.Package.IScanner> utilizza l'oggetto per facilitare la colorazione di una riga e anche per raccogliere informazioni sullo stato per tutte le righe nel file di origine. Nelle classi del servizio di <xref:Microsoft.VisualStudio.Package.Colorizer> linguaggio MPF, la classe non deve essere <xref:Microsoft.VisualStudio.Package.IScanner> sottoposta a override perché comunica con lo scanner solo tramite l'interfaccia. L'oggetto che implementa <xref:Microsoft.VisualStudio.Package.IScanner> l'interfaccia <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> esegue l'override del metodo sulla <xref:Microsoft.VisualStudio.Package.LanguageService> classe .

 Allo <xref:Microsoft.VisualStudio.Package.IScanner> scanner viene assegnata una riga <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> di codice sorgente tramite il metodo . Le chiamate <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> al metodo vengono ripetute per ottenere il token successivo nella riga fino all'esaurimento dei token da parte della riga. Per la colorazione, MPF considera tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di far fronte alla fonte proveniente da linee. Inoltre, qualsiasi riga può essere passata allo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceve la variabile di stato dalla riga prima della riga che sta per essere scansionata.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe viene utilizzata anche per identificare i trigger di token. Questi trigger indicano a MPF che un determinato token può avviare un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché l'identificazione di tali trigger deve essere veloce e deve essere eseguita in qualsiasi posizione, lo scanner è più adatto per questa attività.

 Per ulteriori informazioni, vedere [Colorazione della sintassi in un servizio](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)di linguaggio Legacy .

## <a name="parsing-for-functionality-and-scope"></a>Analisi per la funzionalità e l'ambito
 L'analisi per funzionalità e ambito richiede uno sforzo maggiore rispetto alla semplice identificazione dei tipi di token rilevati. Il parser deve identificare non solo il tipo di token, ma anche la funzionalità per cui viene utilizzato il token. Ad esempio, un identificatore è solo un nome, ma nel linguaggio, un identificatore potrebbe essere il nome di una classe, spazio dei nomi, metodo o variabile, a seconda del contesto. Il tipo generale del token può essere un identificatore, ma l'identificatore può anche avere altri significati, a seconda di ciò che è e dove è definito. Questa identificazione richiede al parser di avere una conoscenza più approfondita del linguaggio che viene analizzato. È qui <xref:Microsoft.VisualStudio.Package.AuthoringSink> che entra in gioco la classe. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe raccoglie informazioni su identificatori, metodi, coppie di lingue corrispondenti (ad esempio parentesi graffe e parentesi) e`foreach()`triple`{`di`}`lingua (simile alle coppie di lingue, ad eccezione del fatto che ci sono tre parti, ad esempio " " " " e " "). Inoltre, è possibile <xref:Microsoft.VisualStudio.Package.AuthoringSink> eseguire l'override della classe per supportare l'identificazione del codice, che viene utilizzata nella convalida anticipata dei punti di interruzione in modo che il debugger non debba essere caricato, e la finestra di debug **Auto,** che mostra automaticamente le variabili e i parametri locali quando è in corso il debug di un programma e richiede al parser di identificare le variabili locali appropriate e i parametri oltre a quelli che il debugger presenta.

 L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> viene passato al parser <xref:Microsoft.VisualStudio.Package.ParseRequest> come parte <xref:Microsoft.VisualStudio.Package.AuthoringSink> dell'oggetto e viene <xref:Microsoft.VisualStudio.Package.ParseRequest> creato un nuovo oggetto ogni volta che viene creato un nuovo oggetto. Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo deve <xref:Microsoft.VisualStudio.Package.AuthoringScope> restituire un oggetto, che viene utilizzato per gestire varie operazioni IntelliSense. L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringScope> gestisce un elenco per le dichiarazioni e un elenco per i metodi, uno dei quali viene popolato, a seconda del motivo dell'analisi. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve essere implementata.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
