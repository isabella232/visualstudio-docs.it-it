---
title: Parser e scanner del servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul parser e sullo scanner del servizio di linguaggio legacy che selezionano informazioni sul codice visualizzato.
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
ms.workload:
- vssdk
ms.openlocfilehash: 9c57bd9f8b71f861fd5be4176211af6907b27e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090837"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e parser dei servizi di linguaggio legacy
Il parser è il fulcro del servizio di linguaggio. Per le classi di linguaggio del Framework di pacchetto gestito (MPF) è necessario un parser di linguaggio per selezionare informazioni sul codice visualizzato. Un parser separa il testo in token lessicali e quindi identifica i token in base al tipo e alla funzionalità.

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

 In questo esempio, i token sono le parole e i segni di punteggiatura. I tipi di token sono i seguenti.

|Token Name (Nome del token)|Tipo di token|
|----------------|----------------|
|namespace, Class, Public, void, int|parola chiave|
|=|Operatore|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, funzione, arg1, var1|identificatore|
|MyNamespace|namespace|
|MyClass|classe|
|MyFunction|method|
|arg1|parameter|
|var1|variabile locale|

 Il ruolo del parser consiste nell'identificare i token. Alcuni token possono avere più di un tipo. Dopo l'identificazione dei token da parte del parser, il servizio di linguaggio può usare le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, la corrispondenza delle parentesi graffe e le operazioni di IntelliSense.

## <a name="types-of-parsers"></a>Tipi di parser
 Un parser del servizio di linguaggio non corrisponde a un parser usato come parte di un compilatore. Tuttavia, questo tipo di parser deve usare sia uno scanner che un parser, nello stesso modo in cui si tratta di un parser del compilatore.

- Uno scanner viene usato per identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e per l'identificazione rapida dei tipi di token che possono attivare altre operazioni, ad esempio la corrispondenza tra parentesi. Questo scanner è rappresentato dall' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia.

- Un parser viene usato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengono usate nelle operazioni di IntelliSense per identificare gli elementi del linguaggio, ad esempio metodi, variabili, parametri e dichiarazioni, e per fornire elenchi di membri e firme di metodi in base al contesto. Questo parser viene utilizzato anche per individuare coppie di elementi di linguaggio corrispondenti, ad esempio parentesi graffe e parentesi. È possibile accedere a questo parser tramite il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

  Il modo in cui si implementa uno scanner e un parser per il servizio di linguaggio dipende dall'utente. Sono disponibili diverse risorse che descrivono il funzionamento dei parser e la modalità di scrittura del parser. Sono inoltre disponibili diversi prodotti gratuiti e commerciali che consentono di creare un parser.

### <a name="the-parsesource-parser"></a>Parser ParseSource
 Diversamente da un parser usato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), è possibile chiamare un parser del servizio di linguaggio per diversi motivi e in molti contesti diversi. La modalità di implementazione di questo approccio nel <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo della <xref:Microsoft.VisualStudio.Package.LanguageService> classe dipende dall'utente. È importante tenere presente che il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo può essere chiamato su un thread in background.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura contiene un riferimento all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Impossibile utilizzare questo oggetto nel thread in background. Infatti, molte delle classi di base di MPF non possono essere utilizzate nel thread in background. Sono incluse le <xref:Microsoft.VisualStudio.Package.Source> classi,, <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> e qualsiasi altra classe che comunica direttamente o indirettamente con la visualizzazione.

 Questo parser in genere analizza l'intero file di origine la prima volta che viene chiamato o quando viene specificato il valore del motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Le chiamate successive al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metodo gestiscono una piccola parte del codice analizzato e possono essere eseguite molto più rapidamente usando i risultati dell'operazione di analisi completa precedente. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metodo comunica i risultati dell'operazione di analisi tramite gli <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetti e. L' <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene utilizzato per raccogliere informazioni per un motivo di analisi specifico, ad esempio, informazioni sugli intervalli di parentesi graffe o firme di metodo corrispondenti con elenchi di parametri. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Fornisce raccolte di dichiarazioni e firme del metodo e supporta anche l'opzione di modifica Vai a avanzata (**Vai a definizione**, **Vai a dichiarazione**, **Vai a riferimento**).

