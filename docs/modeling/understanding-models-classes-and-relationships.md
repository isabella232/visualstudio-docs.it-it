---
title: Informazioni su modelli, classi e relazioni
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391dff6540bcea26f63d8ea88f344455722b742a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748228"
---
# <a name="understanding-models-classes-and-relationships"></a>Informazioni su modelli, classi e relazioni
Un linguaggio specifico di dominio (DSL) viene definito dal file di definizione DSL, insieme a qualsiasi codice del programma personalizzato che è possibile scrivere. La maggior parte del codice programma nella soluzione DSL viene generata da questo file.

 In questo argomento vengono illustrate le funzionalità centrali della definizione DSL.

## <a name="the-dsl-definition"></a>Definizione DSL
 Quando si apre `Dsl\DslDefinition.dsl`, la finestra di Visual Studio è simile all'immagine seguente.

 ![Progettazione DSL](../modeling/media/dsl_designer.png)

 Le informazioni più importanti nella definizione DSL vengono visualizzate nel diagramma di definizione DSL. Informazioni aggiuntive, che fanno parte anche di DslDefinition. DSL, vengono visualizzate in DSL Explorer, che in genere viene visualizzato sul lato del diagramma. Si lavora con il diagramma per le attività più frequenti e con DSL Explorer per le personalizzazioni più avanzate.

 Il diagramma di definizione DSL Mostra le classi di dominio che definiscono gli elementi del modello e le relazioni che definiscono i collegamenti tra gli elementi del modello. Vengono inoltre illustrate le forme e i connettori utilizzati per visualizzare gli elementi del modello all'utente.

 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png)

 Quando si seleziona un elemento nella definizione DSL, nel diagramma o in Esplora DSL, le relative informazioni vengono visualizzate nel Finestra Proprietà. Nella finestra Dettagli DSL potrebbero essere visualizzate informazioni aggiuntive.

### <a name="models-are-instances-of-dsls"></a>I modelli sono istanze di DSLs
 Un *modello* è un'istanza del linguaggio DSL creato da un utente. Un modello contiene elementi del modello, ovvero istanze delle classi di dominio definite dall'utente e collegamenti tra gli elementi, ovvero istanze delle relazioni di dominio definite. Un modello può inoltre disporre di forme e connettori, che visualizzano gli elementi del modello e i collegamenti in un diagramma. La definizione DSL include le classi di forma, le classi del connettore e una classe per il diagramma.

 Una definizione DSL è nota anche come *modello di dominio*. Una definizione DSL o un modello di dominio è la rappresentazione in fase di progettazione del linguaggio specifico di dominio, mentre il modello è l'istanza di runtime del linguaggio specifico di dominio.

## <a name="domain-classes-define-model-elements"></a>Classi di dominio che definiscono gli elementi del modello
 Le classi di dominio vengono utilizzate per creare i vari elementi nel dominio e le relazioni di dominio sono i collegamenti tra gli elementi. Si tratta della rappresentazione in fase di progettazione degli elementi e dei collegamenti di cui verrà creata un'istanza dagli utenti del linguaggio specifico della progettazione quando creano i modelli.

 Questa illustrazione mostra un modello creato dall'utente di un linguaggio DSL della raccolta musicale. Gli album musicali sono rappresentati da caselle contenenti elenchi di canzoni. Gli artisti sono rappresentati da caselle con angoli arrotondati e sono connessi agli album a cui hanno contribuito.

 ![Modello di istanza generato di DSL](../modeling/media/music_instance.png)

 La definizione DSL separa due aspetti. L'aspetto degli elementi del modello nel diagramma del modello viene definito usando le classi di forme e le classi del connettore. Le informazioni trasferite nel modello vengono definite utilizzando le classi di dominio e le relazioni di dominio.

 Nella figura seguente sono illustrate le classi di dominio e le relazioni nella definizione DSL della raccolta musicale.

 ![Relazioni di incorporamento e riferimento](../modeling/media/music_classes.png)

 Nella figura sono illustrate quattro classi di dominio: musica, album, artista e brano. Le classi di dominio definiscono le proprietà del dominio, ad esempio il nome, il titolo e così via. Nel modello di istanza, i valori di alcune di queste proprietà vengono visualizzati nel diagramma.

 Tra le classi sono incluse le relazioni di dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs e Artistaapparsoneglialbum. Le relazioni hanno molteplicità, ad esempio 1.. 1, 0.. *. Ogni brano, ad esempio, deve essere correlato esattamente a un album tramite la relazione AlbumHasSongs. Ogni album può avere un numero qualsiasi di canzoni.

### <a name="rearranging-the-dsl-definition-diagram"></a>Ridisposizione del diagramma di definizione DSL
 Si noti che una classe di dominio può apparire più volte nel diagramma di definizione DSL, come avviene in album in questa immagine. C'è sempre una visualizzazione principale e possono esserci alcune visualizzazioni di *riferimento* .

 Per ridisporre il diagramma di definizione DSL, è possibile:

