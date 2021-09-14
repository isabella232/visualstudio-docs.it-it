---
title: File DslDefinition.dsl
description: Informazioni sulla struttura del file DslDefinition.dsl nel progetto Dsl di una soluzione strumenti DSL, che definisce un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c31d6b6b5cc1c1542c27b15af4e6ee741272c3d8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637323"
---
# <a name="the-dsldefinitiondsl-file"></a>File DslDefinition.dsl

Questo argomento descrive la struttura del file DslDefinition.dsl nel progetto Dsl di una soluzione, che definisce un linguaggio [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] *specifico di dominio.* Il file DslDefinition.dsl descrive le classi e le relazioni di un linguaggio specifico di dominio, insieme al diagramma, alle forme, ai connettori, al formato di serializzazione e alla casella degli strumenti del linguaggio specifico di dominio e dei relativi strumenti di modifica.  In una soluzione di linguaggio specifico di dominio, il codice che definisce tali strumenti viene generato in base alle informazioni presenti nel file DslDefinition.dsl.

In genere, si usa *Finestra di progettazione Domain-Specific Language* per modificare il file DslDefinition.dsl. Poiché il formato del file DslDefinition.dsl non elaborato è XML, è possibile aprirlo in un editor XML. Può risultare utile comprendere quali informazioni sono contenute nel file e come sono organizzate per eseguire il debug ed estendere le funzionalità.

Gli esempi riportati in questo argomento provengono dal modello di soluzione Diagramma componente. Per un esempio, creare una soluzione di linguaggio specifico di dominio basata sul modello di soluzione Modelli componente. Dopo aver creato la soluzione, il file DslDefinition.dsl è presente nella finestra di progettazione del linguaggio specifico di dominio. Chiudere il file, fare clic con il pulsante destro del mouse **Esplora soluzioni,** scegliere Apri con **,** fare clic su **Editor XML** e quindi su **OK.**

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sezioni del file DslDefinition.dsl

L'elemento radice è e i relativi attributi identificano il nome del linguaggio specifico di dominio, lo spazio dei nomi e i numeri di versione principale e secondaria per \<Dsl> il controllo delle versioni. Lo schema `DslDefinitionModel` definisce il contenuto e la struttura di un file DslDefinition.dsl valido.

Gli elementi figlio \<Dsl> dell'elemento radice sono i seguenti:

### <a name="classes"></a>Classi

Questa sezione definisce ogni classe di dominio che genera una classe nel codice generato.

### <a name="relationships"></a>Relazioni

Questa sezione definisce le relazioni incluse nel modello. L'origine e la destinazione rappresentano le due parti della relazione.

### <a name="types"></a>Tipi

Questa sezione definisce i tipi ed elenca i relativi spazi dei nomi. Le proprietà di dominio sono di due tipi. `DomainEnumerations` sono definiti nel modello e generano tipi in DomainModel.cs. `ExternalTypes` fare riferimento ai tipi definiti altrove (ad esempio `String` o ) e non `Int32` generano alcun elemento.

### <a name="shapes"></a>Forme

Questa sezione definisce le forme che descrivono l'aspetto del modello in una finestra di progettazione. Queste forme geometriche sono mappate alle classi del modello nella sezione Diagram.

### <a name="connectors"></a>Connettori

Questa sezione definisce l'aspetto dei connettori presenti in una finestra di progettazione. Queste descrizioni degli stili geometrici sono mappate a relazioni specifiche del modello nella sezione Diagram.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Questa sezione definisce uno schema di serializzazione e include altre informazioni sul salvataggio di ciascuna classe in un file.

### <a name="explorerbehavior"></a>ExplorerBehavior

Questa sezione definisce come viene visualizzata **la finestra DSL Explorer** quando l'utente modifica un modello.

### <a name="connectionbuilders"></a>ConnectionBuilders

Questa sezione definisce un generatore di connessione per ogni connettore (lo strumento per creare collegamenti tra classi che possono essere connesse). Questa sezione determina se è possibile connettere una classe di origine e una di destinazione.

### <a name="diagram"></a>Diagramma

