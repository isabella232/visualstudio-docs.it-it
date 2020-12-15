---
title: Componenti e funzionalità dell'editor
description: Informazioni sui sottosistemi e le funzionalità dell'editor. È possibile estendere le funzionalità dell'editor di Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 14193c0806c4b45f721ee97b101969de8437448d
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487530"
---
# <a name="inside-the-editor"></a>All'interno dell'editor

L'editor è costituito da diversi sottosistemi, progettati per rendere il modello di testo dell'editor separato dalla visualizzazione di testo e dall'interfaccia utente.

In queste sezioni vengono descritti diversi aspetti dell'Editor:

- [Panoramica dei sottosistemi](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Modello di testo](../extensibility/inside-the-editor.md#the-text-model)

- [Visualizzazione di testo](../extensibility/inside-the-editor.md#the-text-view)

Queste sezioni descrivono le funzionalità dell'Editor:

- [Tag e classificatori](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Aree](../extensibility/inside-the-editor.md#adornments)

- [Proiezione](../extensibility/inside-the-editor.md#projection)

- [struttura](../extensibility/inside-the-editor.md#outlining)

- [Associazioni del mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operazioni dell'editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Panoramica dei sottosistemi

### <a name="text-model-subsystem"></a>Sottosistema modello di testo

Il sottosistema del modello di testo è responsabile della rappresentazione del testo e dell'abilitazione della relativa manipolazione. Il sottosistema del modello di testo contiene l' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia, che descrive la sequenza di caratteri che deve essere visualizzata dall'editor. Questo testo può essere modificato, rilevato e altrimenti modificato in molti modi. Il modello di testo fornisce anche tipi per gli aspetti seguenti:

- Servizio che associa testo a file e li gestisce leggendo e scrivendo nel file system.

- Un servizio differenze che consente di trovare le differenze minime tra due sequenze di oggetti.

- Sistema per la descrizione del testo in un buffer in termini di subset del testo in altri buffer.

Il sottosistema del modello di testo è privo di concetti dell'interfaccia utente. Ad esempio, non è responsabile della formattazione del testo o del layout del testo e non ha alcuna conoscenza delle aree di disegno visive che possono essere associate al testo.

I tipi pubblici del sottosistema del modello di testo sono contenuti in *Microsoft.VisualStudio.Text.Data.dll* e *Microsoft.VisualStudio.CoreUtility.dll*, che dipendono solo dalla libreria di classi di base .NET Framework e dal Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Sottosistema visualizzazione testo

Il sottosistema visualizzazione testo è responsabile della formattazione e della visualizzazione del testo. I tipi di questo sottosistema sono divisi in due livelli, a seconda che i tipi si basino su Windows Presentation Foundation (WPF). I tipi più importanti sono <xref:Microsoft.VisualStudio.Text.Editor.ITextView> e <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , che controllano il set di righe di testo da visualizzare e anche il punto di inserimento, la selezione e le funzionalità per decorare il testo usando gli elementi dell'interfaccia utente WPF. Questo sottosistema fornisce anche margini intorno all'area di visualizzazione del testo. Questi margini possono essere estesi e possono contenere diversi tipi di contenuto e effetti visivi. Esempi di margini sono le visualizzazioni dei numeri di riga e le barre di scorrimento.

I tipi pubblici del sottosistema di visualizzazione di testo sono contenuti in *Microsoft.VisualStudio.Text.UI.dll* e *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Il primo assembly contiene gli elementi indipendenti dalla piattaforma e il secondo contiene gli elementi specifici di WPF.

### <a name="classification-subsystem"></a>Sottosistema di classificazione

Il sottosistema di classificazione è responsabile della determinazione delle proprietà del tipo di carattere per il testo. Un classificatore suddivide il testo in classi diverse, ad esempio, "keyword" o "comment". Il mapping del formato di classificazione mette in correlazione queste classi alle proprietà del tipo di carattere effettive, ad esempio, "Blue conconsolas 10 PT". Queste informazioni vengono utilizzate dalla visualizzazione testo quando formatta ed esegue il rendering del testo. L'assegnazione di tag, descritta in modo più dettagliato più avanti in questo argomento, consente di associare i dati a intervalli di testo.

I tipi pubblici del sottosistema di classificazione sono contenuti in Microsoft.VisualStudio.Text.Logic.dll e interagiscono con gli aspetti visivi della classificazione, che sono contenuti in Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sottosistema operativo

Il sottosistema operativo definisce il comportamento dell'editor. Fornisce l'implementazione per i comandi dell'editor di Visual Studio e il sistema di annullamento.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Esaminare più in dettaglio il modello di testo e la visualizzazione di testo

### <a name="the-text-model"></a>Modello di testo

Il sottosistema del modello di testo è costituito da diversi raggruppamenti di tipi di testo. Sono inclusi il buffer di testo, gli snapshot di testo e gli intervalli di testo.

#### <a name="text-buffers-and-text-snapshots"></a>Buffer di testo e snapshot di testo

L' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia rappresenta una sequenza di caratteri Unicode codificati utilizzando UTF-16, ovvero la codifica utilizzata dal `String` tipo nel .NET Framework. Un buffer di testo può essere reso permanente come documento file system, ma ciò non è obbligatorio.

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Viene utilizzato per creare un buffer di testo vuoto o un buffer di testo inizializzato da una stringa o da <xref:System.IO.TextReader> . Il buffer di testo può essere salvato in modo permanente nel file system come <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Qualsiasi thread può modificare il buffer di testo fino a quando un thread non acquisisce la proprietà del buffer di testo chiamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Successivamente, solo quel thread può eseguire le modifiche.

Un buffer di testo può attraversare diverse versioni durante la sua durata. Viene generata una nuova versione ogni volta che il buffer viene modificato e un oggetto non modificabile <xref:Microsoft.VisualStudio.Text.ITextSnapshot> rappresenta il contenuto di tale versione del buffer. Poiché gli snapshot di testo non sono modificabili, è possibile accedere a uno snapshot di testo in qualsiasi thread, senza restrizioni, anche se il buffer di testo che rappresenta continua a cambiare.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Snapshot di testo e righe dello snapshot del testo

È possibile visualizzare il contenuto di uno snapshot di testo come sequenza di caratteri o come sequenza di righe. I caratteri e le righe sono entrambi indicizzati a partire da zero. Uno snapshot di testo vuoto contiene zero caratteri e una riga vuota. Una riga è delimitata da qualsiasi sequenza di caratteri di interruzioni di riga Unicode valida o dall'inizio o dalla fine del buffer. I caratteri di interruzione di riga sono rappresentati in modo esplicito nello snapshot di testo e le interruzioni di riga in uno snapshot di testo non devono necessariamente essere uguali.

> [!NOTE]
> Per ulteriori informazioni sui caratteri di interruzione di riga nell'editor di Visual Studio, vedere [codifiche e interruzioni di riga](../ide/encodings-and-line-breaks.md).

Una riga di testo è rappresentata da un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> oggetto, che può essere ottenuto da uno snapshot di testo per un determinato numero di riga o per una particolare posizione di carattere.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Gli elementi SnapshotPoint, SnapshotSpans e NormalizedSnapshotSpanCollections

Un oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint> rappresenta una posizione del carattere in uno snapshot. Si garantisce che la posizione sia compresa tra zero e la lunghezza dello snapshot. Un oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan> rappresenta un intervallo di testo in uno snapshot. La posizione finale è garantita tra zero e la lunghezza dello snapshot. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>È costituito da un set di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> oggetti dello stesso snapshot.

#### <a name="spans-and-normalizedspancollections"></a>Spans e NormalizedSpanCollections

Un oggetto <xref:Microsoft.VisualStudio.Text.Span> rappresenta un intervallo che può essere applicato a un intervallo di testo in uno snapshot di testo. Le posizioni degli snapshot sono in base zero, quindi gli intervalli possono iniziare in qualsiasi posizione, incluso zero. La `End` proprietà di un intervallo è uguale alla somma della proprietà `Start` e della relativa `Length` Proprietà. Un oggetto non `Span` include il carattere indicizzato dalla `End` Proprietà. Ad esempio, un intervallo con inizio = 5 e lunghezza = 3 ha estremità = 8 e include i caratteri nelle posizioni 5, 6 e 7. La notazione per questo intervallo è [5.. 8).

Due intervalli si intersecano se hanno posizioni in comune, inclusa la posizione finale. Pertanto, l'intersezione tra [3, 5) e [2, 7] è [3, 5) e l'intersezione tra [3, 5) e [5, 7] è [5, 5). (Si noti che [5, 5) è un intervallo vuoto.

Due intervalli si sovrappongono se hanno posizioni in comune, ad eccezione della posizione finale. Un intervallo vuoto non si sovrappone mai a qualsiasi altro intervallo e la sovrapposizione di due intervalli non è mai vuota.

Un oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> è un elenco di intervalli nell'ordine delle proprietà di inizio degli intervalli. Nell'elenco gli intervalli sovrapposti o adiacenti vengono uniti. Ad esempio, dato il set di intervalli [5.. 9), [0.. 1), [3.. 6) e [9.. 10), l'elenco normalizzato degli intervalli è [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notifiche di modifica di ITextEdit, TextVersion e testo

Il contenuto di un buffer di testo può essere modificato utilizzando un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto. La creazione di un oggetto di questo tipo (usando uno dei `CreateEdit()` metodi di <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) avvia una transazione di testo costituita da modifiche di testo. Ogni modifica è una sostituzione di una parte di testo nel buffer da una stringa. Le coordinate e il contenuto di ogni modifica sono espressi in relazione allo snapshot del buffer quando la transazione è stata avviata. L' <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto regola le coordinate delle modifiche interessate da altre modifiche nella stessa transazione.

Si consideri, ad esempio, un buffer di testo che contiene la stringa seguente:

```
abcdefghij
```

Applicare una transazione che contiene due modifiche, una modifica che sostituisce l'intervallo in [2.. 4) utilizzando il carattere `X` e una seconda modifica che sostituisce l'intervallo in [6.. 9) utilizzando il carattere `Y` . Il risultato è questo buffer:

```
abXefYj
```

Le coordinate per la seconda modifica sono state calcolate rispetto al contenuto del buffer all'inizio della transazione, prima dell'applicazione della prima modifica.

Le modifiche apportate al buffer diventano effettive quando <xref:Microsoft.VisualStudio.Text.ITextEdit> viene eseguito il commit dell'oggetto chiamando il relativo `Apply()` metodo. Se era presente almeno una modifica non vuota, viene creato un nuovo oggetto, <xref:Microsoft.VisualStudio.Text.ITextVersion> viene creato un nuovo oggetto <xref:Microsoft.VisualStudio.Text.ITextSnapshot> e `Changed` viene generato un evento. Ogni versione di testo presenta uno snapshot di testo diverso. Uno snapshot di testo rappresenta lo stato completo del buffer di testo dopo una transazione di modifica, ma una versione di testo descrive solo le modifiche apportate da uno snapshot al successivo. In generale, gli snapshot di testo devono essere usati una sola volta e quindi eliminati, mentre le versioni di testo devono rimanere attive per un certo periodo di tempo.

Una versione di testo contiene un oggetto <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Questa raccolta descrive le modifiche che, quando applicate allo snapshot, producono lo snapshot successivo. Ogni oggetto della <xref:Microsoft.VisualStudio.Text.ITextChange> raccolta contiene la posizione del carattere della modifica, la stringa sostituita e la stringa di sostituzione. La stringa sostituita è vuota per un inserimento di base e la stringa di sostituzione è vuota per un'eliminazione di base. La raccolta normalizzata è sempre `null` per la versione più recente del buffer di testo.

È <xref:Microsoft.VisualStudio.Text.ITextEdit> possibile creare un'istanza di un solo oggetto per un buffer di testo in qualsiasi momento e tutte le modifiche di testo devono essere eseguite sul thread proprietario del buffer di testo (se la proprietà è stata rivendicata). Una modifica di testo può essere abbandonata chiamando il relativo `Cancel` metodo o il relativo `Dispose` metodo.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> fornisce inoltre `Insert()` `Delete()` metodi, e `Replace()` simili a quelli disponibili nell' <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaccia. La chiamata a questi oggetti ha lo stesso effetto della creazione di un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto, della chiamata analoga e dell'applicazione della modifica.

#### <a name="tracking-points-and-tracking-spans"></a>Punti di rilevamento e intervalli di rilevamento

Un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingPoint> rappresenta una posizione del carattere in un buffer di testo. Se il buffer viene modificato in modo da far sì che la posizione del carattere venga spostata, il punto di rilevamento viene spostato su di esso. Se, ad esempio, un punto di rilevamento si riferisce alla posizione 10 in un buffer e vengono inseriti cinque caratteri all'inizio del buffer, il punto di rilevamento fa riferimento alla posizione 15. Se un inserimento si verifica esattamente nella posizione indicata dal punto di rilevamento, il relativo comportamento è determinato dalla proprietà <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , che può essere `Positive` o `Negative` . Se la modalità di rilevamento è positiva, il punto di rilevamento si riferisce allo stesso carattere, che ora si trova alla fine dell'inserimento. Se la modalità di rilevamento è negativa, il punto di rilevamento si riferisce al primo carattere inserito nella posizione originale. Se il carattere in corrispondenza della posizione rappresentata da un punto di rilevamento viene eliminato, il punto di rilevamento passa al primo carattere che segue l'intervallo eliminato. Se, ad esempio, un punto di rilevamento fa riferimento al carattere nella posizione 5 e i caratteri nelle posizioni da 3 a 6 vengono eliminati, il punto di rilevamento si riferisce al carattere nella posizione 3.

Un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rappresenta un intervallo di caratteri anziché una sola posizione. Il suo comportamento è determinato dalla proprietà <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Se la modalità di rilevamento dell'intervallo è [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), l'intervallo di rilevamento aumenta per incorporare il testo inserito ai bordi. Se la modalità di rilevamento dell'intervallo è [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), l'intervallo di rilevamento non incorpora il testo inserito ai bordi. Tuttavia, se la modalità di rilevamento dell'intervallo è [SpanTrackingMode. EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), un inserimento inserisce la posizione corrente verso l'inizio e se la modalità di rilevamento dell'intervallo è [SpanTrackingMode. EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), un inserimento inserisce la posizione corrente verso la fine.

È possibile ottenere la posizione di un punto di rilevamento o l'intervallo di un intervallo di rilevamento per qualsiasi snapshot del buffer di testo a cui appartengono. I punti di rilevamento e gli intervalli di rilevamento possono essere a cui viene fatto riferimento in modo sicuro da qualsiasi thread.

#### <a name="content-types"></a>Tipi di contenuto

I tipi di contenuto sono un meccanismo per la definizione di tipi diversi di contenuto. Un tipo di contenuto può essere un tipo di file, ad esempio "Text", "code" o "binary", o un tipo di tecnologia, ad esempio "XML", "VB" o "c#". La parola "using", ad esempio, è una parola chiave sia in C# sia in Visual Basic, ma non in altri linguaggi di programmazione. La definizione di questa parola chiave sarà pertanto limitata ai tipi di contenuto "c#" e "VB".

I tipi di contenuto vengono usati come filtro per le aree di strumenti e altri elementi dell'editor. Molte funzionalità dell'editor e punti di estensione sono definiti per ogni tipo di contenuto. Ad esempio, la colorazione del testo è diversa per i file di testo normale, i file XML e i file di codice sorgente Visual Basic. Ai buffer di testo viene generalmente assegnato un tipo di contenuto quando vengono creati e il tipo di contenuto di un buffer di testo può essere modificato.

I tipi di contenuto possono ereditare più tipi da altri tipi di contenuto. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Consente di specificare più tipi di base come elementi padre di un determinato tipo di contenuto.

Gli sviluppatori possono definire i propri tipi di contenuto e registrarli usando <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Molte funzionalità dell'editor possono essere definite in relazione a un tipo di contenuto specifico usando <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . È possibile, ad esempio, definire i margini dell'editor, le aree di controllo e i gestori del mouse in modo che si applichino solo agli editor che visualizzano tipi di contenuto specifici.

### <a name="the-text-view"></a>Visualizzazione di testo

La parte di visualizzazione del modello MVC (Model View Controller) definisce la visualizzazione di testo, la formattazione della visualizzazione, elementi grafici come la barra di scorrimento e il punto di inserimento. Tutti gli elementi di presentazione dell'editor di Visual Studio sono basati su WPF.

#### <a name="text-views"></a>Visualizzazioni di testo

L' <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaccia è una rappresentazione indipendente dalla piattaforma di una visualizzazione di testo. Viene usato principalmente per visualizzare documenti di testo in una finestra, ma può anche essere usato per altri scopi, ad esempio, in una descrizione comando.

La visualizzazione di testo fa riferimento a tipi diversi di buffer di testo. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> proprietà fa riferimento a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> oggetto che punta a questi tre diversi buffer di testo: il buffer dei dati, ovvero il buffer di primo livello dati, il buffer di modifica, in cui si verifica la modifica e il buffer visivo, ovvero il buffer visualizzato nella visualizzazione di testo.

Il testo viene formattato in base ai classificatori collegati al buffer di testo sottostante ed è decorato tramite i provider di aree di visualizzazione collegati alla visualizzazione di testo.

#### <a name="the-text-view-coordinate-system"></a>Sistema di coordinate della visualizzazione testo

Il sistema di coordinate della visualizzazione testo specifica le posizioni nella visualizzazione di testo. In questo sistema di coordinate, il valore x 0,0 corrisponde al bordo sinistro del testo visualizzato e il valore y 0,0 corrisponde al bordo superiore del testo visualizzato. La coordinata x aumenta da sinistra a destra e la coordinata y aumenta dall'alto verso il basso.

Un viewport (la parte del testo visibile nella finestra di testo) non può essere spostato orizzontalmente nello stesso modo in cui viene eseguito lo scorrimento verticale. Un viewport viene spostato orizzontalmente cambiando la relativa coordinata sinistra in modo da spostarla rispetto alla superficie di disegno. Tuttavia, è possibile scorrere verticalmente un viewport solo modificando il testo sottoposto a rendering, che causa la generazione di un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.

Le distanze nel sistema di coordinate corrispondono ai pixel logici. Se la superficie di rendering del testo viene visualizzata senza una trasformazione di ridimensionamento, un'unità nel sistema di coordinate del rendering del testo corrisponde a un pixel sullo schermo.

#### <a name="margins"></a>Margini

L' <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaccia rappresenta un margine e consente di controllare la visibilità del margine e le relative dimensioni. Sono disponibili quattro margini predefiniti, denominati "Top", "left", "Right" e "bottom" e collegati al bordo superiore, inferiore, sinistro o destro di una visualizzazione. Questi margini sono contenitori in cui è possibile posizionare altri margini. L'interfaccia definisce i metodi che restituiscono le dimensioni del margine e la visibilità di un margine. I margini sono elementi visivi che forniscono informazioni aggiuntive sulla visualizzazione di testo a cui sono collegati. Ad esempio, il margine del numero di riga Visualizza i numeri di riga per la visualizzazione di testo. Il margine del glifo Visualizza gli elementi dell'interfaccia utente.

L' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia gestisce la creazione e il posizionamento dei margini. I margini possono essere ordinati rispetto ad altri margini. I margini con priorità più elevata si trovano più vicini alla visualizzazione di testo. Se ad esempio sono presenti due margini sinistri, il margine A e il margine b e il margine B hanno una priorità più bassa del margine A, il margine B viene visualizzato a sinistra del margine A.

#### <a name="the-text-view-host"></a>Host della visualizzazione di testo

L' <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaccia contiene la visualizzazione di testo e tutte le decorazioni adiacenti che accompagnano la visualizzazione, ad esempio le barre di scorrimento. L'host della visualizzazione di testo contiene anche margini collegati a un bordo della visualizzazione.

#### <a name="formatted-text"></a>Testo formattato

Il testo visualizzato in una visualizzazione di testo è costituito da <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oggetti. Ogni riga di visualizzazione di testo corrisponde a una riga di testo nella visualizzazione di testo. Le righe lunghe nel buffer di testo sottostante possono essere parzialmente nascoste (se il ritorno a capo automatico non è abilitato) o suddivise in più righe di visualizzazione di testo. L' <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaccia contiene i metodi e le proprietà per il mapping tra coordinate e caratteri e per le aree di strumenti che possono essere associate alla riga.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> gli oggetti vengono creati tramite un' <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaccia. Se si è interessati solo al testo attualmente visualizzato nella visualizzazione, è possibile ignorare l'origine di formattazione. Se si è interessati al formato del testo che non viene visualizzato nella visualizzazione (ad esempio, per supportare un taglia e incolla di testo RTF), è possibile utilizzare <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> per formattare il testo in un buffer di testo.

La visualizzazione di testo viene formattata una <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> alla volta.

## <a name="editor-features"></a>Funzionalità dell'editor

Le funzionalità dell'editor sono progettate in modo tale che la definizione della funzionalità sia separata dalla relativa implementazione. Nell'editor sono incluse le funzionalità seguenti:

- Tag e classificatori

- Aree

- Proiezione

- struttura

- Tasti di scelta per mouse e tasti

- Operazioni e primitive

- IntelliSense

### <a name="tags-and-classifiers"></a>Tag e classificatori

I tag sono marcatori associati a un intervallo di testo. Possono essere presentati in modi diversi, ad esempio usando la colorazione del testo, le sottolineature, la grafica o i popup. I classificatori sono un tipo di tag.

Altri tipi di tag sono <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> per l'evidenziazione del testo, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> per la struttura e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> per gli errori di compilazione.

#### <a name="classification-types"></a>Tipi di classificazione

Un' <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaccia rappresenta una classe di equivalenza, che è una categoria astratta di testo. I tipi di classificazione possono ereditare più tipi da altri tipi di classificazione. Le classificazioni del linguaggio di programmazione, ad esempio, possono includere "keyword", "comment" e "Identifier", che ereditano tutti da "code". I tipi di classificazione del linguaggio naturale possono includere "sostantivo", "verbo" e "aggettivo", che ereditano tutti da "linguaggio naturale".

#### <a name="classifications"></a>Classificazioni

Una classificazione è un'istanza di un particolare tipo di classificazione, in genere su un intervallo di testo. Un oggetto <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> viene utilizzato per rappresentare una classificazione. Un intervallo di classificazione può essere considerato come un'etichetta che copre una particolare sezione di testo e indica al sistema che questo intervallo di testo è di un determinato tipo di classificazione.

#### <a name="classifiers"></a>Classificatori

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> è un meccanismo che suddivide il testo in un set di classificazioni. I classificatori devono essere definiti per tipi di contenuto specifici e ne viene creata un'istanza per buffer di testo specifici. I client devono implementare <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per partecipare alla classificazione del testo.

#### <a name="classifier-aggregators"></a>Aggregatori di classificatore

Un aggregatore di classificatore è un meccanismo che combina tutti i classificatori per un solo buffer di testo in un unico set di classificazioni. Ad esempio, sia un classificatore C# che un classificatore in lingua inglese possono creare classificazioni su un commento in un file C#. Prendere in considerazione questo commento:

```
// This method produces a classifier
```

Un classificatore C# potrebbe etichettare l'intero intervallo come commento e il classificatore della lingua inglese potrebbe classificare "produce" come "verbo" e "metodo" come "sostantivo". Aggregator produce un set di classificazioni non sovrapposte e il tipo del set si basa su tutti i contributi.

Un aggregatore di classificatore è anche un classificatore perché suddivide il testo in un set di classificazioni. L'aggregatore di classificazione garantisce inoltre che non esistano classificazioni sovrapposte e che le classificazioni siano ordinate. I singoli classificatori sono liberi di restituire qualsiasi set di classificazioni, in qualsiasi ordine e sovrapposte in qualsiasi modo.

#### <a name="classification-formatting-and-text-coloring"></a>Formattazione della classificazione e colorazione del testo

La formattazione del testo è un esempio di una funzionalità basata sulla classificazione di testo. Viene utilizzato dal livello di visualizzazione di testo per determinare la visualizzazione del testo in un'applicazione. L'area di formattazione del testo dipende da WPF, ma la definizione logica delle classificazioni non lo è.

Un formato di classificazione è un set di proprietà di formattazione per un tipo di classificazione specifico. Questi formati ereditano dal formato dell'elemento padre del tipo di classificazione.

Un oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> è una mappa da un tipo di classificazione a un set di proprietà di formattazione del testo. L'implementazione della mappa del formato nell'Editor gestisce tutte le esportazioni dei formati di classificazione.

### <a name="adornments"></a>Aree

Gli elementi decorativi sono effetti grafici che non sono direttamente correlati al tipo di carattere e al colore dei caratteri nella visualizzazione di testo. Ad esempio, la sottolineatura rossa zigzag che viene usata per contrassegnare il codice non compilato in molti linguaggi di programmazione è un'area di controllo incorporata e le descrizioni comandi sono aree di controllo popup. Le aree di strumenti sono derivate da <xref:System.Windows.UIElement> e implementano <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Due tipi specializzati di tag di ornamento sono <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , per le aree di visualizzazione che occupano lo stesso spazio del testo in una visualizzazione e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> per la sottolineatura zigzag.

Gli elementi decorativi incorporati sono elementi grafici che fanno parte della visualizzazione di testo formattata. Sono organizzati in diversi livelli dell'ordine Z. Sono disponibili tre livelli predefiniti, come segue: testo, cursore e selezione. Tuttavia, gli sviluppatori possono definire più livelli e inserirli nell'ordine rispetto a un altro. I tre tipi di aree di controllo incorporate sono le aree di controllo relative al testo (che si muovono quando il testo viene spostato e vengono eliminate quando il testo viene eliminato), le aree di controllo relative alle visualizzazioni (che devono essere eseguite con parti non di testo della visualizzazione) e le aree di controllo del proprietario (lo sviluppatore deve gestire la posizione).

Le aree di controllo popup sono elementi grafici che vengono visualizzati in una piccola finestra sopra la visualizzazione di testo, ad esempio le descrizioni comandi.

### <a name="projection"></a><a name="projection"></a> Proiezione

La proiezione è una tecnica per la creazione di un tipo diverso di buffer di testo che non archivia effettivamente il testo, ma combina il testo da altri buffer di testo. Ad esempio, è possibile usare un buffer di proiezione per concatenare il testo da altri due buffer e presentare il risultato come se si trovasse in un solo buffer o per nascondere parti del testo in un buffer. Un buffer di proiezione può fungere da buffer di origine in un altro buffer di proiezione. È possibile costruire un set di buffer correlati dalla proiezione per ridisporre il testo in molti modi diversi. Un set di questo tipo è noto anche come *grafico del buffer*. La funzionalità di struttura del testo di Visual Studio viene implementata usando un buffer di proiezione per nascondere il testo compresso e l'editor di Visual Studio per le pagine ASP.NET usa la proiezione per supportare linguaggi incorporati, ad esempio Visual Basic e C#.

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Viene creato un oggetto tramite <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Un buffer di proiezione è rappresentato da una sequenza ordinata di <xref:Microsoft.VisualStudio.Text.ITrackingSpan> oggetti noti come *intervalli di origine*. Il contenuto di questi intervalli viene presentato come una sequenza di caratteri. I buffer di testo da cui vengono disegnati gli intervalli di origine vengono denominati *buffer di origine*. I client di un buffer di proiezione non devono essere consapevoli che differisce da un normale buffer di testo.

Il buffer di proiezione è in ascolto degli eventi di modifica del testo nei buffer di origine. Quando viene modificato il testo in un intervallo di origine, il buffer di proiezione esegue il mapping delle coordinate del testo modificate alle proprie coordinate e genera gli eventi di modifica del testo appropriati. Si considerino, ad esempio, i buffer di origine A e B con questi contenuti:

```
A: ABCDE
B: vwxyz
```

Se il buffer di proiezione P è costituito da due intervalli di testo, uno con il buffer A e l'altro con il buffer B, P presenta il contenuto seguente:

```
P: ABCDEvwxyz
```

Se la sottostringa `xy` viene eliminata dal buffer B, il buffer P genera un evento che indica che i caratteri nelle posizioni 7 e 8 sono stati eliminati.

Il buffer di proiezione può anche essere modificato direttamente. Propaga le modifiche ai buffer di origine appropriati. Se, ad esempio, una stringa viene inserita nel buffer P nella posizione 6 (la posizione originale del carattere "v"), l'inserimento viene propagato al buffer B nella posizione 1.

Sono presenti restrizioni sugli intervalli di origine che contribuiscono a un buffer di proiezione. Gli intervalli di origine non possono sovrapporsi. non è possibile eseguire il mapping di una posizione in un buffer di proiezione a più di una posizione in un buffer di origine e non è possibile eseguire il mapping di una posizione in un buffer di origine a più di una posizione in un buffer di proiezione. Non sono consentite circolanze nella relazione del buffer di origine.

Gli eventi vengono generati quando viene modificato il set di buffer di origine per un buffer di proiezione e quando il set di origine si estende.
Un buffer Eliso è un tipo speciale di buffer di proiezione. Viene utilizzato principalmente per la struttura e per le operazioni che espandono e comprimono blocchi di testo. Un buffer di elissi si basa su un solo buffer di origine e gli intervalli nel buffer di Elis devono essere ordinati nello stesso modo in cui sono ordinati nel buffer di origine.

#### <a name="the-buffer-graph"></a>Grafico del buffer

L' <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaccia consente il mapping tra un grafico dei buffer di proiezione. Tutti i buffer di testo e i buffer di proiezione vengono raccolti in un grafico aciclici diretto, molto simile all'albero della sintassi astratta prodotto da un compilatore di linguaggio. Il grafico è definito dal buffer superiore, che può essere qualsiasi buffer di testo. Il grafico del buffer può essere mappato da un punto nel buffer superiore a un punto in un buffer di origine o da un intervallo del buffer superiore a un set di intervalli in un buffer di origine. Analogamente, è possibile eseguire il mapping di un punto o di un intervallo da un buffer di origine a un punto nel buffer superiore. I grafici del buffer vengono creati usando <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Eventi e buffer di proiezione

Quando viene modificato un buffer di proiezione, le modifiche vengono inviate dal buffer di proiezione ai buffer che dipendono da esso. Dopo che tutti i buffer sono stati modificati, vengono generati gli eventi di modifica del buffer, a partire dal buffer più profondo.

### <a name="outlining"></a>struttura

La struttura è la possibilità di espandere o comprimere blocchi di testo diversi in una visualizzazione di testo. La struttura è definita come un tipo di <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , nello stesso modo in cui vengono definite le aree di abbellimento. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> è un tag che definisce un'area di testo che può essere espansa o compressa. Per usare la struttura, è necessario importare l'oggetto <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> per ottenere un oggetto <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Il gestore della struttura enumera, comprime ed espande i diversi blocchi, rappresentati come <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> oggetti, e genera eventi di conseguenza.

### <a name="mouse-bindings"></a>Associazioni del mouse

Le associazioni del mouse collegano i movimenti del mouse a comandi diversi. Le associazioni del mouse vengono definite tramite un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> e i tasti di scelta delle chiavi vengono definiti utilizzando un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Crea automaticamente un'istanza di tutte le associazioni e le connette agli eventi del mouse nella visualizzazione.

L' <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaccia contiene i gestori eventi pre-elaborazione e post-elaborazione per diversi eventi del mouse. Per gestire uno degli eventi, è possibile eseguire l'override di alcuni metodi in <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Operazioni dell'editor

Le operazioni dell'editor possono essere utilizzate per automatizzare l'interazione con l'editor, per gli script o altri scopi. È possibile importare l'oggetto <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> per accedere alle operazioni in un determinato <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . È quindi possibile usare questi oggetti per modificare la selezione, scorrere la visualizzazione o spostare il punto di inserimento in parti diverse della visualizzazione.

### <a name="intellisense"></a>IntelliSense

IntelliSense supporta il completamento delle istruzioni, la guida alla firma, nota anche come informazioni sul parametro, informazioni rapide e lampadine.

Il completamento delle istruzioni fornisce elenchi popup di possibili completamenti per i nomi dei metodi, gli elementi XML e altri elementi di codifica o di markup. In generale, un gesto utente richiama una sessione di completamento. La sessione Visualizza l'elenco dei completamenti potenziali e l'utente può selezionarne uno o chiudere l'elenco. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>È responsabile della creazione e dell'attivazione dell'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Calcola l'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> di elementi di completamento per la sessione.

## <a name="see-also"></a>Vedere anche

- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
- [Importazioni editor](../extensibility/editor-imports.md)