- Scambiare le visualizzazioni principali e di riferimento usando i comandi **Bring Tree here** e **Split Tree** . Fare clic con il pulsante destro del mouse su una singola classe di dominio per visualizzare questi comandi.

- Riordinare le classi di dominio e le classi di forme premendo CTRL + freccia su e CTRL + freccia giù.

- Comprime o espande le classi utilizzando l'icona in alto a destra di ogni forma.

- Comprime le parti dell'albero facendo clic sul segno meno (-) nella parte inferiore di una classe di dominio.

## <a name="inheritance"></a>Ereditarietà
 È possibile definire le classi di dominio usando l'ereditarietà. Per creare una derivazione di ereditarietà, fare clic sullo strumento ereditarietà, scegliere la classe derivata, quindi fare clic sulla classe di base. Un elemento del modello dispone di tutte le proprietà definite nella propria classe di dominio, insieme a tutte le proprietà ereditate dalla classe base. Eredita inoltre i ruoli nelle relazioni.

 L'ereditarietà può essere utilizzata anche tra relazioni, forme e connettori. L'ereditarietà deve rimanere nello stesso gruppo. Una forma non può ereditare da una classe di dominio.

## <a name="domain-relationships"></a>Relazioni di dominio
 Gli elementi del modello possono essere collegati da relazioni. I collegamenti sono sempre binari; collegano esattamente due elementi. Tuttavia, qualsiasi elemento può avere molti collegamenti ad altri oggetti e può anche essere presente più di un collegamento tra la stessa coppia di elementi.

 Così come è possibile definire classi diverse di elementi, è possibile definire classi di collegamenti diverse. La classe di un collegamento è denominata *relazione di dominio*. Una relazione di dominio specifica le classi di elementi a cui le istanze possono connettersi. Ogni estremità di una relazione viene chiamata *ruolo*e la relazione di dominio definisce i nomi dei due ruoli, nonché per la relazione stessa.

 Esistono due tipi di relazioni di dominio: incorporamento di relazioni e relazioni di riferimento. Nel diagramma di definizione DSL, le relazioni di incorporamento hanno linee continue a ogni ruolo e le relazioni di riferimento hanno linee tratteggiate.

### <a name="embedding-relationships"></a>Incorporamento di relazioni
 Ogni elemento di un modello, ad eccezione della radice, è la destinazione di un collegamento di incorporamento. Pertanto, l'intero modello costituisce un singolo albero di collegamenti di incorporamento. Una relazione di incorporamento rappresenta il contenimento o la proprietà. Due elementi del modello correlati in questo modo sono noti anche come padre e figlio. Il figlio viene definito incorporato nell'elemento padre.

 I collegamenti di incorporamento non vengono in genere visualizzati in modo esplicito come connettori in un diagramma. Sono invece rappresentati in genere da Containment. La radice del modello è rappresentata dal diagramma e gli elementi incorporati vengono visualizzati come forme nel diagramma.

 Nell'esempio, la classe radice Music dispone di una relazione di incorporamento MusicHasAlbums to album, che include un AlbumHasSongs di incorporamento a Song. I brani vengono visualizzati come elementi in un elenco all'interno di ogni album. Music dispone anche di un MusicHasArtists di incorporamento alla classe Artist, le cui istanze vengono visualizzate anche come forme nel diagramma.

 Per impostazione predefinita, gli elementi incorporati vengono eliminati automaticamente quando vengono eliminati gli elementi padre.

 Quando un modello viene salvato in un file in formato XML, gli elementi incorporati sono annidati all'interno degli elementi padre, a meno che non sia stata personalizzata la serializzazione.

> [!NOTE]
> L'incorporamento è diverso dall'ereditarietà. Gli elementi figlio in una relazione di incorporamento non ereditano le proprietà dell'elemento padre. Un incorporamento è un tipo di collegamento tra gli elementi del modello. L'ereditarietà è una relazione tra le classi e non crea collegamenti tra gli elementi del modello.

### <a name="embedding-rules"></a>Incorporamento di regole
 Ogni elemento in un modello di istanza deve essere la destinazione di un solo collegamento di incorporamento, ad eccezione della radice del modello.

 Pertanto, ogni classe di dominio non astratta, ad eccezione della classe radice, deve essere la destinazione di almeno una relazione di incorporamento o deve ereditare un incorporamento da una classe base. Una classe può essere la destinazione di due o più incorporamenti, ma gli elementi del modello di istanza possono avere un solo elemento padre alla volta. La molteplicità da target a source deve essere 0.. 1 o 1.. 1.