Questa sezione definisce un diagramma e viene usata per specificare proprietà come il colore di sfondo e la classe radice La classe radice è la classe di dominio rappresentata dal diagramma nel suo complesso. La sezione Diagramma contiene anche gli elementi ShapeMap e ConnectorMap, che specificano la forma o il connettore che rappresenta ogni classe di dominio o relazione.

### <a name="designer"></a>Designer

In questa sezione viene definita una finestra di progettazione (editor), che riunisce una casella **degli** strumenti, le impostazioni di convalida, un diagramma e uno schema di serializzazione. La sezione Designer definisce anche la classe radice del modello, che di solito corrisponde alla classe radice del diagramma.

### <a name="explorer"></a>Explorer

Questa sezione identifica il **comportamento di Esplora DSL** (definito nella sezione XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Moniker nel file DslDefinition.dsl

Nel file DslDefinition.dsl è possibile usare moniker per impostare riferimenti incrociati a elementi specifici. Ogni definizione di relazione contiene ad esempio una sottosezione Source e una Target. Ogni sottosezione contiene il moniker della classe di oggetto che può essere collegata con tale relazione:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

In genere, lo spazio dei nomi dell'elemento a cui viene fatto riferimento (in questo esempio la classe di dominio `Library`) corrisponde a quello dell'elemento contenente il riferimento (in questo caso la relazione di dominio LibraryHasMembers). In questo caso il moniker deve fornire solo il nome della classe. Altrimenti è necessario usare la forma completa /SpazioDeiNomi/Nome:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Il sistema dei moniker richiede elementi di pari livello con nomi distinti nell'albero XML. Per questo motivo, se si tenta di salvare una definizione di linguaggio specifico di dominio che ha ad esempio due classi con lo stesso nome, si verificano errori di convalida. È sempre necessario correggere gli errori di nome duplicato prima di salvare il file DslDefinition.dsl per poterlo ricaricare senza errori in seguito.

Ogni tipo ha un moniker specifico: DomainClassMoniker, DomainRelationshipMoniker e così via.

## <a name="types"></a>Tipi

La sezione Types specifica tutti i tipi inclusi nel file DslDefinition.dsl come tipi di proprietà. Si tratta di due categorie di tipi: i tipi esterni, come System.String, e i tipi enumerati.

### <a name="external-types"></a>Tipi esterni

Nell'esempio Diagramma dei componenti è elencato un set di tipi primitivi standard, anche se solo alcuni sono usati.

Ogni definizione di tipo esterno include semplicemente un nome e uno spazio dei nomi, ad esempio String e System:

```xml
<ExternalType Name="String" Namespace="System" />
```

Si usano i nomi completi dei tipi invece delle parole chiave del compilatore equivalenti come "string".

I tipi esterni non sono limitati ai tipi delle librerie standard.

### <a name="enumerations"></a>Enumerazioni

Una specifica di enumerazione tipica è simile a questo esempio:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

L'attributo `IsFlags` controlla se il codice generato è preceduto dall'attributo CLR (Common Language Runtime) `[Flags]`, che determina se i valori dell'enumerazione possono essere combinati bit per bit. Se questo attributo è impostato su True, occorre specificare potenze di due per i valori letterali.

## <a name="classes"></a>Classi

Gran parte degli elementi di una definizione di linguaggio specifico di dominio sono istanze dirette o indirette di `DomainClass`. Le sottoclassi di `DomainClass` includono `DomainRelationship`, `Shape`, `Connector` e `Diagram`. La sezione `Classes` del file DslDefinition.dsl elenca le classi di dominio.

Ogni classe ha un set di proprietà e può avere una classe base. Nell'esempio Diagramma dei componenti, `NamedElement` è una classe astratta con una proprietà `Name`, il cui tipo è String:

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` è la base di molte delle altre classi, ad esempio , che ha proprietà proprie oltre alla proprietà `Component` `Name` ereditata da `NamedElement` . Il nodo figlio BaseClass contiene un riferimento a un moniker. Poiché la classe di riferimento si trova nello stesso spazio dei nomi, nel moniker è necessario solo il suo nome:

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Ogni classe di dominio, incluse le relazioni, le forme, i connettori e i diagrammi, può avere questi attributi e nodi figlio:

- **ID.** Questo attributo è un GUID. Se non si specifica un valore nel file, la finestra di progettazione del linguaggio specifico di dominio crea un valore (nelle figure di questo documento, questo attributo è in genere omesso per questioni di spazio).

- **Name e Namespace.**  Questi attributi specificano il nome e lo spazio dei nomi della classe nel codice generato. Entrambi devono essere be univoci nel linguaggio specifico di dominio.

- **InheritanceModifier.** Questo attributo è "abstract", "sealed" o non specificato.

- **Displayname.** Questo attributo è il nome visualizzato nella **finestra** Proprietà. L'attributo DisplayName può contenere spazi e altri segni di punteggiatura.

- **GeneratesDoubleDerived.**  Se questo attributo è impostato su True, vengono generate due classi, di cui una è una sottoclasse dell'altra. Tutti i metodi generati si trovano nella classe base e i costruttori nella sottoclasse. Impostando questo attributo, è possibile eseguire l'override di qualsiasi metodo generato nel codice personalizzato.

- **HasCustomConstructor**. Se questo attributo è impostato su True, il costruttore viene omesso dal codice generato per poter scrivere una versione personalizzata.

- **Attributi**. Questo attributo contiene gli attributi CLR della classe generata.

- **BaseClass**. Se si specifica una classe base, deve essere dello stesso tipo. Una classe di dominio, ad esempio, deve avere un'altra classe di dominio come classe base, mentre una forma Raggruppamento deve avere una forma Raggruppamento. Se non si specifica una classe base, la classe nel codice generato deriva da una classe del framework standard. Una classe di dominio ad esempio deriva da `ModelElement`.

- **Proprietà**. Questo attributo contiene le proprietà mantenute sotto il controllo della transazione e salvate in modo permanente quando il modello viene salvato.

- **ElementMergeDirectives**. Ogni direttiva di unione degli elementi controlla come un'istanza diversa di un'altra classe viene aggiunta a un'istanza della classe padre. Per informazioni più dettagliate sulle direttive di merge degli elementi, vedere più avanti in questo argomento.

- Per ogni classe di dominio elencata nella sezione `Classes` viene generata una classe C#. Le classi C# sono generate in Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Proprietà

Ogni proprietà di dominio ha un nome e un tipo. Il nome deve essere univoco all'interno della classe di dominio e delle relative classi base transitive.

Il tipo deve fare riferimento a uno dei tipi elencati nella sezione `Types`. In genere, il moniker deve includere lo spazio dei nomi.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Ogni proprietà di dominio può anche avere i seguenti attributi:

- **IsBrowsable**. Questo attributo determina se la proprietà viene visualizzata nella **finestra Proprietà** quando l'utente fa clic su un oggetto della classe padre.

- **IsUIReadOnly**. Questo attributo determina se l'utente  può modificare la proprietà nella finestra Proprietà o tramite un elemento Decorator in cui viene visualizzata la proprietà.

- **Tipo**. È possibile impostare questo attributo su Normal, Calculated o CustomStorage. Se si imposta su Calculated, è necessario specificare codice personalizzato che determina il valore. La proprietà sarà di sola lettura. Se si imposta su CustomStorage, è necessario specificare codice che recupera e imposta i valori.

- **IsElementName**. Se questo attributo è impostato su True, il suo valore viene impostato automaticamente su un valore univoco quando viene creata un'istanza della classe padre. Questo attributo può essere impostato su True solo per una proprietà in ogni classe, che deve essere di tipo String. Nell'esempio Diagramma dei componenti, la proprietà `Name` in `NamedElement` ha `IsElementName` impostato su True. Quando un utente crea un elemento `Component` (che eredita da `NamedElement`), il nome viene inizializzato automaticamente con un valore simile a "Component6".

- `DefaultValue`. Se questo attributo è stato specificato, il valore indicato viene assegnato all'attributo per le nuove istanze di questa classe. Se `IsElementName` è impostato, l'attributo DefaultValue specifica la parte iniziale della nuova stringa.

- **Category** è l'intestazione in cui la proprietà verrà visualizzata nella **finestra** Proprietà.

## <a name="relationships"></a>Relazioni

La sezione `Relationships` contiene un elenco di tutte le relazioni del linguaggio specifico di dominio. Ogni elemento `Domain Relationship` è binario e diretto e collega i membri di una classe di origine ai membri della classe di destinazione. Le classi di origine e destinazione sono in genere classi di dominio, ma sono ammesse anche le relazioni con altre relazioni.

La relazione Connection collega ad esempio i membri della classe OutPort a quelli della classe InPort. Ogni istanza di collegamento della relazione collega un'istanza di OutPort a un'istanza di InPort. Poiché si tratta di una relazione molti a molti, ogni oggetto OutPort può avere molti collegamenti Connection con le relative origini e ogni istanza di InPort può avere più collegamenti Connection con tale oggetto come destinazione.

### <a name="source-and-target-roles"></a>Ruoli di origine e di destinazione

Ogni relazione contiene ruoli di origine e di destinazione con i seguenti attributi:

- L'attributo `RolePlayer` fa riferimento alla classe di dominio delle istanze collegate: OutPort per l'origine e InPort per la destinazione.

- L'attributo `Multiplicity` ha quattro valori possibili: ZeroMany, ZeroOne, One e OneMany. Questo attributo fa riferimento al numero di collegamenti di questa relazione che possono essere associati a un assegnatario di ruolo.

- L'attributo `PropertyName` specifica il nome usato nella classe assegnataria del ruolo per accedere agli oggetti dell'altra parte della relazione. Questo nome viene usato nel modello o nel codice personalizzato per attraversare la relazione. L'attributo `PropertyName` del ruolo di origine, ad esempio, è impostato su `Targets`. Quindi il codice seguente è valido:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Per convenzione, i nomi di proprietà sono plurali se la molteplicità è ZeroMany o OneMany.

     La molteplicità di un ruolo si riferisce alla quantità di ruoli opposti che è possibile associare a ogni istanza del ruolo. Nella relazione ComponentHasPorts, ad esempio, il ruolo di destinazione ha l'attributo `RolePlayer` impostato su Port, l'attributo `PropertyName` impostato su Component e l'attributo `Multiplicity` impostato su ZeroOne. Quindi, il codice appropriato per usare il ruolo è:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- L'attributo `Name` del ruolo indica il nome usato all'interno della classe Relationship per fare riferimento a tale parte di un collegamento. Per convenzione, un nome di ruolo è sempre singolare, perché ogni collegamento ha una sola istanza per ogni parte. Il codice seguente funziona:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Per impostazione predefinita, l'attributo `IsPropertyGenerator` è impostato su True. Se viene impostato su False, non viene creata alcuna proprietà per la classe Role Player (in tal caso, ad esempio `op.Targets` non funziona). È comunque possibile usare codice personalizzato per attraversare la relazione o ottenere l'accesso ai collegamenti stessi se il codice personalizzato usa la relazione in modo esplicito:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Attributi delle relazioni

Oltre agli attributi e ai nodi figlio disponibili per tutte le classi, ogni relazione ha i seguenti attributi:

- **IsEmbedding**. Questo attributo booleano specifica se la relazione fa parte dell'albero di incorporamento. Ogni modello deve formare un albero con le relative relazioni di incorporamento. Ogni classe di dominio deve quindi essere la destinazione di almeno una relazione di incorporamento, a meno che non sia la radice di un modello.

- **AllowsDuplicates**. Questo attributo booleano, impostato su False per impostazione predefinita, si applica solo alle relazioni con una molteplicità "molti" sia come origine che come destinazione. Determina se gli utenti del linguaggio possono connettere una coppia di elementi di origine e destinazione con più collegamenti della stessa relazione.

## <a name="designer-and-toolbox-tabs"></a>Schede Finestra di progettazione e Casella degli strumenti

La parte principale della **sezione Progettazione** del file DslDefinition.dsl sono gli **elementi ToolboxTab.** Una finestra di progettazione può avere diversi di questi elementi, ognuno dei quali rappresenta una sezione intestazione nella casella degli strumenti della finestra di progettazione **generata.** Ogni **elemento ToolboxTab** può contenere uno o più **elementi ElementTool,** **elementi ConnectionTool** o entrambi.

Gli elementi ElementTool possono creare istanze di una classe di dominio specifica. Quando l'utente trascina un ElementTool nel diagramma, il risultato è determinato dalle direttive di merge degli elementi come descritto nella sezione relativa alle direttive di merge degli elementi più avanti in questo argomento.

Ogni strumento di connessione può richiamare un generatore di connessione specifico. Un generatore di connessione può creare più tipi di relazione, a seconda del punto in cui l'utente fa clic con il mouse, come descritto nella sezione relativa ai generatori di connessioni.

Nessuno dei due tipi di strumento costruisce direttamente forme o connettori. Ognuno crea un'istanza di una classe di dominio o di una relazione di dominio. I mapping di Shape e Connector determinano quindi l'aspetto della classe o della relazione di dominio.

## <a name="paths"></a>Percorsi

I percorsi di dominio si trovano in varie posizioni all'interno del file DslDefinition.dsl. Questi percorsi specificano una serie di collegamenti da un elemento di un modello, cioè un'istanza del linguaggio specifico di dominio, a un altro. La sintassi dei percorsi è semplice ma dettagliata.

I percorsi si trovano nel file DslDefinition.dsl tra tag `<DomainPath>...</DomainPath>`. I percorsi possono usare più collegamenti, ma in pratica la maggior parte degli esempi attraversa un solo collegamento.

Un percorso è costituito da una sequenza di segmenti. Ogni segmento è un hop sia da un oggetto a un collegamento che da un collegamento a un oggetto. Pertanto gli hop in genere si alternano in un percorso lungo. Il primo hop è da un oggetto a un collegamento, il secondo all'oggetto all'altra estremità del collegamento, il terzo al collegamento successivo e così via. L'eccezione occasionale a questa sequenza si ha nei punti in cui la relazione stessa è l'origine o la destinazione di un'altra relazione.

Ogni segmento inizia con un nome di relazione. In un hop da un oggetto a un collegamento, la relazione precede un punto seguito dal nome della proprietà: "`Relationship . Property`". In un hop da un collegamento a un oggetto, la relazione precede un punto esclamativo seguito dal nome del ruolo: "`Relationship ! Role`".

L'esempio Diagramma dei componenti contiene un percorso nell'elemento ParentElementPath di ShapeMap per InPort. Il percorso inizia come segue:

```
    ComponentHasPorts.Component
```

In questo esempio, InPort è una sottoclasse di ComponentPort e ha una relazione ComponentHasPorts. La proprietà è denominata Component.

Quando si scrive codice C# per questo modello, è possibile attraversare un collegamento in un unico passaggio tramite la proprietà che la relazione genera su ciascuna delle classi che collega:

```
     InPort port; ...  Component c = port.Component;
```

È però necessario eseguire entrambi gli hop in modo esplicito nella sintassi del percorso. Questo requisito consente di accedere al collegamento intermedio più facilmente. Il codice seguente completa l'hop dal collegamento alla proprietà Component:

```
    ComponentHasPorts.Component / ! Component
```

È possibile omettere il nome della relazione quando corrisponde a quello del segmento precedente.

## <a name="element-merge-directives"></a>Direttive di merge degli elementi

Quando l'utente del linguaggio trascina un elemento dalla **casella** degli strumenti nel diagramma, viene costruita un'istanza della classe dello strumento. Vengono anche creati collegamenti tra l'istanza e gli elementi del modello esistenti. Alcuni elementi, ad esempio componenti o commenti, vengono creati quando  l'utente del linguaggio li trascina dalla casella degli strumenti in una parte vuota del diagramma. Altri elementi vengono creati quando l'utente del linguaggio li trascina su altri elementi host. Un elemento OutPort o InPort viene creato ad esempio quando l'utente del linguaggio lo trascina su un componente.

Una possibile classe host, come Component, accetta un nuovo elemento solo se la classe host include una direttiva di unione degli elementi per la classe del nuovo elemento. Il nodo DomainClass con Name="Component" contiene ad esempio:

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Il moniker della classe sotto il nodo Index fa riferimento alla classe di elementi che può essere accettata. In questo caso, ComponentPort è la classe base astratta di InPort e OutPort. Entrambi questi elementi possono quindi essere accettati.

ComponentModel, la classe radice del linguaggio, include direttive di merge degli elementi per i componenti e i commenti. L'utente del linguaggio può trascinare elementi di tali classi direttamente nel diagramma perché le parti vuote del diagramma rappresentano la classe radice. ComponentModel non ha però una direttiva di unione degli elementi per ComponentPort. L'utente del linguaggio non può quindi trascinare elementi InPort o OutPort direttamente nel diagramma.

La direttiva di unione degli elementi determina i collegamenti creati in modo che il nuovo elemento possa essere integrato o inserito nel modello esistente. Per un elemento ComponentPort viene creata un'istanza di ComponentHasPorts. DomainPath identifica sia la relazione che la proprietà della classe padre Ports, a cui il nuovo elemento verrà aggiunto.

È possibile creare più collegamenti a una direttiva di unione degli elementi includendo più percorsi di creazione dei collegamenti. Uno dei percorsi deve essere incorporato.

È possibile usare più segmenti in un percorso di creazione dei collegamenti. In questo caso, l'ultimo segmento definisce quale collegamento deve essere creato. I segmenti precedenti passano dalla classe padre all'oggetto da cui il nuovo collegamento deve essere creato.

È ad esempio possibile aggiungere questa direttiva di unione degli elementi alla classe Component:

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Gli utenti del linguaggio possono quindi trascinare un commento in un componente per creare automaticamente il commento con un collegamento al componente.

Il primo percorso di creazione del collegamento passa da `Component` a `ComponentModel` e crea un'istanza della relazione di incorporamento `ComponentModelHasComments`. Il secondo percorso di creazione del collegamento crea un collegamento alla relazione di riferimento CommentsReferenceComponents dal componente host al nuovo commento. Tutti i percorsi di creazione dei collegamenti devono iniziare con la classe host e terminare con un collegamento alla classe di cui è stata creata un'istanza.

## <a name="xmlclassdata"></a>XmlClassData

Ogni classe di dominio, incluse le relazioni e gli altri sottotipi, può includere informazioni aggiuntive in un nodo `XmlClassData`, presente nella sezione `XmlSerializationBehavior` del file DslDefinition.dsl. Queste informazioni riguardano in modo specifico come le istanze della classe vengono archiviate in formato serializzato quando un modello viene salvato in un file.

Gran parte del codice generato interessato da `XmlSerializationBehavior` si trova in `Dsl\GeneratedCode\Serializer.cs`.

Ogni nodo `XmlClassData` include i nodi e gli attributi figlio seguenti:

- Un nodo moniker, che fa riferimento alla classe a cui si applicano i dati.

- **XmlPropertyData** per ogni proprietà definita nella classe .

- **XmlRelationshipData** per ogni relazione di origine nella classe . (anche le relazioni hanno i propri nodi XmlClassData).

- **Attributo stringa TypeName,** che determina il nome della classe helper di serializzazione nel codice generato.

- **Stringa ElementName,** che determina il tag XML delle istanze serializzate di questa classe. Per convenzione, ElementName corrisponde in genere al nome della classe con l'iniziale minuscola. Ad esempio, un file modello inizia così:

    ```xml
    <componentModel ...
    ```

- **MonikerElementName nei** file di modello serializzati dell'utente. Questo attributo introduce un moniker che fa riferimento a questa classe.

- **MonikerAttributeName**, che identifica il nome dell'attributo XML all'interno di un moniker. In questo frammento del file serializzato di un utente, l'autore del linguaggio specifico di dominio ha definito **MonikerElementName** come "inPortMoniker" e **MonikerAttributeName** come "path":

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Per ogni strumento di connessione viene definito un generatore di connessione. Ogni generatore di connessione è costituito da uno o più elementi LinkConnectDirective, ciascuno dei quali contiene uno o più elementi SourceDirective e uno o più elementi TargetDirective. Dopo avere fatto clic su uno strumento di connessione, l'utente può iniziare una connessione da qualsiasi forma mappata a un elemento del modello presente nell'elenco di elementi SourceDirective. La connessione può quindi essere completata su una forma mappata a un elemento presente nell'elenco di elementi TargetDirective. La classe di relazione di cui viene creata un'istanza dipende dall'elemento LinkConnectDirective designato dall'elemento da cui è partita la connessione.

### <a name="xmlpropertydata"></a>XmlPropertyData

Un **attributo DomainPropertyMoniker** identifica la proprietà a cui fanno riferimento i dati. Questo attributo deve essere una proprietà della classe ClassData contenitore.

**L'attributo XmlName** assegna il nome dell'attributo corrispondente come dovrebbe essere visualizzato nel codice XML. Per convenzione, questa stringa corrisponde al nome della proprietà con l'iniziale minuscola.

Per impostazione predefinita, **l'attributo Representation** è impostato su Attribute. Se **La rappresentazione** è impostata su Element, nel codice XML viene creato un nodo figlio. Se **La rappresentazione** è impostata su Ignora, la proprietà non viene serializzata.

Gli **attributi IsMonikerKey** e **IsMonikerQualifier** assegnano a una proprietà un ruolo nell'identificazione delle istanze della classe padre. È possibile impostare **IsMonikerKey** su true per una proprietà definita in o ereditata da una classe. Questo attributo identifica una singola istanza della classe padre. La proprietà impostata su `IsMonikerKey` è in genere un nome o un altro identificatore chiave. La proprietà di stringa `Name` è ad esempio la chiave moniker per NamedElement e le relative classi derivate. Quando l'utente salva un modello in un file, questo attributo deve contenere valori univoci per ogni istanza, tra i propri elementi di pari livello nell'albero delle relazioni di incorporamento.

Nel file modello serializzato, il moniker completo di un elemento è un percorso dalla radice del modello fino all'albero delle relazioni di incorporamento, con un riferimento alla chiave moniker in ogni punto. Gli elementi InPort, ad esempio, sono incorporati in elementi Component, che a loro volta sono incorporati nella radice del modello. Un moniker valido è il seguente:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

È possibile impostare **l'attributo IsMonikerQualifier** per una proprietà stringa e fornire un modo aggiuntivo per costruire il nome completo di un elemento. Ad esempio, nel file DslDefinition.dsl **Namespace** è un qualificatore moniker.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

In un file modello serializzato, i collegamenti, sia delle relazioni di incorporamento che di quelle di riferimento, sono rappresentati dai nodi figlio dell'origine della relazione. Per le relazioni di incorporamento, il nodo figlio contiene un sottoalbero. Per le relazioni di riferimento, il nodo figlio contiene un moniker che fa riferimento a un'altra parte dell'albero.

**L'attributo XmlRelationshipData** in **un attributo XmlClassData** definisce esattamente come vengono annidati i nodi figlio all'interno dell'elemento di origine. Ogni relazione che è un'origine nella classe di dominio ha un **attributo XmlRelationshipData.**

**L'attributo DomainRelationshipMoniker** identifica una delle relazioni di origine nella classe.

**L'attributo RoleElementName** fornisce il nome del tag XML che racchiude il nodo figlio nei dati serializzati.

Il file DslDefinition.dsl contiene ad esempio:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Quindi il file serializzato contiene:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Se **l'attributo UseFullForm** è impostato su true, viene introdotto un ulteriore livello di annidamento. Questo livello rappresenta la relazione stessa. L'attributo deve essere impostato su True se la relazione include proprietà.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Il file serializzato contiene:

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

La relazione di connessione include dati della classe XML propri che forniscono i nomi degli elementi e degli attributi della classe.

Se l'attributo **OmitElement** è impostato su true, il nome del ruolo relazione viene omesso, che abbrevia il file serializzato e non è ambiguo se le due classi non hanno più di una relazione. Ad esempio:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializzazione di una definizione di linguaggio specifico di dominio

Il file DslDefinition.dsl è un file serializzato e risulta conforme a una definizione del linguaggio specifico di dominio. Di seguito sono riportati alcuni esempi di definizioni di serializzazione XML:

- **Dsl** è il nodo RootClass e la classe del diagramma. DomainClass, DomainRelationship e altri elementi sono incorporati in `Dsl`.

- **Classes** è **roleElementName della** relazione tra Domain-Specific Language e DomainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- **L'attributo XmlSerializationBehavior** è incorporato nell'attributo , ma l'attributo `Dsl` **OmitElement** è stato impostato nella relazione di incorporamento. Quindi, nessun attributo `RoleElementName` interviene. Al contrario, un **attributo ClassData** è l'attributo della relazione di incorporamento tra un `RoleElementName` attributo **XmlSerializationBehavior** e **un attributo XmlClassData.**

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators è la relazione di incorporamento tra `Connector` e `Decorator`. `UseFullForm` è stato impostato in modo che il nome della relazione venga visualizzato con il relativo elenco di proprietà per ogni collegamento dall'oggetto Connector. `OmitElement` è però anche stato impostato in modo che nessun elemento `RoleElementName` includa i vari collegamenti incorporati in `Connector`:

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Forme e connettori

Le definizioni delle forme e dei connettori ereditano gli attributi e i nodi figlio dalle classi di dominio, oltre ai seguenti elementi:

- Attributi `Color` e `Line``Style`.

- **EsponeFillColorAsProperty e** diversi attributi simili. Questi attributi booleani rendono la proprietà corrispondente modificabile dall'utente. In genere, quando un utente del linguaggio fa clic  su una forma nel diagramma, le proprietà visualizzate nella finestra Proprietà sono quelle dell'istanza della classe di dominio a cui è mappata la forma. Se `ExposesFillColorAsProperty` è impostato su True, viene visualizzata anche una proprietà della forma stessa.

- **ShapeHasDecorators**. È presente un'istanza di questo attributo per ogni elemento Decorator di testo, icona o espansione o compressione. Nel file DslDefinition.dsl, `ShapeHasDecorators` è una relazione con `UseFullForm` impostato su True.

## <a name="shape-maps"></a>Mappe delle forme

Le mappe delle forme determinano come le istanze di una determinata classe di dominio vengono visualizzate sullo schermo, rappresentate da una forma. Le mappe delle forme e dei connettori si trovano nella sezione `Diagram` del file DslDefinition.dsl.

Come illustrato nel seguente esempio, gli elementi `ShapeMap` hanno almeno il moniker di una classe di dominio, il moniker di una forma e un elemento `ParentElementPath`:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

La funzione principale dell'elemento `ParentElementPath` è fare in modo che la stessa classe di oggetti possa essere visualizzata come una forma diversa in contesti diversi. Se ad esempio un elemento `InPort` può anche essere incorporato in un commento, l'elemento `InPort` può essere rappresentato con una forma diversa in tale contesto.

In secondo luogo, il percorso determina la relazione tra la forma e la propria forma padre. Nessuna struttura di incorporamento è definita tra le forme in un file DslDefinition.dsl. È necessario dedurre la struttura dalle mappe delle forme. La forma padre di una forma è la forma mappata all'elemento del dominio identificato dal percorso dell'elemento padre. In questo caso, il percorso identifica il componente a cui appartiene `InPort`. In un'altra mappa delle forme, la classe Component è mappata a ComponentShape. La nuova forma `InPort` è quindi una forma figlio dell'elemento `ComponentShape` del relativo componente.

Se la forma InPort viene invece associata al diagramma, il percorso dell'elemento padre dovrebbe eseguire un altro passaggio al modello del componente, che è mappato al diagramma:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

La radice del modello non ha una mappa delle forme. Alla radice viene invece fatto riferimento direttamente dal diagramma, che include un elemento `Class`:

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Mappe degli elementi Decorator

Una mappa degli elementi Decorator associa una proprietà nella classe mappata a un elemento Decorator nella forma. Se la proprietà è un tipo enumerato o booleano, il relativo valore può determinare se l'elemento Decorator è visibile. Se l'elemento Decorator è di testo, il valore della proprietà può essere visualizzato e l'utente può modificarlo.

### <a name="compartment-shape-maps"></a>Mappe delle forme raggruppamento

Le mappe delle forme raggruppamento sono sottotipi di mappe delle forme.

## <a name="connector-maps"></a>Mappe dei connettori

La mappa dei connettori minima fa riferimento a un connettore e a una relazione:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Le mappe dei connettori possono anche contenere mappe degli elementi Decorator.

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)