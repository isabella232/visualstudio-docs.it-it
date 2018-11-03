---
title: Informazioni su modelli, classi e relazioni
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 74172b6e7f03d7e3baef329f053fc4a83ee6ae28
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967389"
---
# <a name="understanding-models-classes-and-relationships"></a>Informazioni su modelli, classi e relazioni
Un linguaggio specifico di dominio (DSL) è definito dal relativo file di definizione DSL, insieme a qualsiasi codice programma personalizzato che è possibile scrivere. La maggior parte del codice del programma nella soluzione DSL viene generato da questo file.

 Questo argomento illustra le funzionalità principali di definizione DSL.

## <a name="the-dsl-definition"></a>La definizione DSL
 Quando si apre `Dsl\DslDefinition.dsl`, finestra di Visual Studio è simile all'immagine seguente.

 ![Progettazione DSL](../modeling/media/dsl_designer.png)

 Vengono visualizzate le informazioni più importanti nella definizione DSL del diagramma di definizione DSL. Informazioni aggiuntive, che fa anche parte di Dsldefinition, viene visualizzate in Esplora DSL, che in genere viene visualizzato nel riquadro laterale del diagramma. Si lavora con il diagramma per le attività più frequenti e DSL Explorer per le personalizzazioni più avanzate.

 Diagramma di definizione DSL vengono illustrate le classi di dominio che definiscono gli elementi del modello e le relazioni che definiscono i collegamenti tra elementi del modello. Indica anche le forme e connettori che consentono di visualizzare gli elementi del modello per l'utente.

 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png)

 Quando si seleziona un elemento nella definizione DSL, nel diagramma o in Esplora DSL, informazioni su di esso viene visualizzate nella finestra Proprietà. Informazioni aggiuntive possono essere visualizzate nella finestra Dettagli DSL.

### <a name="models-are-instances-of-dsls"></a>I modelli sono istanze dei linguaggi specifici di dominio
 Oggetto *modello* è un'istanza del linguaggio DSL creata da un utente. Un modello contiene elementi del modello, che sono istanze di classi di dominio che definiscono e i collegamenti tra gli elementi, che sono istanze delle relazioni di dominio che definiscono. Un modello può anche avere forme e connettori, che visualizza gli elementi di modello e i collegamenti in un diagramma. La definizione DSL include le classi forma, connettore classi e una classe del diagramma.

 Una definizione DSL è noto anche come un *modello di dominio*. Un modello di dominio o di definizione DSL è la rappresentazione design-time del linguaggio specifico di dominio, mentre il modello è la creazione dell'istanza di runtime del linguaggio specifico di dominio.

## <a name="domain-classes-define-model-elements"></a>Le classi di dominio definiscono gli elementi del modello
 Classi di dominio vengono utilizzate per creare i vari elementi del dominio e le relazioni di dominio sono i collegamenti tra gli elementi. Sono la rappresentazione design-time degli elementi e collegamenti a cui verranno creati dagli utenti del linguaggio specifico di progettazione quando si creano i propri modelli.

 Questa illustrazione mostra un modello che è stato creato dall'utente di un catalogo musicale DSL. Gli album musicali sono rappresentati da caselle che contengono elenchi di brani. Alle creazioni degli artisti sono rappresentati da caselle con angoli arrotondati e sono connessi agli album a cui hanno contribuito.

 ![Modello di istanza generato di DSL](../modeling/media/music_instance.png)

 La definizione DSL separa due aspetti. L'aspetto degli elementi del modello nel diagramma modello viene definito tramite le classi shape e connector. Le informazioni incluse nel modello sono definite tramite le classi di dominio e le relazioni di dominio.

 Nella figura seguente mostra le classi di dominio e le relazioni nella definizione DSL del catalogo musicale.

 ![Relazioni di incorporamento e riferimento](../modeling/media/music_classes.png)

 L'illustrazione mostra quattro classi di dominio: musica, Album, artisti e brano. Le classi di dominio definiscono le proprietà di dominio, ad esempio nome, titolo e così via. Nel modello di istanza, i valori di alcune di queste proprietà vengono visualizzati nel diagramma.

 Tra le classi sono le relazioni di dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs e Artistaapparsoneglialbum. Le relazioni dispongono di molteplicità, ad esempio 1..1, 0.. *. Ogni brano, ad esempio, deve essere correlato a esattamente un Album attraverso la relazione AlbumHasSongs. Ogni Album può avere un numero qualsiasi di brani.

### <a name="rearranging-the-dsl-definition-diagram"></a>Ridisposizione il diagramma di definizione DSL
 Si noti che una classe di dominio può venire visualizzato diverse volte nel diagramma di definizione DSL, così come dell'Album in questa immagine. È sempre presente un'unica visualizzazione principale, e possono essere presenti alcuni *riferimento* viste.

 Per ridisporre il diagramma di definizione DSL, è possibile:

