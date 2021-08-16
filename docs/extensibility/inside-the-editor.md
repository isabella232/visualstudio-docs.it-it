---
title: Componenti e funzionalità dell'editor
description: Informazioni sui sottosistemi e sulle funzionalità dell'editor. È possibile estendere le funzionalità dell'editor Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b7fbf671b20cd923e8adc181179ce3d042ed9326f69638eaee3d5e57d7c1ffa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359793"
---
# <a name="inside-the-editor"></a>All'interno dell'editor

L'editor è costituito da diversi sottosistemi, progettati per mantenere il modello di testo dell'editor separato dalla visualizzazione testo e dall'interfaccia utente.

Queste sezioni descrivono i diversi aspetti dell'editor:

- [Panoramica dei sottosistemi](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Modello di testo](../extensibility/inside-the-editor.md#the-text-model)

- [Visualizzazione di testo](../extensibility/inside-the-editor.md#the-text-view)

Queste sezioni descrivono le funzionalità dell'editor:

- [Tag e classificatori](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ornamenti](../extensibility/inside-the-editor.md#adornments)

- [Proiezione](../extensibility/inside-the-editor.md#projection)

- [struttura](../extensibility/inside-the-editor.md#outlining)

- [Associazioni del mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operazioni dell'editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Panoramica dei sottosistemi

### <a name="text-model-subsystem"></a>Sottosistema del modello di testo

Il sottosistema del modello di testo è responsabile della rappresentazione del testo e dell'abilitazione della manipolazione. Il sottosistema del modello di testo contiene l'interfaccia , che descrive la sequenza di caratteri che deve <xref:Microsoft.VisualStudio.Text.ITextBuffer> essere visualizzata dall'editor. Questo testo può essere modificato, tracciato e modificato in molti modi. Il modello di testo fornisce anche i tipi per gli aspetti seguenti:

- Servizio che associa il testo ai file e gestisce la lettura e la scrittura nel file system.

- Servizio di differenziazione che trova le differenze minime tra due sequenze di oggetti.

- Sistema per la descrizione del testo in un buffer in termini di subset di testo in altri buffer.

Il sottosistema del modello di testo è privo di concetti relativi all'interfaccia utente. Ad esempio, non è responsabile della formattazione del testo o del layout del testo e non ha alcuna conoscenza delle aree di controllo visive che possono essere associate al testo.

I tipi pubblici del sottosistema del modello di testo sono contenuti in *Microsoft.VisualStudio.Text.Data.dll* e *Microsoft.VisualStudio.CoreUtility.dll*, che dipendono solo dalla libreria di classi di base .NET Framework e da Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Sottosistema di visualizzazione testo

Il sottosistema di visualizzazione del testo è responsabile della formattazione e della visualizzazione del testo. I tipi in questo sottosistema sono suddivisi in due livelli, a seconda che i tipi si basano Windows Presentation Foundation (WPF). I tipi più importanti sono e , che controllano il set di righe di testo da visualizzare, e anche il punto di selezione, la selezione e le funzionalità per adornare il testo usando gli elementi dell'interfaccia utente <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> WPF. Questo sottosistema fornisce anche margini intorno all'area di visualizzazione del testo. Questi margini possono essere estesi e possono contenere diversi tipi di contenuto ed effetti visivi. Esempi di margini sono gli schermi dei numeri di riga e le barre di scorrimento.

I tipi pubblici del sottosistema di visualizzazione testo sono contenuti *in* Microsoft.VisualStudio.Text.UI.dlle *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Il primo assembly contiene gli elementi indipendenti dalla piattaforma e il secondo contiene gli elementi specifici di WPF.

### <a name="classification-subsystem"></a>Sottosistema di classificazione

Il sottosistema di classificazione è responsabile della determinazione delle proprietà dei caratteri per il testo. Un classificatore suddivide il testo in classi diverse, ad esempio "parola chiave" o "commento". La mappa del formato di classificazione mette in relazione queste classi con le proprietà effettive del tipo di carattere, ad esempio "Blue Consolas 10 pt". Queste informazioni vengono usate dalla visualizzazione testo quando formatta ed esegue il rendering del testo. L'assegnazione di tag, descritta in modo più dettagliato più avanti in questo argomento, consente di associare dati a intervalli di testo.

I tipi pubblici del sottosistema di classificazione sono contenuti in Microsoft.VisualStudio.Text.Logic.dll e interagiscono con gli aspetti visivi della classificazione, che sono contenuti in Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Sottosistema operazioni

Il sottosistema operazioni definisce il comportamento dell'editor. Fornisce l'implementazione per Visual Studio comandi dell'editor e il sistema di annullamento.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Uno sguardo più da vicino al modello di testo e alla visualizzazione testo

### <a name="the-text-model"></a>Modello di testo

Il sottosistema del modello di testo è costituito da diversi raggruppamenti di tipi di testo. Sono inclusi il buffer di testo, gli snapshot di testo e gli intervalli di testo.

#### <a name="text-buffers-and-text-snapshots"></a>Buffer di testo e snapshot di testo

L'interfaccia rappresenta una sequenza di caratteri Unicode codificati usando UTF-16, ovvero la codifica usata dal tipo nel <xref:Microsoft.VisualStudio.Text.ITextBuffer> `String` .NET Framework. Un buffer di testo può essere reso persistente come file system documento, ma non è obbligatorio.

Viene utilizzato per creare un buffer di testo vuoto o un buffer di testo <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> inizializzato da una stringa o da <xref:System.IO.TextReader> . Il buffer di testo può essere reso persistente nel file system come <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Qualsiasi thread può modificare il buffer di testo fino a quando un thread non diventa proprietario del buffer di testo chiamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Successivamente, solo il thread può eseguire modifiche.

Un buffer di testo può passare attraverso molte versioni durante la sua durata. Viene generata una nuova versione ogni volta che il buffer viene modificato e un oggetto non modificabile rappresenta il contenuto di <xref:Microsoft.VisualStudio.Text.ITextSnapshot> tale versione del buffer. Poiché gli snapshot di testo non sono modificabili, è possibile accedere a uno snapshot di testo in qualsiasi thread, senza restrizioni, anche se il buffer di testo rappresentato continua a cambiare.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Snapshot di testo e righe di snapshot di testo

È possibile visualizzare il contenuto di uno snapshot di testo come sequenza di caratteri o come sequenza di righe. I caratteri e le righe vengono entrambi indicizzati a partire da zero. Uno snapshot di testo vuoto contiene zero caratteri e una riga vuota. Una riga è delimitata da qualsiasi sequenza di caratteri di interruzione di riga Unicode valida o dall'inizio o dalla fine del buffer. I caratteri di interruzione di riga sono rappresentati in modo esplicito nello snapshot di testo e le interruzioni di riga in uno snapshot di testo non devono essere tutte uguali.

> [!NOTE]
> Per altre informazioni sui caratteri di interruzione di riga nell'editor Visual Studio, vedere [Codifiche e interruzioni di riga.](../ide/encodings-and-line-breaks.md)

Una riga di testo è rappresentata da un oggetto , che può essere ottenuto da uno snapshot di testo per un numero di riga specifico o <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> per una posizione di carattere specifica.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections

Rappresenta <xref:Microsoft.VisualStudio.Text.SnapshotPoint> una posizione di carattere in uno snapshot. È garantito che la posizione sia compresa tra zero e la lunghezza dello snapshot. Rappresenta <xref:Microsoft.VisualStudio.Text.SnapshotSpan> un intervallo di testo in uno snapshot. È garantito che la posizione End sia compresa tra zero e la lunghezza dello snapshot. è <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> costituito da un set di oggetti dello stesso <xref:Microsoft.VisualStudio.Text.SnapshotSpan> snapshot.

#### <a name="spans-and-normalizedspancollections"></a>Spans e NormalizedSpanCollections

Rappresenta <xref:Microsoft.VisualStudio.Text.Span> un intervallo che può essere applicato a un intervallo di testo in uno snapshot di testo. Le posizioni dello snapshot sono in base zero, quindi gli intervalli possono iniziare da qualsiasi posizione, incluso zero. La `End` proprietà di un intervallo è uguale alla somma della relativa proprietà e della relativa `Start` `Length` proprietà. Non `Span` include il carattere indicizzato dalla proprietà `End` . Ad esempio, un intervallo con Start=5 e Length=3 ha End=8 e include i caratteri nelle posizioni 5, 6 e 7. La notazione per questo intervallo è [5..8).

Due intervalli si intersecano se hanno posizioni in comune, inclusa la posizione End. Pertanto, l'intersezione di [3, 5) e [2, 7) è [3, 5) e l'intersezione di [3, 5) e [5, 7) è [5, 5). Si noti che [5, 5) è un intervallo vuoto.

Due intervalli si sovrappongono se hanno posizioni in comune, ad eccezione della posizione End. Un intervallo vuoto non si sovrappone mai ad altri intervalli e la sovrapposizione di due intervalli non è mai vuota.

Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> è un elenco di intervalli nell'ordine delle proprietà Start degli intervalli. Nell'elenco vengono uniti gli intervalli sovrapposti o non sovrapposti. Ad esempio, dato il set di intervalli [5..9), [0..1), [3..6) e [9..10), l'elenco normalizzato di intervalli è [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notifiche di modifica di ITextEdit, TextVersion e testo

Il contenuto di un buffer di testo può essere modificato usando un <xref:Microsoft.VisualStudio.Text.ITextEdit> oggetto . La creazione di un oggetto di questo tipo (usando uno dei metodi di ) avvia una transazione di testo `CreateEdit()` costituita da modifiche di <xref:Microsoft.VisualStudio.Text.ITextBuffer> testo. Ogni modifica è una sostituzione di un intervallo di testo nel buffer da una stringa. Le coordinate e il contenuto di ogni modifica vengono espressi in relazione all'istantanea del buffer all'avvio della transazione. L'oggetto regola le coordinate delle modifiche interessate da <xref:Microsoft.VisualStudio.Text.ITextEdit> altre modifiche nella stessa transazione.

Si consideri ad esempio un buffer di testo che contiene questa stringa:

```
abcdefghij
```

Applicare una transazione che contiene due modifiche, una modifica che sostituisce l'intervallo in [2..4) usando il carattere e una seconda modifica che sostituisce l'intervallo in `X` [6..9) usando il carattere `Y` . Il risultato è questo buffer:

```
abXefYj
```

Le coordinate per la seconda modifica sono state calcolate in relazione al contenuto del buffer all'inizio della transazione, prima dell'applicazione della prima modifica.

Le modifiche apportate al buffer vengono applicate quando viene eseguito il <xref:Microsoft.VisualStudio.Text.ITextEdit> commit dell'oggetto chiamando il relativo `Apply()` metodo . Se si è verificata almeno una modifica non vuota, viene creato un nuovo oggetto , viene creato un nuovo oggetto <xref:Microsoft.VisualStudio.Text.ITextVersion> e viene generato un evento <xref:Microsoft.VisualStudio.Text.ITextSnapshot> `Changed` . Ogni versione di testo ha uno snapshot di testo diverso. Uno snapshot di testo rappresenta lo stato completo del buffer di testo dopo una transazione di modifica, ma una versione di testo descrive solo le modifiche da uno snapshot a quello successivo. In generale, gli snapshot di testo devono essere usati una sola volta e quindi eliminati, mentre le versioni del testo devono rimanere attivo per un certo periodo di tempo.

Una versione di testo contiene un oggetto <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Questa raccolta descrive le modifiche che, se applicate al snapshot, producono lo snapshot successivo. Ogni <xref:Microsoft.VisualStudio.Text.ITextChange> oggetto nella raccolta contiene la posizione del carattere della modifica, la stringa sostituita e la stringa di sostituzione. La stringa sostituita è vuota per un inserimento di base e la stringa di sostituzione è vuota per un'eliminazione di base. La raccolta normalizzata è sempre `null` per la versione più recente del buffer di testo.

È possibile creare un'istanza di un solo oggetto per un buffer di testo in qualsiasi momento e tutte le modifiche di testo devono essere eseguite sul thread proprietario del buffer di testo (se è stata richiesta la <xref:Microsoft.VisualStudio.Text.ITextEdit> proprietà). Una modifica di testo può essere abbandonata chiamando il `Cancel` relativo metodo o il relativo metodo `Dispose` .

<xref:Microsoft.VisualStudio.Text.ITextBuffer> fornisce anche `Insert()` metodi , e simili a quelli `Delete()` `Replace()` trovati <xref:Microsoft.VisualStudio.Text.ITextEdit> nell'interfaccia . La chiamata di questi metodi ha lo stesso effetto della creazione <xref:Microsoft.VisualStudio.Text.ITextEdit> di un oggetto, dell'esecuzione della chiamata simile e dell'applicazione della modifica.

#### <a name="tracking-points-and-tracking-spans"></a>Punti di rilevamento e intervalli di rilevamento

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> oggetto rappresenta la posizione di un carattere in un buffer di testo. Se il buffer viene modificato in modo da causare lo spostamento della posizione del carattere, il punto di rilevamento si sposta con esso. Ad esempio, se un punto di rilevamento fa riferimento alla posizione 10 in un buffer e all'inizio del buffer vengono inseriti cinque caratteri, il punto di rilevamento fa quindi riferimento alla posizione 15. Se un inserimento si verifica esattamente nella posizione denotata dal punto di rilevamento, il relativo comportamento è determinato da , che può <xref:Microsoft.VisualStudio.Text.PointTrackingMode> essere `Positive` o `Negative` . Se la modalità di rilevamento è positiva, il punto di rilevamento fa riferimento allo stesso carattere, che ora si trova alla fine dell'inserimento. Se la modalità di rilevamento è negativa, il punto di rilevamento fa riferimento al primo carattere inserito nella posizione originale. Se il carattere nella posizione rappresentata da un punto di rilevamento viene eliminato, il punto di rilevamento passa al primo carattere successivo all'intervallo eliminato. Ad esempio, se un punto di rilevamento fa riferimento al carattere nella posizione 5 e i caratteri nelle posizioni da 3 a 6 vengono eliminati, il punto di rilevamento fa riferimento al carattere nella posizione 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> oggetto rappresenta un intervallo di caratteri anziché una sola posizione. Il comportamento è determinato dal relativo <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> oggetto . Se la modalità di rilevamento span [è SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), l'intervallo di rilevamento aumenta per incorporare il testo inserito ai bordi. Se la modalità di rilevamento span [è SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), l'intervallo di rilevamento non incorpora il testo inserito ai bordi. Tuttavia, se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), un inserimento inserisce la posizione corrente verso l'inizio e se la modalità di rilevamento dell'intervallo è [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), un inserimento inserisce la posizione corrente verso la fine.

È possibile ottenere la posizione di un punto di rilevamento o l'intervallo di un intervallo di rilevamento per qualsiasi snapshot del buffer di testo a cui appartengono. I punti di rilevamento e gli intervalli di rilevamento possono essere referenziati in modo sicuro da qualsiasi thread.

#### <a name="content-types"></a>Tipi di contenuto

I tipi di contenuto sono un meccanismo per la definizione di diversi tipi di contenuto. Un tipo di contenuto può essere un tipo di file, ad esempio "text", "code" o "binary" o un tipo di tecnologia come "xml", "vb" o "c#". Ad esempio, la parola "using" è una parola chiave sia in C# che in Visual Basic, ma non in altri linguaggi di programmazione. Pertanto, la definizione di questa parola chiave sarebbe limitata ai tipi di contenuto "c#" e "vb".

I tipi di contenuto vengono usati come filtro per le aree di controllo e altri elementi dell'editor. Molte funzionalità dell'editor e punti di estensione sono definiti per ogni tipo di contenuto. Ad esempio, la colorazione del testo è diversa per i file di testo normale, i file XML e Visual Basic di codice sorgente. Ai buffer di testo viene in genere assegnato un tipo di contenuto al momento della creazione e il tipo di contenuto di un buffer di testo può essere modificato.

I tipi di contenuto possono ereditare più da altri tipi di contenuto. consente <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> di specificare più tipi di base come elementi padre di un determinato tipo di contenuto.

Gli sviluppatori possono definire i propri tipi di contenuto e registrarli usando <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Molte funzionalità dell'editor possono essere definite in relazione a un tipo di contenuto specifico tramite <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Ad esempio, i margini dell'editor, le aree di controllo e i gestori del mouse possono essere definiti in modo che siano applicabili solo agli editor che visualizzano tipi di contenuto specifici.

### <a name="the-text-view"></a>Visualizzazione testo

La parte di visualizzazione del modello MVC (Model View Controller) definisce la visualizzazione testo, la formattazione della visualizzazione, gli elementi grafici, ad esempio la barra di scorrimento e il punto di controllo. Tutti gli elementi di presentazione dell Visual Studio editor sono basati su WPF.

#### <a name="text-views"></a>Visualizzazioni testo

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>L'interfaccia è una rappresentazione indipendente dalla piattaforma di una visualizzazione di testo. Viene usato principalmente per visualizzare documenti di testo in una finestra, ma può essere usato anche per altri scopi, ad esempio in una descrizione comando.

La visualizzazione testo fa riferimento a diversi tipi di buffer di testo. La proprietà fa riferimento a un oggetto che punta a questi tre diversi buffer di testo: il buffer di dati, ovvero il buffer a livello di dati principale, il buffer di modifica, in cui si verifica la modifica, e il buffer visivo, ovvero il buffer visualizzato nella visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> testo.

Il testo viene formattato in base ai classificatori collegati al buffer di testo sottostante e viene decorato usando i provider di strumenti decorativi associati alla visualizzazione testo stessa.

#### <a name="the-text-view-coordinate-system"></a>Sistema di coordinate della visualizzazione testo

Il sistema di coordinate della visualizzazione testo specifica le posizioni nella visualizzazione testo. In questo sistema di coordinate, il valore x 0,0 corrisponde al bordo sinistro del testo visualizzato e il valore y 0,0 corrisponde al bordo superiore del testo visualizzato. La coordinata x aumenta da sinistra a destra e la coordinata y aumenta dall'alto verso il basso.

Un viewport (la parte del testo visibile nella finestra di testo) non può essere scorrendo orizzontalmente nello stesso modo in cui viene fatto scorrere verticalmente. Uno scorrimento orizzontale di un viewport viene modificato modificando la coordinata sinistra in modo che si svolgi rispetto alla superficie di disegno. È tuttavia possibile scorrere verticalmente un riquadro di visualizzazione solo modificando il testo sottoposto a rendering, causando la <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> generazione di un evento .

Le distanze nel sistema di coordinate corrispondono ai pixel logici. Se la superficie di rendering del testo viene visualizzata senza una trasformazione di ridimensionamento, un'unità nel sistema di coordinate di rendering del testo corrisponde a un pixel sullo schermo.

#### <a name="margins"></a>Margini

<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>L'interfaccia rappresenta un margine e consente il controllo della visibilità del margine e delle relative dimensioni. Sono disponibili quattro margini predefiniti, denominati "Top", "Left", "Right" e "Bottom" e collegati al bordo superiore, inferiore, sinistro o destro di una visualizzazione. Questi margini sono contenitori in cui è possibile inserire altri margini. L'interfaccia definisce i metodi che restituiscono le dimensioni del margine e la visibilità di un margine. I margini sono elementi visivi che forniscono informazioni aggiuntive sulla visualizzazione testo a cui sono collegati. Ad esempio, il margine del numero di riga visualizza i numeri di riga per la visualizzazione testo. Il margine del glifo visualizza gli elementi dell'interfaccia utente.

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>L'interfaccia gestisce la creazione e la posizione dei margini. I margini possono essere ordinati rispetto ad altri margini. I margini con priorità più alta si trovano più vicino alla visualizzazione testo. Ad esempio, se sono presenti due margini sinistro, il margine A e il margine B, e il margine B ha una priorità inferiore rispetto al margine A, il margine B viene visualizzato a sinistra del margine A.

#### <a name="the-text-view-host"></a>Host di visualizzazione del testo

L'interfaccia contiene la visualizzazione testo e tutte le decorazione di stile che accompagnano la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> visualizzazione, ad esempio le barre di scorrimento. L'host della visualizzazione testo contiene anche margini collegati a un bordo della visualizzazione.

#### <a name="formatted-text"></a>Testo formattato

Il testo visualizzato in una visualizzazione testo è costituito da <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oggetti . Ogni riga di visualizzazione testo corrisponde a una riga di testo nella visualizzazione testo. Le righe lunghe nel buffer di testo sottostante possono essere parzialmente nascoste (se il ritorno a capo automatico non è abilitato) o suddivise in più righe di visualizzazione del testo. L'interfaccia contiene metodi e proprietà per il mapping tra coordinate e caratteri e per le aree di <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> controllo che possono essere associate alla riga.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Gli oggetti vengono creati tramite <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> un'interfaccia . Se si è semplicemente interessati al testo attualmente visualizzato nella visualizzazione, è possibile ignorare l'origine della formattazione. Se si è interessati al formato del testo non visualizzato nella visualizzazione , ad esempio per supportare le operazioni taglia e incolla in formato RTF, è possibile usare per formattare il testo in un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> buffer di testo.

La visualizzazione testo viene formattata <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> una alla volta.

## <a name="editor-features"></a>Funzionalità dell'editor

Le funzionalità dell'editor sono progettate in modo che la definizione della funzionalità sia separata dall'implementazione. L'editor include le funzionalità seguenti:

- Tag e classificatori

- Ornamenti

- Proiezione

- struttura

- Tasti di scelta del mouse e tasti

- Operazioni e primitive

- IntelliSense

### <a name="tags-and-classifiers"></a>Tag e classificatori

I tag sono marcatori associati a un intervallo di testo. Possono essere presentati in modi diversi, ad esempio usando la colorazione del testo, le sottolineature, la grafica o i popup. I classificatori sono un tipo di tag.

Altri tipi di tag sono <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> per l'evidenziazione del testo, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> per la struttura e per gli errori di <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> compilazione.

#### <a name="classification-types"></a>Tipi di classificazione

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Un'interfaccia rappresenta una classe di equivalenza, ovvero una categoria astratta di testo. I tipi di classificazione possono ereditare più da altri tipi di classificazione. Ad esempio, le classificazioni del linguaggio di programmazione possono includere "keyword", "comment" e "identifier", che ereditano tutte da "code". I tipi di classificazione del linguaggio naturale possono includere "sostantivo", "verbo" e "aggettivo", che ereditano tutti dal "linguaggio naturale".

#### <a name="classifications"></a>Classificazioni

Una classificazione è un'istanza di un particolare tipo di classificazione, in genere su un intervallo di testo. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> oggetto viene usato per rappresentare una classificazione. Un intervallo di classificazione può essere pensato come un'etichetta che copre un particolare intervallo di testo e indica al sistema che questo intervallo di testo è di un particolare tipo di classificazione.

#### <a name="classifiers"></a>Classificatori

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> è un meccanismo che suddivide il testo in un set di classificazioni. I classificatori devono essere definiti per tipi di contenuto specifici e creare un'istanza per buffer di testo specifici. I client devono <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> implementare per partecipare alla classificazione del testo.

#### <a name="classifier-aggregators"></a>Aggregatori di classificatori

Un aggregatore di classificatori è un meccanismo che combina tutti i classificatori per un buffer di testo in un solo set di classificazioni. Ad esempio, sia un classificatore C# che un classificatore in lingua inglese possono creare classificazioni su un commento in un file C#. Prendere in considerazione questo commento:

```
// This method produces a classifier
```

Un classificatore C# potrebbe etichettare l'intero intervallo come commento e il classificatore in lingua inglese potrebbe classificare "produce" come "verbo" e "metodo" come "sostantivo". L'aggregatore produce un set di classificazioni non sovrapposte e il tipo del set è basato su tutti i contributi.

Un aggregatore di classificatori è anche un classificatore perché suddivide il testo in un set di classificazioni. L'aggregatore di classificatori garantisce anche che non siano presenti classificazioni sovrapposte e che le classificazioni siano ordinate. I singoli classificatori sono liberi di restituire qualsiasi set di classificazioni, in qualsiasi ordine e sovrapposti in qualsiasi modo.

#### <a name="classification-formatting-and-text-coloring"></a>Formattazione della classificazione e colorazione del testo

La formattazione del testo è un esempio di funzionalità che si basa sulla classificazione del testo. Viene usato dal livello di visualizzazione del testo per determinare la visualizzazione del testo in un'applicazione. L'area di formattazione del testo dipende da WPF, ma la definizione logica delle classificazioni non lo fa.

Un formato di classificazione è un set di proprietà di formattazione per un tipo di classificazione specifico. Questi formati ereditano dal formato dell'elemento padre del tipo di classificazione.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> oggetto è una mappa da un tipo di classificazione a un set di proprietà di formattazione del testo. L'implementazione della mappa formato nell'editor gestisce tutte le esportazioni dei formati di classificazione.

### <a name="adornments"></a>Ornamenti

Le aree di controllo sono effetti grafici non direttamente correlati al tipo di carattere e al colore dei caratteri nella visualizzazione testo. Ad esempio, la sottolineatura a sottolineatura ondulata rossa usata per contrassegnare il codice non di compilazione in molti linguaggi di programmazione è un'area di controllo incorporata e le descrizioni comando sono aree di controllo popup. Le aree di controllo derivano da <xref:System.Windows.UIElement> e implementano <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Due tipi specializzati di tag di area di controllo sono , per le aree di controllo che occupano lo stesso spazio del testo in una visualizzazione e , per la sottolineatura a sottolineatura a <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> sottolineatura ondulata.

Le aree di controllo incorporate sono elementi grafici che fanno parte della visualizzazione testo formattata. Sono organizzati in diversi livelli dell'ordine Z. Sono disponibili tre livelli predefiniti, come indicato di seguito: testo, punti di accesso e selezione. Tuttavia, gli sviluppatori possono definire più livelli e metterli in ordine l'uno rispetto all'altro. I tre tipi di aree di controllo incorporate sono le aree di controllo relative al testo (che vengono spostate quando il testo viene spostato e vengono eliminate quando il testo viene eliminato), le aree di controllo relative alla visualizzazione (che hanno a che fare con parti non di testo della visualizzazione) e le aree di controllo del proprietario (lo sviluppatore deve gestire la posizione).

Le aree di controllo popup sono elementi grafici visualizzati in una piccola finestra sopra la visualizzazione di testo, ad esempio descrizioni comando.

### <a name="projection"></a><a name="projection"></a> Proiezione

La proiezione è una tecnica per costruire un tipo diverso di buffer di testo che non archivia effettivamente il testo, ma combina invece il testo di altri buffer di testo. Ad esempio, un buffer di proiezione può essere usato per concatenare il testo da altri due buffer e presentare il risultato come se si trovasse in un solo buffer o per nascondere parti del testo in un buffer. Un buffer di proiezione può fungere da buffer di origine in un altro buffer di proiezione. È possibile costruire un set di buffer correlati dalla proiezione per ridisporre il testo in molti modi diversi. Un set di questo tipo è noto anche come *grafico del buffer.* La funzionalità di struttura del testo Visual Studio viene implementata usando un buffer di proiezione per nascondere il testo compresso e l'editor Visual Studio per le pagine ASP.NET usa la proiezione per supportare linguaggi incorporati come Visual Basic e C#.

Viene <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> creato un oggetto utilizzando <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Un buffer di proiezione è rappresentato da una sequenza ordinata di oggetti <xref:Microsoft.VisualStudio.Text.ITrackingSpan> noti come *intervalli di origine.* Il contenuto di questi intervalli viene presentato come una sequenza di caratteri. I buffer di testo da cui vengono disegnati gli intervalli di origine sono denominati *buffer di origine.* I client di un buffer di proiezione non devono essere consapevoli del fatto che è diverso da un buffer di testo normale.

Il buffer di proiezione è in ascolto degli eventi di modifica del testo nei buffer di origine. Quando il testo in un intervallo di origine cambia, il buffer di proiezione esegue il mapping delle coordinate di testo modificate alle proprie coordinate e genera gli eventi di modifica del testo appropriati. Si considerino ad esempio i buffer di origine A e B con il contenuto seguente:

```
A: ABCDE
B: vwxyz
```

Se il buffer di proiezione P è formato da due intervalli di testo, uno con tutto il buffer A e l'altro con tutto il buffer B, P ha il contenuto seguente:

```
P: ABCDEvwxyz
```

Se la sottostringa viene eliminata dal buffer B, il buffer P genera un evento che indica che i caratteri nelle posizioni 7 e `xy` 8 sono stati eliminati.

Il buffer di proiezione può anche essere modificato direttamente. Propaga le modifiche ai buffer di origine appropriati. Ad esempio, se una stringa viene inserita nel buffer P nella posizione 6 (posizione originale del carattere "v"), l'inserimento viene propagato nel buffer B nella posizione 1.

Esistono restrizioni sugli intervalli di origine che contribuiscono a un buffer di proiezione. Gli intervalli di origine non possono sovrapporsi. una posizione in un buffer di proiezione non può essere mappata a più di una posizione in qualsiasi buffer di origine e una posizione in un buffer di origine non può eseguire il mapping a più di una posizione in un buffer di proiezione. Non sono consentite circolari nella relazione del buffer di origine.

Gli eventi vengono generati quando il set di buffer di origine per un buffer di proiezione cambia e quando il set di intervalli di origine cambia.
Un buffer di elisione è un tipo speciale di buffer di proiezione. Viene usato principalmente per la struttura e per le operazioni che espandono e comprendono blocchi di testo. Un buffer di elisione è basato su un solo buffer di origine e gli intervalli nel buffer di elisione devono essere ordinati nello stesso modo in cui vengono ordinati nel buffer di origine.

#### <a name="the-buffer-graph"></a>Grafico del buffer

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>L'interfaccia consente il mapping in un grafico di buffer di proiezione. Tutti i buffer di testo e i buffer di proiezione vengono raccolti in un grafo aciclico diretto, in modo simile all'albero della sintassi astratta prodotto da un compilatore di linguaggio. Il grafico è definito dal buffer superiore, che può essere qualsiasi buffer di testo. Il grafico del buffer può essere mappato da un punto nel buffer superiore a un punto in un buffer di origine o da un intervallo nel buffer superiore a un set di intervalli in un buffer di origine. Analogamente, può eseguire il mapping di un punto o di un intervallo da un buffer di origine a un punto nel buffer superiore. I grafici del buffer vengono creati usando <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Eventi e buffer di proiezione

Quando un buffer di proiezione viene modificato, le modifiche vengono inviate dal buffer di proiezione ai buffer che dipendono da esso. Dopo la modifica di tutti i buffer, vengono generati eventi di modifica del buffer, a partire dal buffer più profondo.

### <a name="outlining"></a>struttura

La struttura è la possibilità di espandere o comprimere blocchi di testo diversi in una visualizzazione di testo. La struttura è definita come un tipo di , nello stesso modo in cui vengono definite <xref:Microsoft.VisualStudio.Text.Tagging.ITag> le aree di controllo. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> è un tag che definisce un'area di testo che può essere espansa o compressa. Per usare la struttura , è necessario importare per <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> ottenere <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> un oggetto . Il gestore della struttura enumera, comprime ed espande i diversi blocchi, rappresentati come oggetti, e genera <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> eventi di conseguenza.

### <a name="mouse-bindings"></a>Associazioni del mouse

Le associazioni del mouse collegano i movimenti del mouse a comandi diversi. Le associazioni del mouse vengono definite tramite un oggetto e le associazioni di tasti vengono definite <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> tramite <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> un oggetto . Crea <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automaticamente un'istanza di tutte le associazioni e le connette agli eventi del mouse nella visualizzazione.

<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>L'interfaccia contiene gestori eventi di pre-elaborazione e post-elaborazione per diversi eventi del mouse. Per gestire uno degli eventi, è possibile eseguire l'override di alcuni metodi in <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Operazioni dell'editor

Le operazioni dell'editor possono essere usate per automatizzare l'interazione con l'editor, a scopo di scripting o per altri scopi. È possibile importare per <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> accedere alle operazioni in un determinato oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . È quindi possibile usare questi oggetti per modificare la selezione, scorrere la visualizzazione o spostare il punto di selezione in parti diverse della visualizzazione.

### <a name="intellisense"></a>IntelliSense

IntelliSense supporta il completamento delle istruzioni, la guida alla firma (note anche come informazioni sui parametri), le informazioni rapide e le lampadine.

Il completamento delle istruzioni fornisce elenchi popup di potenziali completamenti per i nomi dei metodi, gli elementi XML e altri elementi di codice o markup. In generale, un movimento dell'utente richiama una sessione di completamento. La sessione visualizza l'elenco dei potenziali completamenti e l'utente può selezionarne uno o ignorarne uno. è <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> responsabile della creazione e dell'attivazione di <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . Calcola <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> l'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> degli elementi di completamento per la sessione.

## <a name="see-also"></a>Vedi anche

- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
- [Importazioni dell'editor](../extensibility/editor-imports.md)
