---
title: Informazioni su modelli, classi e relazioni
description: Informazioni su come viene definito un linguaggio specifico di dominio (DSL) dal relativo file di definizione DSL e che la maggior parte del codice del programma nella soluzione DSL viene generata da questo file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: e1fed82d9a8baaf44300e002a5436a532781ed01
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116578"
---
# <a name="understanding-models-classes-and-relationships"></a>Informazioni su modelli, classi e relazioni
Un linguaggio specifico di dominio (DSL) è definito dal relativo file di definizione DSL, insieme a qualsiasi codice di programma personalizzato che è possibile scrivere. La maggior parte del codice del programma nella soluzione DSL viene generata da questo file.

 Questo argomento illustra le funzionalità centrali della definizione DSL.

## <a name="the-dsl-definition"></a>Definizione DSL
 Quando si apre `Dsl\DslDefinition.dsl` , la finestra Visual Studio simile all'immagine seguente.

 ![Progettazione DSL](../modeling/media/dsl_designer.png)

 Le informazioni più importanti nella definizione DSL vengono visualizzate nel diagramma di definizione DSL. Informazioni aggiuntive, che fanno anche parte di DslDefinition.dsl, vengono visualizzate in Esplora DSL, che in genere viene visualizzato a lato del diagramma. Si lavora con il diagramma per le attività più frequenti e con Esplora DSL per personalizzazioni più avanzate.

 Il diagramma definizione DSL mostra le classi di dominio che definiscono gli elementi del modello e le relazioni che definiscono i collegamenti tra gli elementi del modello. Mostra anche le forme e i connettori usati per visualizzare gli elementi del modello all'utente.

 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png)

 Quando si seleziona un elemento nella definizione DSL, nel diagramma o in Esplora DSL, le informazioni su di esso vengono visualizzate nel Finestra Proprietà. Nella finestra Dettagli DSL possono essere visualizzate informazioni aggiuntive.

### <a name="models-are-instances-of-dsls"></a>I modelli sono istanze di DSL
 Un *modello* è un'istanza del DSL creata da un utente. Un modello contiene elementi del modello, ovvero istanze delle classi di dominio definite dall'utente, e collegamenti tra gli elementi, ovvero istanze delle relazioni di dominio definite. Un modello può anche avere forme e connettori, che visualizzano gli elementi del modello e i collegamenti in un diagramma. La definizione DSL include le classi shape, le classi connettore e una classe per il diagramma.

 Una definizione DSL è nota anche come modello *di dominio*. Una definizione DSL o un modello di dominio è la rappresentazione in fase di progettazione del linguaggio specifico di dominio, mentre il modello è la creazione di istanze in fase di esecuzione del linguaggio specifico di dominio.

## <a name="domain-classes-define-model-elements"></a>Le classi di dominio definiscono gli elementi del modello
 Le classi di dominio vengono usate per creare i vari elementi del dominio e le relazioni di dominio sono i collegamenti tra gli elementi. Si tratta della rappresentazione in fase di progettazione degli elementi e dei collegamenti di cui verrà creata un'istanza dagli utenti del linguaggio specifico della progettazione quando creano i modelli.

 Questa figura mostra un modello creato dall'utente di una libreria musicale DSL. Musica album sono rappresentati da caselle contenenti elenchi di brani. Gli artisti sono rappresentati da caselle arrotondate e sono connessi agli album a cui hanno contribuito.

 ![Modello di istanza generato di DSL](../modeling/media/music_instance.png)

 La definizione DSL separa due aspetti. L'aspetto degli elementi del modello nel diagramma del modello viene definito tramite classi di forme e classi connettore. Le informazioni contenute nel modello vengono definite usando classi di dominio e relazioni di dominio.

 La figura seguente mostra le classi di dominio e le relazioni nella definizione DSL della Musica library.

 ![Relazioni di incorporamento e riferimento](../modeling/media/music_classes.png)

 La figura mostra quattro classi di dominio: Musica, Album, Artista e Brano. Le classi di dominio definiscono le proprietà di dominio, ad esempio Nome, Titolo e così via. Nel modello di istanza i valori di alcune di queste proprietà vengono visualizzati nel diagramma.

 Tra le classi sono presenti relazioni di dominio: MusicHasAlbums, MusicHasArtist, AlbumbHasSongs e ArtistAppearedOnAlbums. Le relazioni hanno molteplicità, ad esempio 1..1, 0..*. Ad esempio, ogni brano deve essere correlato esattamente a un album tramite la relazione AlbumHasSongs. Ogni album può avere un numero qualsiasi di brani.

### <a name="rearranging-the-dsl-definition-diagram"></a>Riorganizzazione del diagramma di definizione DSL
 Si noti che una classe di dominio può essere visualizzata più volte nel diagramma di definizione DSL, come fa Album in questa immagine. Esiste sempre una visualizzazione principale e possono essere presenti alcune *viste di* riferimento.

 Per ridisporre il diagramma di definizione DSL, è possibile:

- Scambiare le visualizzazioni principale e di riferimento usando i **comandi Bring Tree Here (Porta albero qui)** e Split Tree **(Dividi albero).** Fare clic con il pulsante destro del mouse su una singola classe di dominio per visualizzare questi comandi.

- Riordinare le classi di dominio e le classi di forma premendo CTRL+SU e CTRL+GIÙ.

- Comprimere o espandere le classi usando l'icona in alto a destra di ogni forma.

- Comprimere parti dell'albero facendo clic sul segno meno (-) nella parte inferiore di una classe di dominio.

## <a name="inheritance"></a>Ereditarietà
 Le classi di dominio possono essere definite usando l'ereditarietà. Per creare una derivazione di ereditarietà, fare clic su Ereditarietà, fare clic sulla classe derivata e quindi sulla classe di base. Un elemento del modello ha tutte le proprietà definite nella propria classe di dominio, insieme a tutte le proprietà ereditate dalla classe di base. Eredita anche i ruoli nelle relazioni.

 L'ereditarietà può essere usata anche tra relazioni, forme e connettori. L'ereditarietà deve rimanere all'interno dello stesso gruppo. Una forma non può ereditare da una classe di dominio.

## <a name="domain-relationships"></a>Relazioni tra domini
 Gli elementi del modello possono essere collegati da relazioni. I collegamenti sono sempre binari. collegano esattamente due elementi. Tuttavia, qualsiasi elemento può avere molti collegamenti ad altri oggetti e può essere presente anche più di un collegamento tra la stessa coppia di elementi.

 Così come è possibile definire diverse classi di elementi, è possibile definire diverse classi di collegamenti. La classe di un collegamento è detta *relazione di dominio*. Una relazione di dominio specifica le classi dell'elemento che le istanze possono connettere. Ogni fine di una relazione è denominata *ruolo* e la relazione di dominio definisce i nomi per i due ruoli, nonché per la relazione stessa.

 Esistono due tipi di relazioni di dominio: incorporamento di relazioni e relazioni di riferimento. Nel diagramma di definizione DSL le relazioni di incorporamento hanno linee solide per ogni ruolo e le relazioni di riferimento hanno linee tratteggiate.

### <a name="embedding-relationships"></a>Incorporamento di relazioni
 Ogni elemento in un modello, ad eccezione della radice, è la destinazione di un collegamento di incorporamento. Di conseguenza, l'intero modello costituisce un singolo albero di collegamenti di incorporamento. Una relazione di incorporamento rappresenta il contenimento o la proprietà. Due elementi del modello correlati in questo modo sono noti anche come padre e figlio. L'elemento figlio viene detto incorporato nell'elemento padre.

 I collegamenti di incorporamento non vengono in genere visualizzati in modo esplicito come connettori in un diagramma. Al contrario, sono in genere rappresentate da contenimento. La radice del modello è rappresentata dal diagramma e gli elementi incorporati in esso vengono visualizzati come forme nel diagramma.

 Nell'esempio la classe radice Musica ha una relazione di incorporamento MusicHasAlbums con Album, che include un elemento AlbumHasSongs di incorporamento in Song. I brani vengono visualizzati come elementi in un elenco all'interno di ogni album. Musica ha anche un elemento MusicHasArtists incorporato nella classe Artist, le cui istanze vengono visualizzate anche come forme nel diagramma.

 Per impostazione predefinita, gli elementi incorporati vengono eliminati automaticamente quando vengono eliminati gli elementi padre.

 Quando un modello viene salvato in un file in formato XML, gli elementi incorporati vengono annidati all'interno dei relativi elementi padre, a meno che non sia stata personalizzata la serializzazione.

> [!NOTE]
> L'incorporamento è diverso dall'ereditarietà. Gli elementi figlio in una relazione di incorporamento non ereditano le proprietà dell'elemento padre. Un incorporamento è un tipo di collegamento tra gli elementi del modello. L'ereditarietà è una relazione tra classi e non crea collegamenti tra gli elementi del modello.

### <a name="embedding-rules"></a>Regole di incorporamento
 Ogni elemento in un modello di istanza deve essere la destinazione di esattamente un collegamento di incorporamento, ad eccezione della radice del modello.

 Pertanto, ogni classe di dominio non astratta, ad eccezione della classe radice, deve essere la destinazione di almeno una relazione di incorporamento oppure deve ereditare un incorporamento da una classe di base. Una classe può essere la destinazione di due o più incorporamenti, ma i relativi elementi del modello di istanza possono avere un solo elemento padre alla volta. La molteplicità da destinazione a origine deve essere 0..1 o 1..1.

