---
title: Parser e scanner del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726729"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e parser dei servizi di linguaggio legacy
Il parser è il fulcro del servizio di linguaggio. Per le classi di linguaggio del Framework di pacchetto gestito (MPF) è necessario un parser di linguaggio per selezionare informazioni sul codice visualizzato. Un parser separa il testo in token lessicali e quindi identifica i token in base al tipo e alla funzionalità.

## <a name="discussion"></a>Discussione
 Di seguito è riportato C# un metodo.

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
|namespace, Class, Public, void, int|keyword|
|=|operator|
|{ } ( ) ;|Delimitatore|
|MyNamespace, MyClass, funzione, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|classe|
|MyFunction|metodo|
|arg1|parametro|
|var1|Variabile locale|

 Il ruolo del parser consiste nell'identificare i token. Alcuni token possono avere più di un tipo. Dopo l'identificazione dei token da parte del parser, il servizio di linguaggio può usare le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e le operazioni di IntelliSense.

## <a name="types-of-parsers"></a>Tipi di parser
 Un parser del servizio di linguaggio non corrisponde a un parser usato come parte di un compilatore. Tuttavia, questo tipo di parser deve usare sia uno scanner che un parser, nello stesso modo in cui si tratta di un parser del compilatore.

- Uno scanner viene usato per identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e per l'identificazione rapida dei tipi di token che possono attivare altre operazioni, ad esempio la corrispondenza tra parentesi graffe. Questo scanner è rappresentato dall'interfaccia <xref:Microsoft.VisualStudio.Package.IScanner>.

- Un parser viene usato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengono usate nelle operazioni di IntelliSense per identificare gli elementi del linguaggio, ad esempio metodi, variabili, parametri e dichiarazioni, e per fornire elenchi di membri e firme di metodi in base al contesto. Questo parser viene utilizzato anche per individuare coppie di elementi di linguaggio corrispondenti, ad esempio parentesi graffe e parentesi. È possibile accedere a questo parser tramite il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nella classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

  Il modo in cui si implementa uno scanner e un parser per il servizio di linguaggio dipende dall'utente. Sono disponibili diverse risorse che descrivono il funzionamento dei parser e la modalità di scrittura del parser. Sono inoltre disponibili diversi prodotti gratuiti e commerciali che consentono di creare un parser.

### <a name="the-parsesource-parser"></a>Parser ParseSource
 Diversamente da un parser usato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), è possibile chiamare un parser del servizio di linguaggio per diversi motivi e in molti contesti diversi. La modalità di implementazione di questo approccio nel metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> nella classe <xref:Microsoft.VisualStudio.Package.LanguageService> dipende dall'utente. È importante tenere presente che il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> potrebbe essere chiamato su un thread in background.

> [!CAUTION]
> La struttura <xref:Microsoft.VisualStudio.Package.ParseRequest> contiene un riferimento all'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Impossibile utilizzare questo oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nel thread in background. Infatti, molte delle classi di base di MPF non possono essere utilizzate nel thread in background. Sono incluse le classi <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> e tutte le altre classi che comunicano direttamente o indirettamente con la visualizzazione.

 Questo parser in genere analizza l'intero file di origine la prima volta che viene chiamato o quando viene specificato il valore del motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason>. Le chiamate successive al metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> gestiscono una piccola parte del codice analizzato e possono essere eseguite molto più rapidamente usando i risultati dell'operazione di analisi completa precedente. Il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> comunica i risultati dell'operazione di analisi tramite gli oggetti <xref:Microsoft.VisualStudio.Package.AuthoringSink> e <xref:Microsoft.VisualStudio.Package.AuthoringScope>. L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> viene utilizzato per raccogliere informazioni per un motivo di analisi specifico, ad esempio, informazioni sugli intervalli di parentesi graffe o firme di metodo corrispondenti con elenchi di parametri. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornisce raccolte di dichiarazioni e firme del metodo e supporta anche l'opzione di modifica Vai a avanzata (**Vai a definizione**, **Vai a dichiarazione**, **Vai a riferimento**).

### <a name="the-iscanner-scanner"></a>Scanner di autocanner
 È inoltre necessario implementare uno scanner che implementi <xref:Microsoft.VisualStudio.Package.IScanner>. Tuttavia, poiché questo scanner opera su base riga per riga tramite la classe <xref:Microsoft.VisualStudio.Package.Colorizer>, è in genere più semplice da implementare. All'inizio di ogni riga, MPF assegna alla classe <xref:Microsoft.VisualStudio.Package.Colorizer> un valore da usare come variabile di stato passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornata. MPF memorizza nella cache le informazioni sullo stato per ogni riga in modo che lo scanner possa avviare l'analisi da qualsiasi riga senza dover iniziare all'inizio del file di origine. Questa analisi rapida di una singola riga consente all'editor di fornire un feedback rapido all'utente.

