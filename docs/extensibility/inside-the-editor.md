---
title: Componenti e funzionalità dell'editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710320"
---
# <a name="inside-the-editor"></a>All'interno dell'editor

L'editor è composto da diversi sottosistemi, che sono progettati per mantenere il modello di testo dell'editor separato dalla visualizzazione di testo e dall'interfaccia utente.

Queste sezioni descrivono diversi aspetti dell'editor:

- [Panoramica dei sottosistemi](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Il modello di testo](../extensibility/inside-the-editor.md#the-text-model)

- [La visualizzazione di testo](../extensibility/inside-the-editor.md#the-text-view)

Queste sezioni descrivono le funzionalità dell'editor:

- [Tag e classificatori](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ornamenti](../extensibility/inside-the-editor.md#adornments)

- [Proiezione](../extensibility/inside-the-editor.md#projection)

- [struttura](../extensibility/inside-the-editor.md#outlining)

- [Associazioni del mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operazioni dell'editore](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Panoramica dei sottosistemi

### <a name="text-model-subsystem"></a>Sottosistema del modello di testo

Il sottosistema del modello di testo è responsabile della rappresentazione del testo e dell'abilitazione della relativa manipolazione. Il sottosistema del <xref:Microsoft.VisualStudio.Text.ITextBuffer> modello di testo contiene l'interfaccia, che descrive la sequenza di caratteri che deve essere visualizzata dall'editor. Questo testo può essere modificato, tracciato e manipolato in altro modo in molti modi. Il modello di testo fornisce anche i tipi per i seguenti aspetti:

- Servizio che associa il testo ai file e gestisce la lettura e la scrittura nel file system.

- Servizio differenze che individua le differenze minime tra due sequenze di oggetti.

- Sistema per la descrizione del testo in un buffer in termini di sottoinsiemi del testo in altri buffer.

Il sottosistema del modello di testo è privo di concetti dell'interfaccia utente. Ad esempio, non è responsabile della formattazione del testo o del layout del testo e non ha alcuna conoscenza delle aree di controllo visive che possono essere associate al testo.

I tipi pubblici del sottosistema del modello di testo sono contenuti in *Microsoft.VisualStudio.Text.Data.dll* e *Microsoft.VisualStudio.CoreUtility.dll*, che dipendono solo dalla libreria di classi base di .NET Framework e da Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Sottosistema vista testo

Il sottosistema della visualizzazione di testo è responsabile della formattazione e della visualizzazione del testo. I tipi in questo sottosistema sono suddivisi in due livelli, a seconda che i tipi si basino su Windows Presentation Foundation (WPF). I tipi più <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>importanti sono e , che controllano il set di righe di testo da visualizzare, nonché il punto di inserimento, la selezione e le funzionalità per l'ornamento del testo tramite gli elementi dell'interfaccia utente WPF. Questo sottosistema fornisce anche margini intorno all'area di visualizzazione del testo. Questi margini possono essere estesi e possono contenere diversi tipi di contenuto ed effetti visivi. Esempi di margini sono le visualizzazioni dei numeri di riga e le barre di scorrimento.

I tipi pubblici del sottosistema di visualizzazione di testo sono contenuti in *Microsoft.VisualStudio.Text.UI.dll* e *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Il primo assembly contiene gli elementi indipendenti dalla piattaforma e il secondo contiene gli elementi specifici di WPFWPF.

### <a name="classification-subsystem"></a>Sottosistema di classificazione

Il sottosistema di classificazione è responsabile della determinazione delle proprietà dei caratteri per il testo. Un classificatore suddivide il testo in classi diverse, ad esempio "parola chiave" o "commento". La mappa del formato di classificazione mette in relazione queste classi con le proprietà del carattere effettive, ad esempio "Blue Consolas 10 pt". Queste informazioni vengono utilizzate dalla visualizzazione di testo durante la visualizzazione e il rendering del testo. L'aggiunta di tag, descritta in modo più dettagliato più avanti in questo argomento, consente di associare i dati agli intervalli di testo.

I tipi pubblici del sottosistema di classificazione sono contenuti in Microsoft.VisualStudio.Text.Logic.dll e interagiscono con gli aspetti visivi della classificazione, contenuti in Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sottosistema delle operazioni

Il sottosistema delle operazioni definisce il comportamento dell'editor. Fornisce l'implementazione per i comandi dell'editor di Visual Studio e il sistema di annullamento.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Uno sguardo più da vicino al modello di testo e alla vista di testo

### <a name="the-text-model"></a>Il modello di testo

Il sottosistema del modello di testo è costituito da diversi raggruppamenti di tipi di testo. Questi includono il buffer di testo, le istantanee di testo e le estensioni di testo.

#### <a name="text-buffers-and-text-snapshots"></a>Buffer di testo e istantanee di testo

L'interfaccia <xref:Microsoft.VisualStudio.Text.ITextBuffer> rappresenta una sequenza di caratteri Unicode codificati utilizzando UTF-16, ovvero la codifica utilizzata dal `String` tipo in .NET Framework. Un buffer di testo può essere reso persistente come documento del file system, ma questa operazione non è necessaria.

L'oggetto <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> viene utilizzato per creare un buffer di testo vuoto o <xref:System.IO.TextReader>un buffer di testo inizializzato da una stringa o da . Il buffer di testo può essere salvato <xref:Microsoft.VisualStudio.Text.ITextDocument>in modo permanente nel file system come file .

Qualsiasi thread può modificare il buffer di testo fino <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>a quando un thread assume la proprietà del buffer di testo chiamando . Dopo di che, solo quel thread può eseguire modifiche.

Un buffer di testo può passare attraverso molte versioni durante la sua durata. Una nuova versione viene generata ogni volta che il <xref:Microsoft.VisualStudio.Text.ITextSnapshot> buffer viene modificato e un non modificabile rappresenta il contenuto di tale versione del buffer. Poiché le istantanee di testo non sono modificabili, è possibile accedere a un'istantanea di testo su qualsiasi thread, senza restrizioni, anche se il buffer di testo che rappresenta continua a cambiare.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Istantanee di testo e linee di testo

È possibile visualizzare il contenuto di un'istantanea di testo come una sequenza di caratteri o come una sequenza di righe. I caratteri e le righe sono entrambi indicizzati a partire da zero. Un'istantanea di testo vuoto contiene zero caratteri e una riga vuota. Una riga è delimitata da qualsiasi sequenza di caratteri di interruzione di riga Unicode valida o dall'inizio o dalla fine del buffer. I caratteri di interruzione di riga sono rappresentati in modo esplicito nello snapshot di testo e le interruzioni di riga in uno snapshot di testo non devono essere tutte uguali.

> [!NOTE]
> Per ulteriori informazioni sui caratteri di interruzione di riga nell'editor di Visual Studio, vedere [Codifiche e interruzioni](../ide/encodings-and-line-breaks.md)di riga .

Una riga di testo <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> è rappresentata da un oggetto, che può essere ottenuto da un'istantanea di testo per un particolare numero di riga o per una particolare posizione del carattere.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections

Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint> rappresenta la posizione di un carattere in un'istantanea. La posizione è garantita per giacere tra zero e la lunghezza dell'istantanea. Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan> rappresenta un intervallo di testo in un'istantanea. La sua posizione finale è garantita per giacere tra zero e la lunghezza dell'istantanea. L'oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> è <xref:Microsoft.VisualStudio.Text.SnapshotSpan> costituito da un insieme di oggetti dallo stesso snapshot.

#### <a name="spans-and-normalizedspancollections"></a>Spans e NormalizedSpanCollections

Oggetto <xref:Microsoft.VisualStudio.Text.Span> rappresenta un intervallo che può essere applicato a un intervallo di testo in un'istantanea di testo. Le posizioni delle istantanee sono in base zero, pertanto gli intervalli possono iniziare in qualsiasi posizione, incluso zero. La `End` proprietà di un intervallo è `Start` uguale `Length` alla somma della relativa proprietà e della relativa proprietà. Un `Span` oggetto non include il carattere `End` indicizzato dalla proprietà . Ad esempio, un intervallo con inizio 5 e lunghezza 3 ha la fine 8 e include i caratteri nelle posizioni 5, 6 e 7. La notazione per questo intervallo è [5..8).

Due campate si intersecano se hanno in comune posizioni, inclusa la posizione Finale. Pertanto, l'intersezione di [3, 5) e [2, 7) è [3, 5) e l'intersezione di [3, 5) e [5, 7) è [5, 5). (Si noti che [5, 5) è un intervallo vuoto.)

Due estensioni si sovrappongono se hanno posizioni in comune, ad eccezione della posizione Finale. Un intervallo vuoto non si sovrappone mai ad altri intervalli e la sovrapposizione di due intervalli non è mai vuota.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> è un elenco di intervalli nell'ordine delle proprietà Start degli intervalli. Nell'elenco vengono unite le estensioni sovrapposte o adiacenti. Ad esempio, dato il set di intervalli [5..9), [0..1), [3..6) e [9..10), l'elenco normalizzato di intervalli è [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notifiche di Modifica di testo, TextVersion e Modifiche testo

Il contenuto di un buffer di <xref:Microsoft.VisualStudio.Text.ITextEdit> testo può essere modificato utilizzando un oggetto . La creazione di un oggetto `CreateEdit()` di <xref:Microsoft.VisualStudio.Text.ITextBuffer>questo tipo (utilizzando uno dei metodi di ) avvia una transazione di testo costituita da modifiche di testo. Ogni modifica è la sostituzione di un intervallo di testo nel buffer da una stringa. Le coordinate e il contenuto di ogni modifica sono espressi in relazione allo snapshot del buffer all'avvio della transazione. L'oggetto <xref:Microsoft.VisualStudio.Text.ITextEdit> regola le coordinate delle modifiche interessate da altre modifiche nella stessa transazione.

Si consideri, ad esempio, un buffer di testo che contiene questa stringa:For example, consider a text buffer that contains this string:

```
abcdefghij
```

Applicare una transazione che contiene due modifiche, una modifica che sostituisce l'intervallo in corrispondenza di [2..4) utilizzando il carattere `X` e una seconda modifica che sostituisce l'intervallo in [6..9) utilizzando il carattere `Y`. Il risultato è questo buffer:The result is this buffer:

```
abXefYj
```

Le coordinate per la seconda modifica sono state calcolate rispetto al contenuto del buffer all'inizio della transazione, prima dell'applicazione della prima modifica.

Le modifiche apportate al <xref:Microsoft.VisualStudio.Text.ITextEdit> buffer diventano effettive quando viene eseguito il commit dell'oggetto chiamando il relativo `Apply()` metodo. Se si è verificato almeno una modifica <xref:Microsoft.VisualStudio.Text.ITextVersion> non vuota, <xref:Microsoft.VisualStudio.Text.ITextSnapshot> viene creata `Changed` una nuova modifica, viene creato un nuovo evento e viene generato un evento. Ogni versione di testo ha un'istantanea di testo diversa. Uno snapshot di testo rappresenta lo stato completo del buffer di testo dopo una transazione di modifica, ma una versione di testo descrive solo le modifiche da uno snapshot a quello successivo. In generale, le istantanee di testo devono essere utilizzate una sola volta e quindi eliminate, mentre le versioni di testo devono rimanere attive per un certo periodo di tempo.

Una versione di <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>testo contiene un file . Questa raccolta descrive le modifiche che, se applicate allo snapshot, producono lo snapshot successivo. Ogni <xref:Microsoft.VisualStudio.Text.ITextChange> nella raccolta contiene la posizione del carattere della modifica, la stringa sostituita e la stringa di sostituzione. La stringa sostituita è vuota per un inserimento di base e la stringa di sostituzione è vuota per un'eliminazione di base. La raccolta normalizzata `null` è sempre per la versione più recente del buffer di testo.

È <xref:Microsoft.VisualStudio.Text.ITextEdit> possibile creare un'istanza di un solo oggetto per un buffer di testo in qualsiasi momento e tutte le modifiche di testo devono essere eseguite sul thread proprietario del buffer di testo (se la proprietà è stata rivendicata). Una modifica di testo può `Cancel` essere abbandonata chiamando il relativo metodo o il relativo `Dispose` metodo.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>fornisce `Insert()`inoltre `Delete()`, `Replace()` e metodi simili <xref:Microsoft.VisualStudio.Text.ITextEdit> a quelli presenti sull'interfaccia. La chiamata a questi ha <xref:Microsoft.VisualStudio.Text.ITextEdit> lo stesso effetto della creazione di un oggetto, l'esecuzione della chiamata simile e quindi l'applicazione della modifica.

#### <a name="tracking-points-and-tracking-spans"></a>Punti di tracciamento e campate di tracciamento

Oggetto <xref:Microsoft.VisualStudio.Text.ITrackingPoint> rappresenta una posizione di carattere in un buffer di testo. Se il buffer viene modificato in modo da spostare la posizione del carattere, il punto di rilevamento si sposta con esso. Ad esempio, se un punto di rilevamento fa riferimento alla posizione 10 in un buffer e cinque caratteri vengono inseriti all'inizio del buffer, il punto di rilevamento fa riferimento alla posizione 15. Se un inserimento avviene esattamente nella posizione indicata dal <xref:Microsoft.VisualStudio.Text.PointTrackingMode>punto di tracciamento, il suo comportamento è determinato dalla relativa , che può essere o `Positive` `Negative`. Se la modalità di tracciamento è positiva, il punto di tracciamento fa riferimento allo stesso carattere, che si trova ora alla fine dell'inserimento. Se la modalità di tracciamento è negativa, il punto di tracciamento si riferisce al primo carattere inserito nella posizione originale. Se il carattere nella posizione rappresentata da un punto di rilevamento viene eliminato, il punto di rilevamento passa al primo carattere che segue l'intervallo eliminato. Ad esempio, se un punto di tracciamento si riferisce al carattere nella posizione 5 e i caratteri nelle posizioni da 3 a 6 vengono eliminati, il punto di tracciamento fa riferimento al carattere nella posizione 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rappresenta un intervallo di caratteri anziché una sola posizione. Il suo comportamento <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>è determinato dalla sua . Se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), l'intervallo di rilevamento viene aumentato per incorporare il testo inserito ai bordi. Se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), l'intervallo di rilevamento non incorpora il testo inserito ai bordi. Tuttavia, se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), un inserimento spinge la posizione corrente verso l'inizio e se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), un inserimento spinge la posizione corrente verso la fine.

È possibile ottenere la posizione di un punto di rilevamento o l'intervallo di un intervallo di rilevamento per qualsiasi snapshot del buffer di testo a cui appartengono. I punti di rilevamento e gli intervalli di rilevamento possono essere referenziati in modo sicuro da qualsiasi thread.

#### <a name="content-types"></a>Tipi di contenuto

I tipi di contenuto sono un meccanismo per la definizione di diversi tipi di contenuto. Un tipo di contenuto può essere un tipo di file, ad esempio "text", "code" o "binary", oppure un tipo di tecnologia, ad esempio "xml", "vb" o "c". Ad esempio, la parola "using" è una parola chiave sia in C , che in Visual Basic, ma non in altri linguaggi di programmazione. Di conseguenza, la definizione di questa parola chiave sarebbe limitata ai tipi di contenuto "c" e "vb".

I tipi di contenuto vengono utilizzati come filtro per le aree di controllo e altri elementi dell'editor. Molte funzionalità dell'editor e punti di estensione sono definiti per tipo di contenuto. Ad esempio, la colorazione del testo è diversa per i file di testo normale, i file XML e i file di codice sorgente di Visual Basic. I buffer di testo sono in genere assegnati a un tipo di contenuto quando vengono creati e il tipo di contenuto di un buffer di testo può essere modificato.

I tipi di contenuto possono ereditare più elementi da altri tipi di contenuto. Consente <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> di specificare più tipi di base come elementi padre di un determinato tipo di contenuto.

Gli sviluppatori possono definire i propri tipi <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>di contenuto e registrarli utilizzando il file . Molte funzionalità dell'editor possono essere definite rispetto <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>a un tipo di contenuto specifico utilizzando il metodo . Ad esempio, i margini dell'editor, le aree di controllo e i gestori del mouse possono essere definiti in modo che vengano applicati solo agli editor che visualizzano tipi di contenuto specifici.

### <a name="the-text-view"></a>La visualizzazione di testo

La parte di visualizzazione del modello del controller di visualizzazione modello (MVC) definisce la visualizzazione di testo, la formattazione della visualizzazione, gli elementi grafici, ad esempio la barra di scorrimento e il punto di inserimento. Tutti gli elementi di presentazione dell'editor di Visual Studio sono basati su WPFWPF.

#### <a name="text-views"></a>Visualizzazioni di testo

L'interfaccia <xref:Microsoft.VisualStudio.Text.Editor.ITextView> è una rappresentazione indipendente dalla piattaforma di una visualizzazione di testo. Viene utilizzato principalmente per visualizzare documenti di testo in una finestra, ma può essere utilizzato anche per altri scopi, ad esempio, in una descrizione comando.

La visualizzazione di testo fa riferimento a diversi tipi di buffer di testo. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> proprietà fa <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> riferimento a un oggetto che punta a questi tre diversi buffer di testo: il buffer di dati, che è il buffer a livello di dati superiore, il buffer di modifica, in cui si verifica la modifica, e il buffer visivo, ovvero il buffer visualizzato nella visualizzazione di testo.

Il testo viene formattato in base ai classificatori associati al buffer di testo sottostante ed è decorato utilizzando i provider di area di controllo associati alla visualizzazione di testo stessa.

#### <a name="the-text-view-coordinate-system"></a>Il sistema di coordinate della vista di testo

Il sistema di coordinate della vista di testo specifica le posizioni nella vista di testo. In questo sistema di coordinate, il valore x 0,0 corrisponde al bordo sinistro del testo visualizzato e il valore y 0,0 corrisponde al bordo superiore del testo visualizzato. La coordinata x aumenta da sinistra a destra e la coordinata y aumenta dall'alto verso il basso.

Una finestra (la parte del testo visibile nella finestra di testo) non può essere fatta scorrere nello stesso modo in senso orizzontale in cui viene fatto scorrere verticalmente. Una finestra viene fatta scorrere orizzontalmente modificandone la coordinata sinistra in modo che si sposti rispetto alla superficie di disegno. Tuttavia, è possibile scorrere una finestra verticalmente solo modificando <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> il testo di cui è stato eseguito il rendering, che causa la generamento di un evento.

Le distanze nel sistema di coordinate corrispondono ai pixel logici. Se la superficie di rendering del testo viene visualizzata senza una trasformazione di ridimensionamento, un'unità nel sistema di coordinate di rendering del testo corrisponde a un pixel sullo schermo.

#### <a name="margins"></a>Margini

L'interfaccia <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> rappresenta un margine e consente il controllo della visibilità del margine e delle sue dimensioni. Sono disponibili quattro margini predefiniti, denominati "Top", "Left", "Right" e "Bottom" e collegati al bordo superiore, inferiore, sinistro o destro di una vista. Questi margini sono contenitori in cui è possibile posizionare altri margini. L'interfaccia definisce i metodi che restituiscono le dimensioni del margine e la visibilità di un margine. I margini sono elementi visivi che forniscono informazioni aggiuntive sulla visualizzazione di testo a cui sono associati. Ad esempio, il margine del numero di riga visualizza i numeri di riga per la visualizzazione di testo. Il margine del glifo visualizza gli elementi dell'interfaccia utente.

L'interfaccia <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> gestisce la creazione e la posizione dei margini. I margini possono essere ordinati rispetto ad altri margini. I margini con priorità più alta si trovano più vicini alla visualizzazione di testo. Ad esempio, se sono presenti due margini sinistro, il margine A e il margine B e il margine B ha una priorità inferiore rispetto al margine A, il margine B viene visualizzato a sinistra del margine A.

#### <a name="the-text-view-host"></a>L'host della visualizzazione di testo

L'interfaccia <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> contiene la visualizzazione di testo e le eventuali decorazioni adiacenti che accompagnano la visualizzazione, ad esempio le barre di scorrimento. L'host della visualizzazione di testo contiene anche i margini associati a un bordo della vista.

#### <a name="formatted-text"></a>Testo formattato

Il testo visualizzato in una visualizzazione di <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> testo è composto da oggetti. Ogni riga di visualizzazione di testo corrisponde a una riga di testo nella visualizzazione di testo. Le righe lunghe nel buffer di testo sottostante possono essere parzialmente oscurate (se il ritorno a capo automatico non è abilitato) o suddivise in più righe di visualizzazione di testo. L'interfaccia <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> contiene metodi e proprietà per il mapping tra coordinate e caratteri e per le aree di controllo che possono essere associate alla riga.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>gli oggetti vengono <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> creati tramite un'interfaccia. Se si è preoccupati solo per il testo attualmente visualizzato nella visualizzazione, è possibile ignorare l'origine della formattazione. Se si è interessati al formato del testo non visualizzato nella visualizzazione (ad esempio, per supportare un taglio e incolla di testo RTF), è possibile utilizzare <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> per formattare il testo in un buffer di testo.

La visualizzazione di <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> testo viene formatta una alla volta.

## <a name="editor-features"></a>Funzionalità dell'editor

Le funzionalità dell'editor sono progettate in modo che la definizione della funzionalità sia separata dalla relativa implementazione. L'editor include le seguenti funzionalità:

- Tag e classificatori

- Ornamenti

- Proiezione

- struttura

- Associazioni di mouse e tasti

- Operazioni e primitive

- IntelliSense

### <a name="tags-and-classifiers"></a>Tag e classificatori

I tag sono marcatori associati a un intervallo di testo. Possono essere presentati in diversi modi, ad esempio utilizzando la colorazione del testo, le sottolineature, la grafica o i popup. I classificatori sono un tipo di tag.

Altri tipi di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> tag sono <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> per l'evidenziazione del testo, per la struttura e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> per gli errori di compilazione.

#### <a name="classification-types"></a>Tipi di classificazione

Un'interfaccia <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> rappresenta una classe di equivalenza, ovvero una categoria astratta di testo. I tipi di classificazione possono ereditare più elementi da altri tipi di classificazione. Ad esempio, le classificazioni dei linguaggi di programmazione potrebbero includere "parola chiave", "commento" e "identificatore", che ereditano tutte da "codice". I tipi di classificazione del linguaggio naturale possono includere "sostantivo", "verbo" e "aggettivo", che tutti ereditano da "linguaggio naturale".

#### <a name="classifications"></a>Classificazioni

Una classificazione è un'istanza di un particolare tipo di classificazione, in genere su un intervallo di testo. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> viene utilizzato per rappresentare una classificazione. Un intervallo di classificazione può essere considerato come un'etichetta che copre un particolare intervallo di testo e indica al sistema che questo intervallo di testo è di un particolare tipo di classificazione.

#### <a name="classifiers"></a>Classificatori

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> meccanismo è un meccanismo che suddivide il testo in un set di classificazioni. I classificatori devono essere definiti per tipi di contenuto specifici e istanziati per buffer di testo specifici. I client <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> devono implementare per partecipare alla classificazione di testo.

#### <a name="classifier-aggregators"></a>Aggregatori classificatori

Un aggregatore di classificatori è un meccanismo che combina tutti i classificatori per un buffer di testo in un solo set di classificazioni. Ad esempio, sia un classificatore di c'è e un classificatore di lingua inglese potrebbe creare classificazioni su un commento in un file c.For example, both a C' classifier and an English language classifier could create classifications over a comment in a C' file. Considera questo commento:

```
// This method produces a classifier
```

Un classificatore di C, potrebbe etichettare l'intero intervallo come commento e il classificatore di lingua inglese potrebbe classificare "produce" come "verbo" e "metodo" come "sostantivo". L'aggregatore produce una serie di classificazioni non sovrapposte e il tipo di set si basa su tutti i contributi.

Un aggregatore classificatore è anche un classificatore perché suddivide il testo in un set di classificazioni. L'aggregatore di classificatori garantisce inoltre che non vi siano classificazioni sovrapposte e che le classificazioni siano ordinate. I singoli classificatori sono liberi di restituire qualsiasi set di classificazioni, in qualsiasi ordine e sovrapposte in qualsiasi modo.

#### <a name="classification-formatting-and-text-coloring"></a>Formattazione della classificazione e colorazione del testo

La formattazione del testo è un esempio di funzionalità basata sulla classificazione del testo. Viene utilizzato dal livello di visualizzazione del testo per determinare la visualizzazione del testo in un'applicazione. L'area di formattazione del testo dipende da WPFWPF, ma non dalla definizione logica delle classificazioni.

Un formato di classificazione è un set di proprietà di formattazione per un tipo di classificazione specifico. Questi formati ereditano dal formato dell'elemento padre del tipo di classificazione.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> oggetto è una mappa da un tipo di classificazione a un set di proprietà di formattazione del testo. L'implementazione della mappa di formato nell'editor gestisce tutte le esportazioni dei formati di classificazione.

### <a name="adornments"></a>Ornamenti

Gli elementi decorativi sono effetti grafici che non sono direttamente correlati al tipo di carattere e al colore dei caratteri nella visualizzazione di testo. Ad esempio, la sottolineatura ondulata rossa utilizzata per contrassegnare il codice non di compilazione in molti linguaggi di programmazione è un'area di controllo incorporata e le descrizioni comandi sono aree di controllo popup. Gli elementi decorativi sono derivati da <xref:System.Windows.UIElement> e implementano <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Due tipi specializzati di <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>tag di area di controllo sono , per le aree di controllo che occupano lo stesso spazio del testo in una vista e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, per la sottolineatura ondulata.

Le aree di controllo incorporate sono elementi grafici che fanno parte della visualizzazione di testo formattata. Sono organizzati in diversi livelli di ordine z. Sono disponibili tre livelli incorporati, come indicato di seguito: testo, il punto di inserimento e la selezione. Tuttavia, gli sviluppatori possono definire più layer e metterli in ordine l'uno rispetto all'altro. I tre tipi di aree di controllo incorporate sono aree di controllo relative al testo (che si spostano quando il testo viene spostato e vengono eliminati quando il testo viene eliminato), le aree di controllo relative alla visualizzazione (che hanno a che fare con le parti non testuali della visualizzazione) e le aree di controllo controllate dal proprietario (lo sviluppatore deve gestire il posizionamento).

Le aree di controllo popup sono elementi grafici che vengono visualizzati in una piccola finestra sopra la visualizzazione di testo, ad esempio le descrizioni comandi.

### <a name="projection"></a><a name="projection"></a>Proiezione

La proiezione è una tecnica per la costruzione di un tipo diverso di buffer di testo che non archivia effettivamente il testo, ma combina il testo di altri buffer di testo. Ad esempio, un buffer di proiezione può essere utilizzato per concatenare il testo da altri due buffer e presentare il risultato come se si trovasse in un solo buffer o per nascondere parti del testo in un buffer. Un buffer di proiezione può fungere da buffer di origine per un altro buffer di proiezione. Un set di buffer correlati dalla proiezione può essere costruito per ridisporre il testo in molti modi diversi. (Questo set è noto anche come *grafico del buffer.* La funzionalità di struttura del testo di Visual Studio viene implementata utilizzando un buffer di proiezione per nascondere il testo compresso e l'editor di Visual Studio per ASP.NET pagine utilizza la proiezione per supportare i linguaggi incorporati, ad esempio Visual Basic e C.

Viene <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> creato un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>oggetto mediante . Un buffer di proiezione è <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rappresentato da una sequenza ordinata di oggetti noti come *intervalli*di origine . Il contenuto di questi intervalli viene presentato come una sequenza di caratteri. I buffer di testo da cui vengono disegnati gli intervalli di origine sono *denominati buffer di origine.* I client di un buffer di proiezione non devono essere consapevoli del fatto che è diverso da un buffer di testo ordinario.

Il buffer di proiezione è in ascolto degli eventi di modifica del testo nei buffer di origine. Quando il testo in un intervallo di origine viene modificato, il buffer di proiezione esegue il mapping delle coordinate del testo modificate alle proprie coordinate e genera gli eventi di modifica del testo appropriati. Ad esempio, si considerino i buffer di origine A e B che hanno il contenuto seguente:For example, consider source buffers A and B that have these contents:

```
A: ABCDE
B: vwxyz
```

Se il buffer di proiezione P è formato da due intervalli di testo, uno che ha tutto il buffer A e l'altro che ha tutto il buffer B, quindi P ha il seguente contenuto:

```
P: ABCDEvwxyz
```

Se la `xy` sottostringa viene eliminata dal buffer B, il buffer P genera un evento che indica che i caratteri nelle posizioni 7 e 8 sono stati eliminati.

Il buffer di proiezione può anche essere modificato direttamente. Propaga le modifiche ai buffer di origine appropriati. Ad esempio, se una stringa viene inserita nel buffer P nella posizione 6 (la posizione originale del carattere "v"), l'inserimento viene propagato al buffer B nella posizione 1.

Esistono restrizioni sugli intervalli di origine che contribuiscono a un buffer di proiezione. Gli intervalli di origine non possono sovrapporsi; una posizione in un buffer di proiezione non può eseguire il mapping a più di una posizione in qualsiasi buffer di origine e una posizione in un buffer di origine non può eseguire il mapping a più di una posizione in un buffer di proiezione. Non sono consentite circolarità nella relazione del buffer di origine.

Gli eventi vengono generati quando il set di buffer di origine per un buffer di proiezione viene modificato e quando il set di intervalli di origine viene modificato.
Un buffer di elisione è un tipo speciale di buffer di proiezione. Viene utilizzato principalmente per la struttura e per le operazioni che espandono e comprimono blocchi di testo. Un buffer di elisione è basato su un solo buffer di origine e gli intervalli nel buffer di elisione devono essere ordinati come sono ordinati nel buffer di origine.

#### <a name="the-buffer-graph"></a>Il grafico del buffer

L'interfaccia <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> consente il mapping in un grafico di buffer di proiezione. Tutti i buffer di testo e i buffer di proiezione vengono raccolti in un grafico aciclico diretto, in modo analogo all'albero della sintassi astratta prodotto da un compilatore di linguaggio. Il grafico è definito dal buffer superiore, che può essere qualsiasi buffer di testo. Il grafico del buffer può eseguire il mapping da un punto nel buffer superiore a un punto in un buffer di origine o da un intervallo nel buffer superiore a un set di intervalli in un buffer di origine. Analogamente, può eseguire il mapping di un punto o di un intervallo da un buffer di origine a un punto nel buffer superiore. I grafici del buffer <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>vengono creati utilizzando l'oggetto .

#### <a name="events-and-projection-buffers"></a>Buffer di eventi e proiezioni

Quando un buffer di proiezione viene modificato, le modifiche vengono inviate dal buffer di proiezione ai buffer che dipendono da esso. Dopo la modifica di tutti i buffer, vengono generati eventi di modifica del buffer, a partire dal buffer più profondo.

### <a name="outlining"></a>struttura

La struttura consente di espandere o comprimere diversi blocchi di testo in una visualizzazione di testo. La struttura è definita <xref:Microsoft.VisualStudio.Text.Tagging.ITag>come un tipo di , nello stesso modo in cui vengono definite le aree di controllo. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> è un tag che definisce un'area di testo che può essere espansa o compressa. Per utilizzare la struttura, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> è necessario <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>importare l'oggetto per ottenere un file . Il gestore della struttura enumera, comprime ed espande i <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> diversi blocchi, rappresentati come oggetti, generando eventi di conseguenza.

### <a name="mouse-bindings"></a>Associazioni del mouse

Le associazioni del mouse collegano i movimenti del mouse a comandi diversi. Le associazioni del mouse <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>vengono definite utilizzando un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>, e le associazioni di tasti vengono definite mediante un oggetto . L'oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> crea automaticamente un'istanza di tutte le associazioni e le connette agli eventi del mouse nella visualizzazione.

L'interfaccia <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> contiene gestori eventi di pre-elaborazione e post-elaborazione per diversi eventi del mouse. Per gestire uno degli eventi, è possibile <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>eseguire l'override di alcuni metodi in .

### <a name="editor-operations"></a>Operazioni dell'editore

Le operazioni dell'editor possono essere utilizzate per automatizzare l'interazione con l'editor, per lo scripting o altri scopi. È possibile <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> importare l'oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>per accedere alle operazioni su un determinato oggetto . È quindi possibile utilizzare questi oggetti per modificare la selezione, scorrere la vista o spostare il punto di inserimento in diverse parti della vista.

### <a name="intellisense"></a>IntelliSense

IntelliSense supporta il completamento delle istruzioni, la Guida alla firma (nota anche come informazioni sui parametri), le informazioni rapide e le lampadine.

Il completamento delle istruzioni fornisce elenchi popup di potenziali completamenti per i nomi dei metodi, gli elementi XML e altri elementi di codifica o markup. In generale, un gesto dell'utente richiama una sessione di completamento. La sessione visualizza l'elenco dei potenziali completamenti e l'utente può selezionarne uno o chiudere l'elenco. L'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> è responsabile <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>della creazione e dell'attivazione del file . Il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcola <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> il degli elementi di completamento per la sessione.

## <a name="see-also"></a>Vedere anche

- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
- [Importazioni dell'editor](../extensibility/editor-imports.md)