-   Scambia principale e fare riferimento alle viste tramite il **Bring Tree Here** e **Dividi albero** comandi. Fare doppio clic su una classe di dominio singolo per visualizzarne i comandi seguenti.

-   Riordinare le classi di dominio e le classi di forme premendo Ctrl + freccia su e Ctrl + freccia giù.

-   Comprimere o espandere le classi usando l'icona in alto a destra di ciascuna forma.

-   Comprime le parti della struttura ad albero, fare clic sul segno meno (-) nella parte inferiore di una classe di dominio.

## <a name="inheritance"></a>Ereditarietà
 È possibile definire classi di dominio utilizzando l'ereditarietà. Per creare una derivazione di ereditarietà, fare clic sullo strumento di ereditarietà, sulla classe derivata e quindi scegliere la classe di base. Un elemento del modello ha tutte le proprietà definite in una propria classe di dominio, insieme a tutte le proprietà ereditate dalla classe di base. Eredita anche i ruoli nelle relazioni.

 Ereditarietà può essere usata anche tra le relazioni, forme e connettori. Ereditarietà deve mantenere nello stesso gruppo. Una forma non può ereditare da una classe di dominio.

## <a name="domain-relationships"></a>Relazioni di dominio
 È possibile collegare gli elementi del modello tramite relazioni. I collegamenti sono sempre binari; vengono forniti collegamenti esattamente due elementi. Tuttavia, qualsiasi elemento può avere molti collegamenti ad altri oggetti, e può anche essere più di un collegamento tra la stessa coppia di elementi.

 Come è possibile definire diverse classi di elementi, è possibile definire classi diverse di collegamenti. La classe di un collegamento viene chiamata un *relazione di dominio*. Una relazione di dominio specifica quali classi dell'elemento che possono connettersi le relative istanze. Viene chiamato ogni estremità di una relazione di una *ruolo*, e la relazione di dominio definisce i nomi per i due ruoli, nonché per la relazione stessa.

 Esistono due tipi di relazioni di dominio: incorporamento delle relazioni e le relazioni di riferimento. Nel diagramma di definizione DSL, le relazioni di incorporamento sono linee a tinta unita a ogni ruolo e le relazioni di riferimento sono linee tratteggiate.

### <a name="embedding-relationships"></a>Le relazioni di incorporamento
 Ogni elemento in un modello, tranne la radice, è la destinazione di un collegamento di incorporamento. Pertanto, l'intero modello costituisce un singolo albero di incorporamento di collegamenti. Una relazione di incorporamento rappresenta contenuto o la proprietà. Due elementi del modello che sono correlati in questo modo sono noti anche come padre e figlio. L'elemento figlio viene definito da incorporare nell'elemento padre.

 Incorporamento di collegamenti non sono in genere visualizzati in modo esplicito come connettori in un diagramma. In alternativa, in genere sono rappresentate da contenimento. La radice del modello è rappresentata dal diagramma e gli elementi incorporati in essa vengono visualizzati come forme nel diagramma.

 Nell'esempio, la classe radice musica ha una relazione di incorporamento MusicHasAlbums ad Album, dotato di un incorporamento AlbumHasSongs al brano. Canzoni vengono visualizzati come elementi in un elenco all'interno di ogni Album. Musica dispone anche di un incorporamento MusicHasArtists alla classe artista, le cui istanze vengono anche visualizzati come forme nel diagramma.

 Per impostazione predefinita, gli elementi incorporati vengono eliminati automaticamente quando vengono eliminati i padri.

 Quando viene salvato un modello di file in formato XML, gli elementi incorporati sono annidati all'interno di elementi padre, a meno che non è stata personalizzata la serializzazione.

> [!NOTE]
>  L'incorporamento è diverso dall'ereditarietà. Gli elementi figlio in una relazione di incorporamento non ereditano le proprietà dell'elemento padre. Incorporamento è un tipo di collegamento tra elementi del modello. Ereditarietà è una relazione tra classi e di non creare collegamenti tra elementi del modello.

### <a name="embedding-rules"></a>Regole di incorporamento
 Ogni elemento in un modello di istanza deve essere la destinazione di esattamente un collegamento di incorporamento, fatta eccezione per la radice del modello.

 Pertanto, ogni classe di dominio non astratta, ad eccezione della classe radice, deve essere la destinazione di almeno una relazione di incorporamento, o deve ereditare un incorporamento da una classe base. Una classe può essere la destinazione di rappresentazioni distribuite due o più, ma gli elementi di modello di istanza possono avere un solo padre alla volta. La molteplicità di destinazione all'origine deve essere 0..1 1 o 1.

