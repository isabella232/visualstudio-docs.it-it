---
title: Scanner e Parser servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84b569a843a3ee414143dbfffb0dba6e881f5567
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418381"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e parser dei servizi di linguaggio legacy
Il parser è il cuore del servizio di linguaggio. Le classi di lingua di Framework di pacchetto gestito (MPF) richiedono un parser del linguaggio per selezionare le informazioni sul codice di visualizzazione. Un parser separa il testo in token lessicale e quindi identifica i token dal tipo e funzionalità.

## <a name="discussion"></a>Discussione
 Di seguito è riportato un metodo c#.

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

|Nome del token|Tipo di token|
|----------------|----------------|
|spazio dei nomi, void pubblico, classe, int|keyword|
|=|operator|
|{ } ( ) ;|Delimitatore|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|classe|
|MyFunction|metodo|
|arg1|parametro|
|var1|variabile locale|

 Il ruolo del parser consiste nell'identificare il token. Alcuni token possono avere più di un tipo. Dopo che il parser ha identificato i token, il servizio di linguaggio può usare le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, corrispondenza parentesi e le operazioni IntelliSense.

## <a name="types-of-parsers"></a>Tipi di parser
 Un parser di servizio di linguaggio non è quello utilizzato per un parser utilizzato come parte di un compilatore. Tuttavia, questo tipo di parser deve usare uno scanner sia un parser, esattamente come un parser del compilatore.

- Uno scanner consente di identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e identificare rapidamente i tipi di token che possono attivare altre operazioni, ad esempio, corrispondenza parentesi graffe. Questo scanner è rappresentato dal <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia.

- Un parser viene utilizzato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengano utilizzate nelle operazioni di IntelliSense per identificare gli elementi del linguaggio, ad esempio metodi, variabili, parametri e le dichiarazioni e per fornire elenchi di membri e le firme del metodo basati sul contesto. Questo parser viene inoltre utilizzato per individuare coppie di elemento di linguaggi corrispondenti, ad esempio le parentesi graffe e parentesi. Questo parser è accessibile tramite il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

  Come implementare un scanner e parser per il servizio di linguaggio è responsabilità dell'utente. Sono disponibili diverse risorse che descrivono come funzionano i parser e spiega come scrivere un parser personalizzato. Inoltre, sono disponibili diversi prodotti gratuiti e commerciali che semplificano la creazione di un parser.

### <a name="the-parsesource-parser"></a>Il ParseSource Parser
 A differenza di un parser che viene usato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), un parser di servizio di linguaggio può essere chiamato per motivi diversi e in molti contesti diversi. Modalità di implementazione di questo approccio nel <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.LanguageService> classe è responsabilità dell'utente. È importante tenere presente che il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo può essere chiamato su un thread in background.

> [!CAUTION]
> Il <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura contiene un riferimento di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto. Ciò <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto non può essere utilizzato nel thread in background. Infatti, molte delle classi base di MPF non è utilizzabile nel thread in background. Sono inclusi i <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classi e qualsiasi altra classe che direttamente o indirettamente comunica con la vista.

 Questo parser in genere analizza l'ora del file la prima origine intera viene chiamato o quando l'analisi motivo valore <xref:Microsoft.VisualStudio.Package.ParseReason> viene assegnato. Le chiamate successive al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo gestiscono una piccola parte del codice analizzato e possono essere eseguite molto più rapidamente con i risultati dell'operazione di analisi completo precedente. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo comunica i risultati dell'operazione di analisi tramite il <xref:Microsoft.VisualStudio.Package.AuthoringSink> e <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetti. Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene usato per raccogliere informazioni per un motivo specifico di analisi, ad esempio, informazioni su intervalli di firme dei metodi con elenchi di parametri o graffe. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornisce le raccolte di dichiarazioni e le firme dei metodi e anche il supporto per Vai a avanzate per la modifica opzione (**Vai a definizione**, **Vai a dichiarazione**, **Vai a Fare riferimento a**).