### <a name="the-iscanner-scanner"></a>Scanner di autocanner
 È inoltre necessario implementare uno scanner che implementi <xref:Microsoft.VisualStudio.Package.IScanner> . Tuttavia, poiché questo scanner opera su base riga per riga tramite la <xref:Microsoft.VisualStudio.Package.Colorizer> classe, è in genere più semplice da implementare. All'inizio di ogni riga, MPF fornisce alla <xref:Microsoft.VisualStudio.Package.Colorizer> classe un valore da usare come variabile di stato passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornata. MPF memorizza nella cache le informazioni sullo stato per ogni riga in modo che lo scanner possa avviare l'analisi da qualsiasi riga senza dover iniziare all'inizio del file di origine. Questa analisi rapida di una singola riga consente all'editor di fornire un feedback rapido all'utente.

## <a name="parsing-for-matching-braces"></a>Analisi per parentesi graffe corrispondenti
 Questo esempio mostra il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura digitata dall'utente. In questo processo, lo scanner usato per la colorazione viene usato anche per determinare il tipo di token e se il token può attivare un'operazione di corrispondenza-parentesi graffa. Se il trigger viene trovato, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> viene chiamato il metodo per trovare la parentesi graffa corrispondente. Infine, le due parentesi graffe vengono evidenziate.

 Anche se le parentesi graffe vengono usate nei nomi dei trigger e delle ragioni di analisi, questo processo non è limitato alle parentesi graffe effettive. Qualsiasi coppia di caratteri specificata come coppia corrispondente è supportata. Gli esempi includono (e), \< and > e [e].

 Si supponga che il servizio di linguaggio supporti le parentesi graffe corrispondenti.

1. L'utente digita una parentesi graffa chiusa (}).

2. La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore è avanzato di uno.

3. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo nella <xref:Microsoft.VisualStudio.Package.Source> classe viene chiamato con la parentesi graffa di chiusura tipizzata.

4. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo nella <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token nella posizione immediatamente prima della posizione corrente del cursore. Questo token corrisponde alla parentesi graffa di chiusura tipizzata).

    1. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo chiama il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo sull' <xref:Microsoft.VisualStudio.Package.Colorizer> oggetto per ottenere tutti i token nella riga corrente.

    2. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama il <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodo sull' <xref:Microsoft.VisualStudio.Package.IScanner> oggetto con il testo della riga corrente.

    3. Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama ripetutamente il <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo sull' <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per raccogliere tutti i token dalla riga corrente.

    4. Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo chiama un metodo privato nella <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token che contiene la posizione desiderata e passa l'elenco di token ottenuti dal <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo.

5. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo cerca un flag di trigger del token di <xref:Microsoft.VisualStudio.Package.TokenTriggers> nel token restituito dal <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo, ovvero il token che rappresenta la parentesi graffa di chiusura.

6. Se viene trovato il flag del trigger di <xref:Microsoft.VisualStudio.Package.TokenTriggers> , viene <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> chiamato il metodo nella <xref:Microsoft.VisualStudio.Package.Source> classe.

7. Il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo avvia un'operazione di analisi con il valore del motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Questa operazione chiama infine il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metodo sulla <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Se l'analisi asincrona è abilitata, questa chiamata al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo si verifica in un thread in background.

8. Al termine dell'operazione di analisi, viene chiamato un gestore di completamento interno (noto anche come metodo di callback) denominato `HandleMatchBracesResponse` nella <xref:Microsoft.VisualStudio.Package.Source> classe. Questa chiamata viene eseguita automaticamente dalla <xref:Microsoft.VisualStudio.Package.LanguageService> classe base, non dal parser.

9. Il `HandleMatchBracesResponse` metodo ottiene un elenco di intervalli dall' <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto archiviato nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Un intervallo è una <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struttura che specifica un intervallo di righe e caratteri nel file di origine. Questo elenco di intervalli contiene in genere due intervalli, uno per le parentesi graffe di apertura e di chiusura.

10. Il `HandleBracesResponse` metodo chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodo sull' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto archiviato nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Vengono evidenziati gli intervalli specificati.

11. Se la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> è abilitata, il `HandleBracesResponse` metodo ottiene il testo incluso nell'intervallo corrispondente e visualizza i primi 80 caratteri di tale intervallo nella barra di stato. Questa funzione è ottimale se il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo include l'elemento del linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. La conversione è stata completata.