### <a name="the-explorer-displays-the-embedding-tree"></a>La finestra di esplorazione Visualizza l'albero di incorporamento
 La definizione DSL crea anche un visualizzatore, che gli utenti vedono insieme al diagramma del modello.

 ![Finestra di esplorazione generata di DSL](../modeling/media/music_explorer.png)

 La finestra di esplorazione Mostra tutti gli elementi del modello, anche quelli per i quali non sono state definite forme. Mostra gli elementi e le relazioni di incorporamento, ma non le relazioni di riferimento.

 Per visualizzare i valori delle proprietà di dominio di un elemento, l'utente seleziona un elemento nel diagramma del modello o in Esplora modelli e apre il Finestra Proprietà. Vengono visualizzate tutte le proprietà del dominio, incluse quelle che non vengono visualizzate nel diagramma. Nell'esempio, ogni brano ha un titolo e un genere, ma nel diagramma viene visualizzato solo il valore del titolo.

## <a name="reference-relationships"></a>Relazioni di riferimento
 Una relazione di riferimento rappresenta qualsiasi tipo di relazione non incorporata.

 Le relazioni di riferimento vengono in genere visualizzate in un diagramma come connettori tra le forme.

 Nella rappresentazione XML del modello, un collegamento di riferimento tra due elementi viene rappresentato utilizzando i *moniker.* Ovvero, i moniker sono nomi che identificano in modo univoco ogni elemento del modello. Il nodo XML per ogni elemento del modello contiene un nodo che specifica il nome della relazione e il moniker dell'altro elemento.

## <a name="roles"></a>Ruoli
 Ogni relazione di dominio ha due ruoli, un ruolo di origine e un ruolo di destinazione.

 Nell'immagine seguente la riga tra la classe di dominio del **server di pubblicazione** e la relazione di dominio **PublisherCatalog** è il ruolo di origine. La riga tra la relazione di dominio e la classe di dominio **album** è il ruolo di destinazione.

 ![Ruoli e proprietà.](../modeling/media/propertycode.png)

 I nomi associati a una relazione sono particolarmente importanti quando si scrive codice programma che attraversa il modello. Ad esempio, quando si compila la soluzione DSL, il server di pubblicazione della classe generata dispone di un catalogo di proprietà costituito da una raccolta di album. L'album della classe dispone di un server di pubblicazione di proprietà che rappresenta una singola istanza del server di pubblicazione della classe.

 Quando si crea una relazione in una definizione DSL, al nome della proprietà e della relazione vengono assegnati i valori predefiniti. Tuttavia, è possibile modificarli.

## <a name="multiplicities"></a>Molteplicità
 Molteplicità specificare il numero di elementi che possono avere lo stesso ruolo in una relazione di dominio. Nell'esempio, l'impostazione di molteplicità zero-a-molti (0.. \*) nel ruolo del **Catalogo** specifica che qualsiasi istanza della classe di dominio del **server di pubblicazione** può avere tutti i collegamenti alla relazione di **PublisherCatalog** che si desidera assegnare.

 Configurare la molteplicità di un ruolo digitando nel diagramma o modificando la proprietà `Multiplicity` nella finestra **Proprietà** . Nella tabella seguente vengono descritte le impostazioni per questa proprietà.

|Tipo di molteplicità|Descrizione|
|-|-|
|0.. * (da zero a molti)|Ogni istanza della classe di dominio può avere più istanze della relazione o nessuna istanza della relazione.|
|0.. 1 (zero a uno)|Ogni istanza della classe di dominio non può avere più di un'istanza della relazione o nessuna istanza della relazione.|
|1.. 1 (uno)|Ogni istanza della classe di dominio può avere un'istanza della relazione. Non è possibile creare più di un'istanza di questa relazione da qualsiasi istanza della classe Role. Se la convalida è abilitata, viene visualizzato un errore di convalida quando un'istanza della classe role non dispone di un'istanza della relazione.|
|1.. * (da uno a molti)|Ogni istanza della classe nel ruolo che dispone di questa molteplicità può avere più istanze della relazione e ogni istanza deve avere almeno un'istanza della relazione. Se la convalida è abilitata, viene visualizzato un errore di convalida quando un'istanza della classe role non dispone di un'istanza della relazione.|

## <a name="domain-relationships-as-classes"></a>Relazioni di dominio come classi
 Un collegamento viene rappresentato nell'archivio come un'istanza di LinkElement, che è una classe derivata di ModelElement. È possibile definire queste proprietà nel diagramma del modello di dominio per le relazioni di dominio.

 È anche possibile creare una relazione con l'origine o la destinazione di altre relazioni. Nel diagramma del modello di dominio fare clic con il pulsante destro del mouse sulla relazione di dominio, quindi scegliere **Mostra come classe**. Verrà visualizzata una finestra di classe aggiuntiva. È quindi possibile connettere le relazioni.

 È possibile definire una relazione parzialmente in base all'ereditarietà, così come è possibile con le classi di dominio. Selezionare la relazione derivata e impostare la **relazione di base** nel finestra Proprietà.

 Una relazione derivata specializza la relazione di base. Le classi di dominio da cui viene collegato devono essere derivate da o dalle stesse classi collegate dalla relazione di base. Quando viene creato un collegamento della relazione derivata in un modello, è un'istanza di entrambe le relazioni derivate e di base. Nel codice programma è possibile passare all'estremità opposta del collegamento usando le proprietà generate dalla base o dalla classe derivata.

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