### <a name="the-iscanner-scanner"></a>Lo Scanner IScanner
 È inoltre necessario implementare uno scanner che implementa <xref:Microsoft.VisualStudio.Package.IScanner>. Tuttavia, poiché questo scanner opera su una base di riga per riga tramite la <xref:Microsoft.VisualStudio.Package.Colorizer> (classe), è in genere più semplice da implementare. All'inizio di ogni riga, MPF consente il <xref:Microsoft.VisualStudio.Package.Colorizer> classe un valore da usare come una variabile di stato che viene passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornato. MPF memorizza nella cache queste informazioni sullo stato per ogni riga in modo che lo scanner è possibile avviare l'analisi da tutte le righe senza dover iniziare all'inizio del file di origine. Questa analisi veloce di una singola riga consente l'editor fornire commenti e suggerimenti rapidi per l'utente.

## <a name="parsing-for-matching-braces"></a>L'analisi per le parentesi graffe corrispondenti
 Questo esempio viene illustrato il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura che l'utente ha digitato. In questo processo, lo scanner utilizzato per la colorazione viene usato anche per determinare il tipo di token e indica se il token può attivare un'operazione di corrispondenza parentesi graffe. Se il trigger viene trovato, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> viene chiamato per trovare la parentesi graffa corrispondente. Infine, vengono evidenziate le due parentesi graffe.

 Anche se le parentesi graffe vengono utilizzate nei nomi dei trigger e analizzare i motivi, questo processo non è limitato per le parentesi graffe effettive. Qualsiasi coppia di caratteri specificato da una coppia corrispondente è supportato. Gli esempi includono (e), \< e >, e [e].

 Si supponga che il servizio di linguaggio supporta le parentesi graffe corrispondenti.

1. L'utente digita una parentesi graffa di chiusura (}).

2. La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore viene spostato in uno.

3. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> nel metodo il <xref:Microsoft.VisualStudio.Package.Source> classe viene chiamata con parentesi graffa di chiusura tipizzato.

4. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiamate al metodo il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo nel <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token in corrispondenza della posizione appena prima della posizione corrente del cursore. Questo token corrisponde a parentesi graffa di chiusura tipizzato).

    1. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiamate al metodo il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo su di <xref:Microsoft.VisualStudio.Package.Colorizer> oggetto per ottenere tutti i token nella riga corrente.

    2. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chiamate al metodo il <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodo su di <xref:Microsoft.VisualStudio.Package.IScanner> oggetto con il testo della riga corrente.

    3. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama ripetutamente il <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo su di <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per raccogliere tutti i token dalla riga corrente.

    4. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo chiama un metodo privato nel <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token che contiene la posizione desiderata e passa l'elenco dei token ottenuto dal <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> (metodo).

5. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo cerca un flag trigger token <xref:Microsoft.VisualStudio.Package.TokenTriggers> nel token restituito dal <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> (metodo), vale a dire il token che rappresenta la parentesi graffa di chiusura).

6. Se il trigger di flag del <xref:Microsoft.VisualStudio.Package.TokenTriggers> viene trovato, il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo nel <xref:Microsoft.VisualStudio.Package.Source> classe è denominata.

7. Il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo avvia un'operazione di analisi con il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questa operazione chiama infine il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo su di <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Se l'analisi asincrono è abilitato, la chiamata al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo si verifica su un thread in background.

8. Quando viene completata l'operazione di analisi, un gestore di completamento interna (noto anche come un metodo di callback) denominato `HandleMatchBracesResponse` viene chiamato <xref:Microsoft.VisualStudio.Package.Source> classe. Questa chiamata viene eseguita automaticamente dal <xref:Microsoft.VisualStudio.Package.LanguageService> classe base, non dal parser.

9. Il `HandleMatchBracesResponse` Ottiene l'elenco di intervalli dal <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto archiviato nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. (Un intervallo è un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struttura che specifica un intervallo di caratteri e le righe nel file di origine.) Questo elenco di intervalli contiene in genere due intervalli, rispettivamente per l'apertura e la parentesi graffe di chiusura.

10. Il `HandleBracesResponse` chiamate al metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodo sulle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto archiviato nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Ciò evidenzia gli intervalli specificati.

11. Se il <xref:Microsoft.VisualStudio.Package.LanguagePreferences> proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> è abilitata, il `HandleBracesResponse` metodo ottiene il testo che è incluso in modo diretto dall'intervallo di corrispondenza e visualizza i primi 80 caratteri di tale intervallo nella barra di stato. Questa situazione è ideale se le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo include l'elemento di linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Operazione eseguita.