## <a name="parsing-for-matching-braces"></a>Analisi per parentesi graffe corrispondenti
 Questo esempio mostra il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura digitata dall'utente. In questo processo, lo scanner usato per la colorazione viene usato anche per determinare il tipo di token e se il token può attivare un'operazione di corrispondenza-parentesi graffa. Se il trigger viene trovato, viene chiamato il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> per trovare la parentesi graffa corrispondente. Infine, le due parentesi graffe vengono evidenziate.

 Anche se le parentesi graffe vengono usate nei nomi dei trigger e delle ragioni di analisi, questo processo non è limitato alle parentesi graffe effettive. Qualsiasi coppia di caratteri specificata come coppia corrispondente è supportata. Gli esempi includono (e), \< e > e [e].

 Si supponga che il servizio di linguaggio supporti le parentesi graffe corrispondenti.

1. L'utente digita una parentesi graffa chiusa (}).

2. La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore è avanzato di uno.

3. Il metodo <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> nella classe <xref:Microsoft.VisualStudio.Package.Source> viene chiamato con la parentesi graffa di chiusura tipizzata.

4. Il metodo <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiama il metodo <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> nella classe <xref:Microsoft.VisualStudio.Package.Source> per ottenere il token nella posizione immediatamente prima della posizione corrente del cursore. Questo token corrisponde alla parentesi graffa di chiusura tipizzata).

    1. Il metodo <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiama il metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> sull'oggetto <xref:Microsoft.VisualStudio.Package.Colorizer> per ottenere tutti i token nella riga corrente.

    2. Il metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chiama il metodo <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> sull'oggetto <xref:Microsoft.VisualStudio.Package.IScanner> con il testo della riga corrente.

    3. Il metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chiama ripetutamente il metodo <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> sull'oggetto <xref:Microsoft.VisualStudio.Package.IScanner> per raccogliere tutti i token dalla riga corrente.

    4. Il metodo <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiama un metodo privato nella classe <xref:Microsoft.VisualStudio.Package.Source> per ottenere il token che contiene la posizione desiderata e passa l'elenco dei token ottenuti dal metodo <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. Il metodo <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Cerca un flag di attivazione del token di <xref:Microsoft.VisualStudio.Package.TokenTriggers> sul token restituito dal metodo <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>; ovvero il token che rappresenta la parentesi graffa di chiusura.

6. Se viene trovato il flag del trigger di <xref:Microsoft.VisualStudio.Package.TokenTriggers>, viene chiamato il metodo <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> della classe <xref:Microsoft.VisualStudio.Package.Source>.

7. Il metodo <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> avvia un'operazione di analisi con il valore del motivo dell'analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questa operazione chiama infine il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sulla classe <xref:Microsoft.VisualStudio.Package.LanguageService>. Se l'analisi asincrona è abilitata, questa chiamata al metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> si verifica in un thread in background.

8. Al termine dell'operazione di analisi, viene chiamato un gestore di completamento interno (noto anche come metodo di callback) denominato `HandleMatchBracesResponse` nella classe <xref:Microsoft.VisualStudio.Package.Source>. Questa chiamata viene eseguita automaticamente dalla classe di base <xref:Microsoft.VisualStudio.Package.LanguageService> e non dal parser.

9. Il metodo `HandleMatchBracesResponse` ottiene un elenco di intervalli dall'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> archiviato nell'oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest>. Un intervallo è una struttura <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> che specifica un intervallo di righe e caratteri nel file di origine. Questo elenco di intervalli contiene in genere due intervalli, uno per le parentesi graffe di apertura e di chiusura.

10. Il metodo `HandleBracesResponse` chiama il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> sull'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> archiviato nell'oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest>. Vengono evidenziati gli intervalli specificati.

11. Se la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> è abilitata, il metodo `HandleBracesResponse` ottiene il testo incluso nell'intervallo corrispondente e Visualizza i primi 80 caratteri di tale intervallo nella barra di stato. Questa funzione è ottimale se il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> include l'elemento del linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Eseguita.