### <a name="summary"></a>Riepilogo
 L'operazione delle parentesi graffe corrispondenti è in genere limitata a coppie semplici di elementi del linguaggio. È possibile evidenziare elementi più complessi, ad esempio triple corrispondenti (" `if(...)` ", " `{` " e " `}` ", "" `else` , "" `{` e " `}` ") come parte di un'operazione di completamento della parola. Ad esempio, quando la parola "else" viene completata, è `if` possibile evidenziare l'istruzione "" corrispondente. In presenza di una serie di `if` / `else if` istruzioni, tutte possono essere evidenziate utilizzando lo stesso meccanismo delle parentesi graffe corrispondenti. La <xref:Microsoft.VisualStudio.Package.Source> classe base supporta già questa operazione, come indicato di seguito: lo scanner deve restituire il valore del trigger del token <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinato con il valore <xref:Microsoft.VisualStudio.Package.TokenTriggers> di trigger per il token che precede la posizione del cursore.

 Per altre informazioni, vedere [corrispondenza tra parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analisi per la colorazione
 La colorazione del codice sorgente è semplice, è sufficiente identificare il tipo di token e restituire le informazioni sul colore per quel tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe funge da intermediario tra l'editor e lo scanner per fornire informazioni sui colori per ogni token. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa l' <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per facilitare la colorazione di una linea e anche per raccogliere informazioni sullo stato per tutte le righe nel file di origine. Nelle classi del servizio di linguaggio MPF, <xref:Microsoft.VisualStudio.Package.Colorizer> non è necessario eseguire l'override della classe perché comunica con lo scanner solo tramite l' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia. Si fornisce l'oggetto che implementa l' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia eseguendo l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Allo <xref:Microsoft.VisualStudio.Package.IScanner> scanner viene assegnata una riga di codice sorgente tramite il <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodo. Le chiamate al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo vengono ripetute per ottenere il token successivo nella riga fino a quando non viene esaurita la riga dei token. Per la colorazione, MPF considera tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di far fronte all'origine come righe. Inoltre, qualsiasi riga può essere passata allo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceve la variabile di stato dalla riga prima della riga che sta per essere analizzata.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe viene usata anche per identificare i trigger di token. Questi trigger indicano a MPF che un determinato token può avviare un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché l'identificazione di tali trigger deve essere veloce e deve essere eseguita in qualsiasi posizione, lo scanner è più adatto per questa attività.

 Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analisi per funzionalità e ambito
 L'analisi per la funzionalità e l'ambito richiede più impegno rispetto alla semplice identificazione dei tipi di token rilevati. Il parser deve identificare non solo il tipo di token, ma anche la funzionalità per cui viene usato il token. Un identificatore, ad esempio, è semplicemente un nome, ma nella propria lingua un identificatore può essere il nome di una classe, uno spazio dei nomi, un metodo o una variabile, a seconda del contesto. Il tipo generale del token può essere un identificatore, ma l'identificatore può avere anche altri significati, a seconda della posizione e della posizione in cui è definito. Questa identificazione richiede che il parser disponga di una conoscenza più approfondita del linguaggio analizzato. Qui viene fornita la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe raccoglie informazioni sugli identificatori, i metodi, le coppie di lingue corrispondenti (ad esempio parentesi graffe e parentesi) e le triple del linguaggio (simili alle coppie di lingue, ad eccezione del fatto che esistono tre parti, ad esempio, "" "" `foreach()` `{` e " `}` "). Inoltre, è possibile eseguire l'override della <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe per supportare l'identificazione del codice, che viene utilizzata per la convalida anticipata dei punti di interruzione in modo che non sia necessario caricare il debugger e la finestra di debug **auto** , che mostra automaticamente le variabili e i parametri locali durante il debug di un programma e richiede al parser di identificare le variabili e i parametri locali appropriati oltre a quelli presenti nel debugger.

 L' <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene passato al parser come parte dell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto e <xref:Microsoft.VisualStudio.Package.AuthoringSink> viene creato un nuovo oggetto ogni volta che <xref:Microsoft.VisualStudio.Package.ParseRequest> viene creato un nuovo oggetto. Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo deve restituire un <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto, che viene usato per gestire varie operazioni di IntelliSense. L' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto gestisce un elenco di dichiarazioni e un elenco per i metodi, ognuno dei quali è popolato, a seconda del motivo dell'analisi. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve essere implementata.

## <a name="see-also"></a>Vedi anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Panoramica dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