### <a name="summary"></a>Riepilogo
 L'operazione di parentesi graffe corrispondenti è in genere limitata alle semplici coppie di elementi del linguaggio. Gli elementi più complessi, come la corrispondenza Triple ("`if(...)`","`{`"e"`}`", o "`else`","`{`"e"`}`"), potrebbe essere evidenziato come parte di un'operazione di completamento delle parole. Ad esempio, la parola "else" termine, la corrispondenza "`if`" istruzione potrebbe essere evidenziata. Se si sono verificati una serie di `if` / `else if` (istruzioni), tutti gli elementi potrebbe essere evidenziato usando lo stesso meccanismo come le parentesi graffe corrispondenti. Il <xref:Microsoft.VisualStudio.Package.Source> classe di base supporta già questa operazione, come indicato di seguito: Lo scanner deve restituire il valore del token di trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinato con il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> per il token che precede la posizione del cursore.

 Per altre informazioni, vedere [corrispondenza delle parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>L'analisi per la colorazione
 Colorazione di codice sorgente è semplice, identificare solo il tipo di informazioni sul colore token e restituiscono informazioni sul tipo. Il <xref:Microsoft.VisualStudio.Package.Colorizer> classe agisce come intermediario tra l'editor e lo scanner per specificare le informazioni di colore di ogni token. Il <xref:Microsoft.VisualStudio.Package.Colorizer> classe Usa il <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per facilitare il colorare una riga e anche per raccogliere informazioni sullo stato per tutte le righe nel file di origine. Nelle classi del servizio del linguaggio MPF, il <xref:Microsoft.VisualStudio.Package.Colorizer> classe non è necessario eseguire l'override perché comunica con lo scanner solo attraverso il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia. La fornitura dell'oggetto che implementa il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia eseguendo l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo sul <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Il <xref:Microsoft.VisualStudio.Package.IScanner> scanner viene data una riga del codice sorgente tramite la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> (metodo). Le chiamate al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo vengono ripetuti per ottenere il token successivo nella riga fino all'esaurimento dei token di riga. Per la colorazione, MPF gestisce tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di far fronte alle origine presto analizzarlo sotto forma di linee. Inoltre, qualsiasi riga renserlo passabile per lo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceva la variabile di stato dalla riga che precede la riga per eseguire l'analisi.

 Il <xref:Microsoft.VisualStudio.Package.Colorizer> classe viene utilizzata anche per identificare i trigger di token. Questi trigger indicano MPF che un determinato token può essere avviata un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché identificando tali trigger devono essere veloce e devono verificarsi in qualsiasi posizione, lo scanner è ideale per questa attività.

 Per altre informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>L'analisi per funzionalità e ambito
 Per ambito e funzionalità di analisi richiede uno sforzo maggiore semplicemente l'identificazione dei tipi di token che vengono rilevati. Il parser deve identificare non solo il tipo di token, ma anche le funzionalità per il quale il token viene usato. Ad esempio, un identificatore è solo un nome, ma nella propria lingua, un identificatore potrebbe essere il nome di una classe, spazio dei nomi, metodo o variabile, a seconda del contesto. Il tipo generale del token può essere un identificatore, ma l'identificatore può contenere anche altri significati, a seconda che cos'è e in cui è definito. Questa identificazione richiede che il parser per dispone di conoscenze più approfondite sull'utilizzo del linguaggio da analizzare. Si tratta di dove il <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe è disponibile in. Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe raccoglie informazioni su identificatori, metodi, le coppie di linguaggi corrispondenti (ad esempio le parentesi graffe e parentesi) e linguaggio Triple (simile a coppie di linguaggi, ad eccezione del fatto che siano presenti tre parti, ad esempio, "`foreach()`" "`{`"e"`}`"). Inoltre, è possibile eseguire l'override di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe per supportare l'identificazione del codice, che viene usato nella convalida anticipata dei punti di interruzione in modo che non deve essere caricato il debugger, e il **Auto** finestra di debug, che mostra locale variabili e parametri automaticamente quando un programma viene eseguito il debug e richiede il parser per identificare parametri oltre a quelli che presenta il debugger e variabili locali appropriate.

 Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene passato al parser come parte del <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto e un nuovo <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene creato ogni volta che un nuovo <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto viene creato. Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo deve restituire un <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto, che consente di gestire varie operazioni di IntelliSense. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto mantiene un elenco di dichiarazioni e l'elenco di metodi, ovvero di cui viene popolata, a seconda del motivo per l'analisi. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve essere implementata.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)