### <a name="summary"></a>Riepilogo
 L'operazione delle parentesi graffe corrispondenti è in genere limitata a coppie semplici di elementi del linguaggio. Elementi più complessi, ad esempio triple corrispondenti ("`if(...)`", "`{`" e "`}`" o "`else`", "`{`" e "`}`"), possono essere evidenziati come parte di un'operazione di completamento della parola. Ad esempio, quando la parola "else" viene completata, è possibile evidenziare l'istruzione "`if`" corrispondente. Se è presente una serie di `if` / istruzioni `else if`, tutte possono essere evidenziate usando lo stesso meccanismo delle parentesi graffe corrispondenti. La classe di base <xref:Microsoft.VisualStudio.Package.Source> supporta già questa operazione, come indicato di seguito: lo scanner deve restituire il valore del trigger del token <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinato con il valore del trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> per il token che precede la posizione del cursore.

 Per altre informazioni, vedere [corrispondenza tra parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analisi per la colorazione
 La colorazione del codice sorgente è semplice, è sufficiente identificare il tipo di token e restituire le informazioni sul colore per quel tipo. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> funge da intermediario tra l'editor e lo scanner per fornire informazioni sui colori per ogni token. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> usa l'oggetto <xref:Microsoft.VisualStudio.Package.IScanner> per facilitare la colorazione di una linea e anche per raccogliere informazioni sullo stato per tutte le righe nel file di origine. Nelle classi del servizio di linguaggio MPF, non è necessario eseguire l'override della classe <xref:Microsoft.VisualStudio.Package.Colorizer> perché comunica con lo scanner solo tramite l'interfaccia <xref:Microsoft.VisualStudio.Package.IScanner>. Si fornisce l'oggetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.Package.IScanner> eseguendo l'override del metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> nella classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

 Allo scanner <xref:Microsoft.VisualStudio.Package.IScanner> viene assegnata una riga di codice sorgente tramite il metodo <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>. Le chiamate al metodo <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> vengono ripetute per ottenere il token successivo nella riga finché la riga non viene esaurita dei token. Per la colorazione, MPF considera tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di far fronte all'origine come righe. Inoltre, qualsiasi riga può essere passata allo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceve la variabile di stato dalla riga prima della riga che sta per essere analizzata.

 La classe <xref:Microsoft.VisualStudio.Package.Colorizer> viene utilizzata anche per identificare i trigger del token. Questi trigger indicano a MPF che un determinato token può avviare un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché l'identificazione di tali trigger deve essere veloce e deve essere eseguita in qualsiasi posizione, lo scanner è più adatto per questa attività.

 Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analisi per funzionalità e ambito
 L'analisi per la funzionalità e l'ambito richiede più impegno rispetto alla semplice identificazione dei tipi di token rilevati. Il parser deve identificare non solo il tipo di token, ma anche la funzionalità per cui viene usato il token. Un identificatore, ad esempio, è semplicemente un nome, ma nella propria lingua un identificatore può essere il nome di una classe, uno spazio dei nomi, un metodo o una variabile, a seconda del contesto. Il tipo generale del token può essere un identificatore, ma l'identificatore può avere anche altri significati, a seconda della posizione e della posizione in cui è definito. Questa identificazione richiede che il parser disponga di una conoscenza più approfondita del linguaggio analizzato. Qui viene fornita la classe <xref:Microsoft.VisualStudio.Package.AuthoringSink>. La classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> raccoglie informazioni sugli identificatori, i metodi, le coppie di lingue corrispondenti (ad esempio parentesi graffe e parentesi) e le triple del linguaggio (simili alle coppie di lingue, ad eccezione del fatto che esistono tre parti, ad esempio "`foreach()`" "`{`" e "`}`") . Inoltre, è possibile eseguire l'override della classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> per supportare l'identificazione del codice, che viene utilizzata per la convalida anticipata dei punti di interruzione in modo che non sia necessario caricare il debugger e la finestra di debug **auto** , che Mostra variabili e parametri locali. automaticamente quando viene eseguito il debug di un programma e richiede che il parser identifichi le variabili e i parametri locali appropriati oltre a quelli presentati dal debugger.

 L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> viene passato al parser come parte dell'oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest> e viene creato un nuovo oggetto <xref:Microsoft.VisualStudio.Package.AuthoringSink> ogni volta che viene creato un nuovo oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest>. Inoltre, il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> deve restituire un oggetto <xref:Microsoft.VisualStudio.Package.AuthoringScope>, che viene utilizzato per gestire varie operazioni di IntelliSense. L'oggetto <xref:Microsoft.VisualStudio.Package.AuthoringScope> gestisce un elenco di dichiarazioni e un elenco per i metodi, ognuno dei quali è popolato, a seconda del motivo dell'analisi. È necessario implementare la classe <xref:Microsoft.VisualStudio.Package.AuthoringScope>.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)