### <a name="the-explorer-displays-the-embedding-tree"></a>In Esplora risorse viene visualizzato l'albero di incorporamento
 La definizione DSL crea anche una finestra di esplorazione, che gli utenti visualizzano insieme al diagramma del modello.

 ![Finestra di esplorazione generata di DSL](../modeling/media/music_explorer.png)

 Lo explorer mostra tutti gli elementi del modello, anche quelli per cui non sono state definite forme. Mostra gli elementi e le relazioni di incorporamento, ma non le relazioni di riferimento.

 Per visualizzare i valori delle proprietà di dominio di un elemento, l'utente seleziona un elemento nel diagramma del modello o in Esplora modelli e apre il Finestra Proprietà. Vengono visualizzate tutte le proprietà di dominio, incluse quelle non visualizzate nel diagramma. Nell'esempio, ogni brano ha sia un titolo che un genere, ma nel diagramma viene visualizzato solo il valore del titolo.

## <a name="reference-relationships"></a>Relazioni di riferimento
 Una relazione di riferimento rappresenta qualsiasi tipo di relazione che non è incorporata.

 Le relazioni di riferimento vengono in genere visualizzate in un diagramma come connettori tra le forme.

 Nella rappresentazione XML del modello, un collegamento di riferimento tra due elementi viene rappresentato tramite *moniker.* I moniker sono nomi che identificano in modo univoco ogni elemento nel modello. Il nodo XML per ogni elemento del modello contiene un nodo che specifica il nome della relazione e il moniker dell'altro elemento.

## <a name="roles"></a>Ruoli
 Ogni relazione di dominio ha due ruoli, un ruolo di origine e un ruolo di destinazione.

 Nell'immagine seguente la linea tra la classe Publisher **di** dominio e la relazione di dominio **PublisherCatalog** è il ruolo di origine. La linea tra la relazione di dominio e la **classe di** dominio Album è il ruolo di destinazione.

 ![Ruoli e proprietà.](../modeling/media/propertycode.png)

 I nomi associati a una relazione sono particolarmente importanti quando si scrive codice di programma che attraversa il modello. Ad esempio, quando si compila la soluzione DSL, la classe generata Publisher ha una proprietà Catalog che è una raccolta di Album. La classe Album ha una proprietà Publisher che è una singola istanza della classe Publisher.

 Quando si crea una relazione in una definizione DSL, ai nomi delle proprietà e delle relazioni vengono dati i valori predefiniti. Tuttavia, è possibile modificarli.

## <a name="multiplicities"></a>Moltiplicazioni
 Le moltiplicazioni specificano quanti elementi possono avere lo stesso ruolo in una relazione di dominio. Nell'esempio, l'impostazione di molteplicità zero-a-molti (0.. ) nel ruolo Catalogo specifica che qualsiasi istanza della classe di dominio Publisher può avere un numero di collegamenti di relazione \* **PublisherCatalog** pari **a** quello desiderato. 

 Configurare la molteplicità di un ruolo digitando nel diagramma o modificando la `Multiplicity` proprietà nella **finestra** Proprietà. Nella tabella seguente vengono descritte le impostazioni per questa proprietà.

|Tipo di molteplicità|Descrizione|
|-|-|
|0..* (da zero a molti)|Ogni istanza della classe di dominio può avere più istanze della relazione o nessuna istanza della relazione.|
|0..1 (da zero a uno)|Ogni istanza della classe di dominio non può avere più di un'istanza della relazione o nessuna istanza della relazione.|
|1..1 (Uno)|Ogni istanza della classe di dominio può avere un'istanza della relazione. Non è possibile creare più di un'istanza di questa relazione da qualsiasi istanza della classe del ruolo. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando in qualsiasi istanza della classe del ruolo non è presente alcuna istanza della relazione.|
|1..* (uno a molti)|Ogni istanza della classe nel ruolo con questa molteplicità può avere più istanze della relazione e ogni istanza deve avere almeno un'istanza della relazione. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando in qualsiasi istanza della classe del ruolo non è presente alcuna istanza della relazione.|

## <a name="domain-relationships-as-classes"></a>Relazioni di dominio come classi
 Un collegamento è rappresentato nell'archivio come istanza di LinkElement, che è una classe derivata di ModelElement. È possibile definire queste proprietà nel diagramma del modello di dominio nelle relazioni di dominio.

 È anche possibile impostare una relazione come origine o destinazione di altre relazioni. Nel diagramma del modello di dominio fare clic con il pulsante destro del mouse sulla relazione di dominio e quindi scegliere **Mostra come classe**. Verrà visualizzata una casella della classe aggiuntiva. È quindi possibile connettere le relazioni.

 È possibile definire una relazione in parte tramite ereditarietà, proprio come è possibile con le classi di dominio. Selezionare la relazione derivata e impostare **Relazione di base** nel Finestra Proprietà.

 Una relazione derivata è specializzata nella relazione di base. Le classi di dominio da cui è collegato devono essere derivate o uguali alle classi collegate dalla relazione di base. Quando in un modello viene creato un collegamento della relazione derivata, si tratta di un'istanza delle relazioni derivate e di base. Nel codice del programma è possibile passare all'estremità opposta del collegamento usando le proprietà generate dalla base o dalla classe derivata.

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))