### <a name="the-explorer-displays-the-embedding-tree"></a>Finestra di esplorazione Mostra l'albero di incorporamento
 La definizione DSL creato anche uno strumento di esplorazione, gli utenti vedono insieme ai relativi diagramma del modello.

 ![Finestra di esplorazione generata di DSL](../modeling/media/music_explorer.png)

 Finestra di esplorazione Mostra tutti gli elementi nel modello, anche quelli per cui non è stata definita alcuna forma. Visualizza gli elementi e le relazioni di incorporamento, ma non fare riferimento alle relazioni.

 Per visualizzare i valori delle proprietà di dominio di un elemento, l'utente seleziona un elemento nel diagramma modello o in Esplora modelli e verrà visualizzata la finestra Proprietà. Visualizza tutte le proprietà di dominio, inclusi quelli che non vengono visualizzati nel diagramma. Nell'esempio, ogni brano ha un titolo e un genere, ma viene visualizzato solo il valore del titolo del diagramma.

## <a name="reference-relationships"></a>Relazioni di riferimento
 Una relazione di riferimento rappresenta qualsiasi tipo di relazione che non è di incorporamento.

 Le relazioni di riferimento vengono in genere visualizzate in un diagramma come connettori tra le forme.

 Nella rappresentazione XML del modello, un collegamento di riferimento tra due elementi viene espressa utilizzando *moniker.* Vale a dire i moniker sono nomi che identificano in modo univoco ogni elemento nel modello. Il nodo XML per ogni elemento del modello contiene un nodo che specifica il nome della relazione e il moniker dell'elemento.

## <a name="roles"></a>Ruoli
 Ogni relazione di dominio ha due ruoli, un ruolo di origine e un ruolo di destinazione.

 Nell'immagine seguente, la linea tra i **server di pubblicazione** della classe di dominio e il **PublisherCatalog** relazione di dominio è il ruolo di origine. La riga tra la relazione di dominio e il **Album** della classe di dominio è il ruolo di destinazione.

 ![Ruoli e proprietà.](../modeling/media/propertycode.png)

 I nomi associati a una relazione sono particolarmente importanti quando si scrive codice programma che attraversa il modello. Ad esempio, quando si compila la soluzione DSL, la classe generata, server di pubblicazione ha una proprietà del catalogo che rappresenta una raccolta di album. La classe Album ha una proprietà server di pubblicazione che è una singola istanza della classe server di pubblicazione.

 Quando si crea una relazione in una definizione DSL, valori predefiniti vengono specificati i nomi di proprietà e relazioni. Tuttavia, è possibile modificarli.

## <a name="multiplicities"></a>Molteplicità
 Molteplicità specificare quanti elementi può avere lo stesso ruolo in una relazione di dominio. Nell'esempio zero-a-molti (0..\*) impostazione di molteplicità per il **catalogo** ruolo specifica che qualsiasi istanza del **server di pubblicazione** della classe di dominio può avere un numero  **PublisherCatalog** relazione collega che si desidera assegnare.

 Configurare la molteplicità di un ruolo digitando nel diagramma o modificando la `Multiplicity` proprietà nel **proprietà** finestra. Nella tabella seguente descrive le impostazioni per questa proprietà.

|Tipo di molteplicità|Descrizione|
|-|-|
|0.. * (zero a molti)|Ogni istanza della classe di dominio può avere più istanze della relazione o nessuna istanza della relazione.|
|0..1 (zero a uno)|Ogni istanza della classe di dominio può avere non più di un'istanza della relazione o nessuna istanza della relazione.|
|1..1 (uno)|Ogni istanza della classe di dominio può avere un'istanza della relazione. È possibile creare più di un'istanza di questa relazione da qualsiasi istanza della classe role. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando qualsiasi istanza della classe ruolo non dispone di alcuna istanza della relazione.|
|1.. * (uno a molti)|Ogni istanza della classe nel ruolo con molteplicità di questo può avere più istanze della relazione e ogni istanza deve avere almeno un'istanza della relazione. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando qualsiasi istanza della classe ruolo non dispone di alcuna istanza della relazione.|

## <a name="domain-relationships-as-classes"></a>Relazioni di dominio come classi
 Un collegamento è rappresentato nel Store come un'istanza di LinkElement, ovvero una classe derivata di ModelElement. Nel diagramma del modello di dominio nelle relazioni di dominio, è possibile definire queste proprietà.

 È anche possibile rendere una relazione di origine o destinazione di altre relazioni. Nel diagramma del modello di dominio, fare doppio clic la relazione di dominio e quindi fare clic su **Show As Class**. Verrà visualizzata una finestra di classi aggiuntive. È quindi possibile connettere le relazioni a esso.

 È possibile definire una relazione in parte tramite ereditarietà, proprio come con le classi di dominio. Selezionare la relazione derivata e impostare **relazione Base** nella finestra Proprietà.

 Una relazione derivata specializza la relazione di base. Il dominio delle classi che non devono essere derivati da collegamenti o quello utilizzato per le classi collegate tramite la relazione di base. Quando viene creato un collegamento della relazione derivata in un modello, è un'istanza della classe derivata sia le relazioni di base. Nel codice programma, è possibile passare all'estremità opposta del collegamento utilizzando le proprietà generate da di base o dalla classe derivata.

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
