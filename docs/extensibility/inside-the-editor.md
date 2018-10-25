---
title: All'interno dell'Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18587516298fa58e8a5e783ffb1f7c37d5a6b497
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859681"
---
# <a name="inside-the-editor"></a>All'interno dell'editor
L'editor è composto da un numero di sottosistemi diversi, che sono pensati per l'editor di testo modello separato dalla visualizzazione di testo e l'interfaccia utente.  
  
 Queste sezioni vengono descritti aspetti diversi dell'editor:  
  
- [Panoramica dei sottosistemi](../extensibility/inside-the-editor.md#overview-of-the-subsystems)  
  
- [Il modello di testo](../extensibility/inside-the-editor.md#the-text-model)  
  
- [Visualizzazione di testo.](../extensibility/inside-the-editor.md#the-text-view)  
  
  Queste sezioni descrivono le funzionalità dell'editor:  
  
- [Classificatori e i tag](../extensibility/inside-the-editor.md#tags-and-classifiers)  
  
- [Aree di controllo](../extensibility/inside-the-editor.md#adornments)  
  
- [Proiezione](../extensibility/inside-the-editor.md#projection)  
  
- [Struttura](../extensibility/inside-the-editor.md#outlining)  
  
- [Associazioni del mouse](../extensibility/inside-the-editor.md#mousebindings)  
  
- [Operazioni di editor](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a>Panoramica dei sottosistemi  
  
### <a name="text-model-subsystem"></a>Sottosistema di modello testo  
 Il sottosistema di modello di testo è responsabile per la rappresentazione di testo e consentendo la manipolazione. Il sottosistema di modello di testo contiene il <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia, che descrive la sequenza di caratteri che deve essere visualizzato dall'editor. Questo testo può essere modificato, rilevato e manipolato in caso contrario, in molti modi. Il modello di testo fornisce anche i tipi per gli aspetti seguenti:  
  
- Un servizio che associa i file di testo e gestisce la lettura e scrittura nel file system.  
  
- Un servizio di differenziazione che consente di trovare le differenze minime tra due sequenze di oggetti.  
  
- Un sistema per la descrizione di testo in un buffer in termini di subset del testo in altri buffer.  
  
  Il sottosistema di modello di testo è gratuito dei concetti dell'interfaccia utente. Ad esempio, non è responsabile della formattazione del testo o il layout del testo e non ha alcuna conoscenza di visuali che possono essere associati con il testo.  
  
  I tipi pubblici del sottosistema di modello di testo sono contenuti nel *Microsoft.VisualStudio.Text.Data.dll* e *Microsoft.VisualStudio.CoreUtility.dll*, che variano solo sulla base di .NET Framework libreria di classi e Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Sottosistema di visualizzazione testo  
 Il sottosistema di visualizzazione testo è responsabile della formattazione e visualizzazione di testo. I tipi in questo sottosistema sono suddivise in due livelli, a seconda del fatto che i tipi si basano su Windows Presentation Foundation (WPF). I tipi più importanti sono <xref:Microsoft.VisualStudio.Text.Editor.ITextView> e <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, che controllano il set di righe di testo che devono essere visualizzati e anche il punto di inserimento, la selezione e le funzionalità per la decorazione di testo con elementi UI di WPF. Questo sottosistema fornisce anche i margini intorno al testo dell'area di visualizzazione. I margini possono essere estese e possono contenere diversi tipi di effetti contenuti e visual. Riga numero consente di visualizzare e barre di scorrimento sono esempi dei margini.  
  
 I tipi pubblici del sottosistema di visualizzazione di testo sono contenuti nel *Microsoft.VisualStudio.Text.UI.dll* e *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Il primo assembly contiene gli elementi indipendenti dalla piattaforma e il secondo contiene gli elementi di specifiche di WPF.  
  
### <a name="classification-subsystem"></a>Sottosistema di classificazione  
 Il sottosistema di classificazione è responsabile di determinare le proprietà del carattere per il testo. Un classificatore suddivide il testo in diverse classi, ad esempio, "parola chiave" o "comment". La mappa di formato di classificazione è correlato queste classi per le proprietà del carattere effettivo, ad esempio, "Blue Consolas 10 pt". Queste informazioni vengano utilizzate per la visualizzazione di testo quando viene formattato e si esegue il rendering di testo. L'assegnazione di tag, che è descritti più dettagliatamente più avanti in questo argomento, abilita i dati da associare a intervalli di testo.  
  
 I tipi pubblici del sottosistema di classificazione sono contenuti in Microsoft.VisualStudio.Text.Logic.dll e interagiscono con gli aspetti visivi di classificazione, che sono contenuti nel Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Sottosistema di operazioni  
 Il sottosistema di operazioni definisce il comportamento dell'editor. Fornisce l'implementazione per i comandi dell'editor di Visual Studio e il sistema di annullamento.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Informazioni dettagliate sul modello di testo e la visualizzazione di testo  
  
### <a name="the-text-model"></a>Il modello di testo  
 Il sottosistema di modello di testo è costituito dai raggruppamenti diversi dei tipi di testo. Sono inclusi il buffer di testo, gli snapshot di testo e intervalli di testo.  
  
#### <a name="text-buffers-and-text-snapshots"></a>I buffer di testo e gli snapshot di testo  
 Il <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia rappresenta una sequenza di caratteri Unicode che vengono codificati con UTF-16, che è la codifica usata per il `String` tipo in .NET Framework. Un buffer di testo può essere reso persistente come un documento di file system, ma non è obbligatorio.  
  
 Il <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> viene usato per creare un buffer di testo vuoto o un buffer di testo che viene inizializzato da una stringa o da <xref:System.IO.TextReader>. Il buffer di testo può essere resi persistenti nel file System come un <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Il buffer di testo può essere modificato da qualsiasi thread fino a quando un thread acquisisce la proprietà del buffer di testo chiamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. In seguito, solo quel thread può eseguire modifiche.  
  
 Un buffer di testo può essere eseguita per molte versioni durante la sua durata. Una nuova versione viene generata ogni volta che il buffer viene modificato, mentre l'oggetto non modificabile <xref:Microsoft.VisualStudio.Text.ITextSnapshot> rappresenta il contenuto di tale versione del buffer. Poiché gli snapshot di testo non sono modificabili, è possibile accedere uno snapshot di testo in qualsiasi thread, senza restrizioni, anche se il buffer di testo che esso rappresenta in continua evoluzione.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Gli snapshot di testo e righe di testo dello snapshot  
 È possibile visualizzare il contenuto di uno snapshot di testo come una sequenza di caratteri o come una sequenza di righe. Caratteri e le righe sono che entrambi indicizzati a partire da zero. Uno snapshot di testo vuoto contiene zero caratteri e una riga vuota. Una riga è delimitata da qualsiasi sequenza di caratteri di interruzione di riga Unicode valido, o dall'inizio o alla fine del buffer. I caratteri di interruzione di riga sono rappresentati in modo esplicito nello snapshot di testo e le interruzioni di riga in uno snapshot di testo non devono essere tutte lo stesso.  
  
> [!NOTE]
>  Per altre informazioni sui caratteri di interruzione di riga nell'editor di Visual Studio, vedere [codifiche e interruzioni di riga](../ide/encodings-and-line-breaks.md).  
  
 Una riga di testo è rappresentata da un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> oggetto, che può essere ottenuto da uno snapshot di testo per un numero di riga specifico o per una particolare posizione di carattere.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Elementi SnapshotPoint SnapshotSpans e NormalizedSnapshotSpanCollections  
 Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint> rappresenta una posizione del carattere in uno snapshot. La posizione è garantita a essere compreso tra zero e la lunghezza dello snapshot. Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan> rappresenta un intervallo di testo in uno snapshot. Posizione finale è garantito a essere compreso tra zero e la lunghezza dello snapshot. Il <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> è costituito da un set di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> oggetti dello stesso snapshot.  
  
#### <a name="spans-and-normalizedspancollections"></a>Gli intervalli e NormalizedSpanCollections  
 Oggetto <xref:Microsoft.VisualStudio.Text.Span> rappresenta un intervallo che può essere applicato a un intervallo di testo in uno snapshot di testo. Le posizioni di snapshot sono in base zero, in modo che gli intervalli possono iniziare in qualsiasi posizione inclusi zero. Il `End` proprietà di un intervallo è uguale alla somma dei relativi `Start` proprietà e i relativi `Length` proprietà. Oggetto `Span` non include il carattere che verrà indicizzato per la `End` proprietà. Ad esempio, un intervallo che ha inizio = 5 e Length = 3 ha End = 8, e include i caratteri in corrispondenza delle posizioni 5, 6 e 7. La notazione per questo intervallo è 5..8).  
  
 Due intervalli si intersecano se dispongono di alcuna posizione in comune, tra cui la posizione finale. Pertanto, l'intersezione di [3, 5) e [2, 7) è [3, 5) e punto di intersezione tra [3, 5) e [5, 7) è [5, 5). (Si noti che [5, 5) è un intervallo vuoto.)  
  
 Due intervalli si sovrappongono se hanno le posizioni in comune, ad eccezione della posizione finale. Intervallo vuoto mai si sovrappone a qualsiasi altro intervallo e la sovrapposizione di due intervalli non è mai vuota.  
  
 Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> è riportato un elenco di intervalli in base all'ordine le proprietà di inizio degli intervalli. Nell'elenco di intervalli sovrapposti o adiacenti vengono uniti. Ad esempio, dato il set di intervalli [5..9), [0..1), [3..6), e [9..10), l'elenco normalizzato di intervalli è [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>Le notifiche di modifica ITextEdit, TextVersion e testo  
 Il contenuto di un buffer di testo può essere modificato utilizzando un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto. Creazione di tale tipo di oggetto (usando uno dei `CreateEdit()` metodi di <xref:Microsoft.VisualStudio.Text.ITextBuffer>) avvia una transazione di testo che è costituito da modifiche di testo. Ogni modifica è una sostituzione di un intervallo di testo nel buffer da una stringa. Le coordinate e il contenuto di ogni modifica sono espresse in relazione lo snapshot del buffer quando la transazione è stata avviata. Il <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto consente di regolare le coordinate di modifiche che sono interessate da altre modifiche nella stessa transazione.  
  
 Si consideri, ad esempio, un buffer di testo che contiene questa stringa:  
  
```  
abcdefghij  
```  
  
 Applicare una transazione che contiene due modifiche, una modifica che sostituisce l'intervallo di [2..4) utilizzando il carattere `X` e una seconda modifica che sostituisce l'intervallo di [6..9) utilizzando il carattere `Y`. Il risultato è il buffer:  
  
```  
abXefYj  
```  
  
 Le coordinate per la seconda modifica sono state calcolate per quanto riguarda il contenuto del buffer all'inizio della transazione, prima è stata applicata alla prima modifica.  
  
 Rendere effettive le modifiche al buffer durante la <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto commit viene eseguito chiamando relativo `Apply()` (metodo). Se si è verificato almeno una modifica non è vuoto, una nuova <xref:Microsoft.VisualStudio.Text.ITextVersion> viene creato un nuovo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> viene creato e uno `Changed` viene generato l'evento. Ogni versione di testo ha un altro snapshot di testo. Uno snapshot di testo rappresenta lo stato completo del buffer di testo dopo che una transazione di modifica, ma una versione testuale vengono descritte solo le modifiche da uno snapshot alla successiva. In generale, gli snapshot di testo sono concepiti per essere utilizzate una sola volta e quindi scartati, mentre le versioni di testo devono rimanere attive per un certo tempo.  
  
 Contiene una versione testuale un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Questa raccolta vengono descritte le modifiche che, quando applicato lo snapshot, verrà generato lo snapshot successivo. Ogni <xref:Microsoft.VisualStudio.Text.ITextChange> nella raccolta contiene la posizione di carattere della stringa sostituita, la modifica e la stringa di sostituzione. Stringa sostituita è vuota per un inserimento di base e la stringa di sostituzione è vuota per un'eliminazione di base. La raccolta normalizzata è sempre `null` per la versione più recente del buffer di testo.  
  
 Un solo <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto può essere creata un'istanza per un buffer di testo in qualsiasi momento e tutte le modifiche di testo devono essere eseguite sul thread che possiede il buffer di testo (se la proprietà è stato richiesto). Una modifica di testo può venire abbandonata chiamando relativi `Cancel` metodo o del relativo `Dispose` (metodo).  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> fornisce inoltre `Insert()`, `Delete()`, e `Replace()` metodi simili a quelle disponibili nel <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaccia. La chiamata di questi ha lo stesso effetto di creazione di un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto, effettua la chiamata simile e quindi applicare la modifica.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Track point e intervalli di rilevamento  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> rappresenta una posizione del carattere in un buffer di testo. Se il buffer viene modificato in modo che determina la posizione del carattere da spostare, il punto di rilevamento vengono spostati con essa. Ad esempio, se un punto di rilevamento si riferisce alla posizione 10 in un buffer e vengono inseriti cinque caratteri all'inizio del buffer, il punto di rilevamento quindi fa riferimento alla posizione 15. Se si verifica un inserimento in modo preciso la posizione indicata dal punto di rilevamento, il comportamento è determinato dal relativo <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, che può essere `Positive` o `Negative`. Se la modalità di verifica è positiva, il punto di rilevamento si riferisce allo stesso carattere, che ora è alla fine di inserimento. Se la modalità di rilevamento è negativa, il punto di rilevamento si riferisce al primo carattere inserito nella posizione originale. Se il carattere in corrispondenza della posizione rappresentato da un punto di rilevamento è stato eliminato, il punto di rilevamento passa al primo carattere che segue l'intervallo di eliminazione. Ad esempio, se un punto di rilevamento indica il carattere alla posizione 5 e vengono eliminati i caratteri nelle posizioni 3 a 6, il punto di rilevamento fa riferimento al carattere nella posizione 3.  
  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rappresenta un intervallo di caratteri anziché una sola posizione. Il comportamento è determinato dal relativo <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Se è la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, l'intervallo di rilevamento si espande per incorporare testo inserito nei suoi bordi; se è la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, intervallo di rilevamento non incorpora il testo inserito nei suoi bordi. Tuttavia, se è la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, un inserimento effettua il push della posizione corrente verso l'inizio e se la modalità di rilevamento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, la posizione corrente verso la fine di push di un inserimento.  
  
 È possibile ottenere la posizione di un punto di rilevamento o l'intervallo di un intervallo di rilevamento per tutti gli snapshot del buffer di testo a cui appartengono. Track point e intervalli di rilevamento può fare in modo sicuro riferimento da qualsiasi thread.  
  
#### <a name="content-types"></a>Tipi di contenuto  
 Tipi di contenuto sono un meccanismo per definire tipi diversi di contenuto. Un tipo di contenuto può essere un tipo di file, ad esempio "text", "code" o "binary" o un tipo di tecnologia, ad esempio "xml", "vb" o "c#". Ad esempio, la parola "using" è una parola chiave in c# e Visual Basic, ma non in altri linguaggi di programmazione. Pertanto, la definizione di questa parola chiave sarebbe limitata per i tipi di contenuto "c#" e "vb".  
  
 I tipi di contenuto vengono utilizzati come filtro per le aree di controllo e gli altri elementi dell'editor. Molte funzionalità dell'editor e punti di estensione definiti per ogni tipo di contenuto; colorazione del testo, ad esempio, è diversa per i file di testo normale, i file XML e file del codice sorgente Visual Basic. I buffer di testo sono in genere assegnati un tipo di contenuto quando vengono creati e il tipo di contenuto di un buffer di testo può essere modificato.  
  
 I tipi di contenuto possono multiplo-ereditare da altri tipi di contenuto. Il <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> consente di specificare più tipi di base come elementi padre di un tipo di contenuto specificato.  
  
 Gli sviluppatori possono definire i propri tipi di contenuto e registrarli utilizzando il <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Molte funzionalità dell'editor possono essere definite rispetto al tipo di contenuto specifico tramite la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Margini dell'editor, le aree di controllo e i gestori del mouse, ad esempio, possono essere definiti in modo che si applicano solo agli editor che consentono di visualizzare i tipi di contenuto specifici.  
  
###  <a name="the-text-view"></a>Visualizzazione di testo.  
 La parte di visualizzazione del modello model view controller (MVC) definisce la visualizzazione di testo, la formattazione della visualizzazione, elementi grafici, ad esempio la barra di scorrimento e il punto di inserimento. Tutti gli elementi di presentazione dell'editor di Visual Studio sono basati su WPF.  
  
#### <a name="text-views"></a>Visualizzazioni di testo  
 Il <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaccia è una rappresentazione indipendente dalla piattaforma di una visualizzazione di testo. Viene usato principalmente per visualizzare i documenti di testo in una finestra, ma può anche essere utilizzato per altri scopi, ad esempio, in una descrizione comando.  
  
 La visualizzazione di testo fa riferimento a diversi tipi di buffer di testo. Il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> proprietà fa riferimento a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> oggetto che fa riferimento a questi tre buffer di testo diverso: il buffer di dati, che è il buffer di dati a livello superiore, il buffer di modifica, in cui la modifica si verifica e buffer visivo, ovvero il buffer che è visualizzato nella visualizzazione di testo.  
  
 Il testo viene formattato in base i classificatori collegati al buffer di testo sottostante ed è decorato con i provider dell'area di controllo associati alla visualizzazione di testo stesso.  
  
#### <a name="the-text-view-coordinate-system"></a>Il sistema di coordinate di visualizzazione testo  
 Il sistema di coordinate di visualizzazione di testo specifica le posizioni nella visualizzazione di testo. In questo sistema di coordinate, il valore di x 0,0 corrisponde al bordo sinistro del testo viene visualizzato e il valore di y 0,0 corrisponde al bordo superiore del testo viene visualizzato. La coordinata x aumenta da sinistra a destra e la coordinata y aumenta dall'alto verso il basso.  
  
 Un riquadro di visualizzazione (la parte del testo visibile nella finestra di testo) non è possibile scorrere orizzontalmente allo stesso modo, è necessario scorrere verticalmente. Un riquadro di visualizzazione è necessario scorrere orizzontalmente modificando la coordinata sinistra in modo da spostarla rispetto all'area di disegno. Tuttavia, un riquadro di visualizzazione è possibile scorrere verticalmente solo modificando il testo viene eseguito il rendering, provocando un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> generazione dell'evento.  
  
 Distanze nel sistema di coordinate corrispondono ai pixel logici. Se la superficie di rendering di testo viene visualizzata senza una trasformazione in scala, un'unità di sistema di coordinate del rendering del testo corrisponde a un pixel sullo schermo.  
  
#### <a name="margins"></a>Margini  
 Il <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaccia rappresenta un margine e i controlli di visibilità di margine e le relative dimensioni. Esistono quattro i margini predefiniti, che sono denominati "Top", "Left", "Right" e "Basso" e sono collegati alla parte superiore, inferiore, sinistro o il bordo destro di una vista. I margini sono contenitori in cui possono essere inserito l'altro margine. L'interfaccia definisce i metodi che restituiscono le dimensioni del margine e la visibilità di un margine. I margini sono gli elementi visivi che forniscono informazioni aggiuntive sulla visualizzazione di testo a cui sono collegate. Ad esempio, il margine del numero di riga consente di visualizzare i numeri di riga per la visualizzazione di testo. Il margine del glifo consente di visualizzare elementi dell'interfaccia utente.  
  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia gestisce la creazione e posizionamento dei margini. I margini possono essere ordinati rispetto a altro margine. I margini con priorità più alta si trovano più vicino alla visualizzazione di testo. Ad esempio, se sono presenti due margini sinistro, margine A e B margin e margin B ha una priorità più bassa rispetto a margine A, B margine viene visualizzata a sinistra del margine A.  
  
#### <a name="the-text-view-host"></a>L'host della visualizzazione testo  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaccia contiene la visualizzazione di testo e qualsiasi decorazioni adiacenti che accompagnano la visualizzazione, ad esempio, le barre di scorrimento. L'host di visualizzazione di testo contiene inoltre i margini che sono associati a un bordo della visualizzazione.  
  
#### <a name="formatted-text"></a>Testo formattato  
 È costituito da testo che viene visualizzato in una visualizzazione di testo <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oggetti. Ogni riga della visualizzazione di testo corrisponde a una riga di testo nella visualizzazione di testo. Righe lunghe nel buffer di testo sottostante possono essere parzialmente oscurate (se non è abilitato il ritorno a capo) o suddivise in più righe di visualizzazione di testo. Il <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaccia contiene i metodi e proprietà per il mapping tra i caratteri e le coordinate e per le aree di controllo che possono essere associati con la riga.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> gli oggetti vengono creati utilizzando un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaccia. Se si è preoccupati solo per il testo attualmente visualizzato nella visualizzazione, è possibile ignorare l'origine della formattazione. Se si è interessati nel formato di testo che non è visualizzato nella visualizzazione (ad esempio, per supportare una Taglia testo RTF e incollare), è possibile usare <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> per formattare il testo in un buffer di testo.  
  
 La visualizzazione di testo formatta uno <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> alla volta.  
  
## <a name="editor-features"></a>Funzionalità dell'editor  
 Le funzionalità dell'editor sono progettate in modo che la definizione della funzionalità è separata dalla relativa implementazione. L'editor aggiunge le funzionalità seguenti:  
  
-   Classificatori e i tag  
  
-   Aree di controllo  
  
-   Proiezione  
  
-   struttura  
  
-   Associazioni del mouse e la chiave  
  
-   Operazioni e primitive  
  
-   IntelliSense  
  
### <a name="tags-and-classifiers"></a>Classificatori e i tag  
 I tag sono indicatori che sono associati a un intervallo di testo. Possano essere visualizzati in diversi modi, ad esempio, con colorazione del testo, sottolineature, elementi grafici o i popup. I classificatori sono un tipo di tag.  
  
 Altri tipi di tag sono <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> per l'evidenziazione del testo, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> per la struttura, e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> per errori di compilazione.  
  
#### <a name="classification-types"></a>Tipi di classificazione  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaccia rappresenta una classe di equivalenza, ovvero una categoria astratta di testo. Tipi di classificazione possono più-ereditare da altri tipi di classificazione. Ad esempio, le classificazioni del linguaggio di programmazione potrebbe includere "parola chiave", "comment" e "identificatore", che eredita da "code". Tipi di classificazione di linguaggio naturale potrebbero includere "sostantivo", "verbo" e "aggettivo", che ereditano da "lingua".  
  
#### <a name="classifications"></a>Classificazioni  
 Una classificazione è un'istanza di un determinato tipo di classificazione, in genere in un intervallo di testo. Oggetto <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> viene usato per rappresentare una classificazione. Un intervallo di classificazione può essere considerato come un'etichetta che copre un determinato intervallo di testo e indica al sistema che questo intervallo di testo è di un determinato tipo di classificazione.  
  
#### <a name="classifiers"></a>Classificatori  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> è un meccanismo che suddivide il testo in un set di classificazioni. Classificatori devono essere definiti per i tipi di contenuto specifici e creare un'istanza per i buffer di testo specifico. I client devono implementare <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per partecipare alla classificazione di testo.  
  
#### <a name="classifier-aggregators"></a>Aggregatori di classificazione  
 Un aggregatore di classificatore è un meccanismo che combina tutti i classificatori per buffer di uno testo in un solo set di classificazioni. Ad esempio, un classificatore c# sia un classificatore di lingua inglese è stato possibile creare classificazioni su un commento in un file c#. Prendere in considerazione questo commento:  
  
```  
// This method produces a classifier  
```  
  
 Un classificatore di c# potrebbe assegnare un'etichetta all'intero intervallo come commento e la funzione di classificazione in lingua inglese può classificare "produce" come "verbo" e "method" come "sostantivo". L'aggregatore genera un set di classificazioni non sovrapposti e il tipo del set si basa su tutti i contributi.  
  
 Un aggregatore di classificatore è anche un classificatore perché suddivide il testo in un set di classificazioni. Aggregatore di classificatori garantisce inoltre che non esistono Nessun classificazioni sovrapposte e che le classificazioni sono ordinate. Classificatori singoli sono liberi di restituire qualsiasi set di classificazioni degli aggiornamenti, in qualsiasi ordine e sovrapposti in alcun modo.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Formattazione di classificazione e la colorazione del testo  
 Formattazione del testo è un esempio di una funzionalità che si basa su classificazione di testo. Utilizzato dal livello di visualizzazione di testo per determinare la visualizzazione del testo in un'applicazione. L'area di formattazione di testo è dipendente da WPF, ma non la definizione di logica delle classificazioni.  
  
 Un formato di classificazione è un set di proprietà per un tipo di classificazione specifica di formattazione. Questi formati di ereditano il formato dell'elemento padre del tipo di classificazione.  
  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> è un mapping da un tipo di classificazione per un set di proprietà di formattazione del testo. L'implementazione della mappa di formato nell'editor gestisce tutte le esportazioni dei formati di classificazione.  
  
###   <a name="adornments"></a>Aree di controllo  
 Le aree di controllo sono effetti grafici che non sono direttamente correlati al tipo di carattere e colori dei caratteri nella visualizzazione di testo. Ad esempio, la sottolineatura sottolineatura ondulata rossa che consente di contrassegnare il codice non di compilazione in molti linguaggi di programmazione è un'area di controllo incorporato, e le descrizioni comando sono le aree di controllo popup. Le aree di controllo sono derivati da <xref:System.Windows.UIElement> e implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Due tipi specializzati di tag dell'area di controllo sono le <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, per le aree di controllo che occupano lo stesso spazio come testo in una vista, e il <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, per la sottolineatura a zigzag.  
  
 Le aree di controllo incorporate sono immagini che fanno parte della visualizzazione di testo formattato. Essi sono organizzati in diversi livelli di Z order. Esistono tre livelli predefiniti, come indicato di seguito: testo, il punto di inserimento e la selezione. Tuttavia, gli sviluppatori possono definire più livelli e inserirli in ordine di uno rispetto a altro. I tre tipi di aree di controllo incorporate sono le aree di controllo relativo al testo (che lo spostamento quando si sposta il testo e vengono eliminati quando viene eliminato il testo), le aree di controllo relativo alla visualizzazione, che hanno a che fare con parti non di testo della visualizzazione, e inclusi nel controllo proprietario aree di controllo (i per gli sviluppatori devono gestire la loro posizione).  
  
 Le aree di controllo popup sono immagini che vengono visualizzati in una finestra piccola sopra la visualizzazione di testo, ad esempio, le descrizioni comandi.  
  
###  <a name="projection"></a> Proiezione  
 Proiezione è una tecnica per la costruzione di un tipo diverso di buffer di testo che non archivia effettivamente il testo, ma invece Combina testo dagli altri buffer di testo. Ad esempio, un buffer di proiezione utilizzabile per concatenare il testo di due altri buffer e presentare i risultati come se fosse in un solo buffer o per nascondere le parti del testo in un buffer. Un buffer di proiezione può fungere da buffer di origine a un altro buffer di proiezione. È possibile costruire un set di buffer che sono correlati tramite proiezione per ridisporre il testo in molti modi diversi. (Un set di questo tipo è noto anche come un *grafico del buffer*.) La funzionalità di struttura di testo di Visual Studio viene implementata usando un buffer di proiezione per nascondere il testo compresso e l'editor di Visual Studio per le pagine ASP.NET utilizza proiezione per il supporto incorporati linguaggi quali Visual Basic e c#.  
  
 Un' <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> viene creato usando <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Rappresentato da una sequenza ordinata di un buffer di proiezione <xref:Microsoft.VisualStudio.Text.ITrackingSpan> gli oggetti che sono note come *intervalli di origine*. Il contenuto di questi intervalli viene presentato come una sequenza di caratteri. I buffer di testo da cui vengono disegnati gli intervalli di origine vengono denominati *buffer di origine*. I client di un buffer di proiezione non sono necessario tenere presente che differisce da un buffer di testo normale.  
  
 Il buffer di proiezione è in ascolto degli eventi di modifica testo nel buffer di origine. Quando il testo in un'origine estendono le modifiche, il buffer di proiezione le coordinate di testo modificato viene eseguito il mapping a un proprio coordinate e genera eventi di modifica di testo appropriato. Ad esempio, prendere in considerazione i buffer di origine A e B che hanno questi contenuti:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Se il buffer di proiezione P è costituito da due intervalli di testo, uno che dispone di tutti i buffer A e l'altri dotato di tutti i buffer B, P dispone il contenuto seguente:  
  
```  
P: ABCDEvwxyz  
```  
  
 Se la sottostringa `xy` vengono eliminati dal buffer B, il buffer P genera un evento che indica se i caratteri nelle posizioni 7 e 8 sono stati eliminati.  
  
 Il buffer di proiezione può anche essere modificato direttamente. Propaga le modifiche al buffer di origine appropriato. Ad esempio, se una stringa viene inserita nel buffer P in posizione 6 (vale a dire la posizione originale del carattere "v"), l'inserimento viene propagato al buffer B nella posizione 1.  
  
 Esistono restrizioni per gli intervalli di origine che contribuiscono a un buffer di proiezione. Intervalli di origine non possono sovrapporsi; un percorso in un buffer di proiezione non è possibile eseguire il mapping a più di una posizione nel buffer qualsiasi origine e un percorso in un buffer di origine non è possibile eseguire il mapping a più di una posizione in un buffer di proiezione. Nessun circularities sono consentite nella relazione di buffer di origine.  
  
 Gli eventi vengono generati quando il set di origine nel buffer per la modifica di un buffer di proiezione e se il set di origine è esteso a modifiche.  
  
 Un buffer di elisione è un tipo speciale di buffer di proiezione. Viene principalmente utilizzato per la struttura e per le operazioni che espandere e comprimere blocchi di testo. Un buffer di elisione si basa su un solo buffer di origine e gli intervalli in buffer di elisione devono essere ordinati allo stesso modo come vengono ordinati nel buffer di origine.  
  
#### <a name="the-buffer-graph"></a>Grafico del buffer  
 Il <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaccia attiva il mapping tra un grafico del buffer di proiezione. Tutti i buffer di testo e i buffer di proiezione vengono raccolti in un grafo aciclico diretto, molto simile all'albero sintattico astratto generato da un compilatore di linguaggio. Il grafico è definito dal buffer superiore, che può essere qualsiasi buffer di testo. Grafico del buffer può eseguire il mapping da un punto nel buffer superiore a un punto nel buffer di origine o da un intervallo nel buffer superiore a un set di intervalli in un buffer di origine. Analogamente, può eseguire il mapping di un punto o spaziano da un buffer di origine a un punto nel buffer superiore. Buffer grafici vengono creati utilizzando il <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
#### <a name="events-and-projection-buffers"></a>Gli eventi e i buffer di proiezione  
 Quando viene modificato un buffer di proiezione, le modifiche vengono inviate dal buffer di proiezione per i buffer che dipendono da esso. Dopo che tutti i buffer sono stati modificati, vengono generati gli eventi di modifica del buffer, a partire con il buffer più in basso.  
  
###  <a name="outlining"></a> La struttura  
 La struttura è la possibilità di espandere o comprimere diversi blocchi di testo in una visualizzazione di testo. La struttura viene definita come una sorta di <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, nello stesso modo in sono definite le aree di controllo. Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> è un tag che definisce un'area di testo che può essere espansi o compressi. Per usare la struttura, è necessario importare il <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> per ottenere un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Il gestore della struttura enumera comprime e si espande i blocchi diversi, rappresentati come <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> oggetti e genera eventi di conseguenza.  
  
###  <a name="mousebindings"></a> Associazioni del mouse  
 Le associazioni del mouse collegano spostamenti del mouse a comandi diversi. Vengono definite le associazioni del mouse con un' <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, e tasti di scelta rapida vengono definiti utilizzando un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automaticamente crea un'istanza di tutte le associazioni e li connette agli eventi del mouse nella visualizzazione.  
  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaccia contiene i gestori di eventi di pre-elaborazione e post-elaborazione per gli eventi di mouse diversa. Handle uno degli eventi, è possibile ignorare alcuni dei metodi in <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Operazioni di editor  
 Editor operazioni possono essere utilizzate per automatizzare l'interazione con l'editor, per la creazione di script o altri scopi. È possibile importare il <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> alle operazioni di accesso su un determinato <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. È quindi possibile utilizzare questi oggetti per modificare la selezione, scorrere la visualizzazione o spostare il punto di inserimento in diverse parti della visualizzazione.  
  
###  <a name="intellisense"></a> IntelliSense  
 Completamento delle istruzioni, supporto per la firma (detta anche informazioni sul parametro), informazioni rapide e lampadine supportate da IntelliSense.  
  
 Completamento delle istruzioni fornisce elenchi popup dei completamenti possibili per i nomi dei metodi, gli elementi XML e altri elementi di codice o markup. In generale, un movimento dell'utente richiama una sessione di completamento. La sessione viene visualizzato l'elenco di completamenti possibili e l'utente può selezionare uno o ignorare l'elenco. Il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> è responsabile della creazione e l'attivazione di <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcola il <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> degli elementi di completamento per la sessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)   
 [Importazioni dell'editor](../extensibility/editor-imports.md)
