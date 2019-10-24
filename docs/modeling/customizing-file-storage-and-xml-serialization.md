---
title: Personalizzazione dell'archiviazione dei file e della serializzazione XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27d8672ea94cf2a1547904f313ac36509f111462
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748452"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personalizzare l'archiviazione dei file e la serializzazione XML

Quando l'utente salva un'istanza o un *modello*di un linguaggio specifico di dominio (DSL) in Visual Studio, viene creato o aggiornato un file XML. Il file può essere ricaricato per ricreare il modello nell'archivio.

È possibile personalizzare lo schema di serializzazione modificando le impostazioni in **comportamento di serializzazione XML** in Esplora DSL. È disponibile un nodo in **comportamento di serializzazione XML** per ogni classe di dominio, proprietà e relazione. Le relazioni si trovano sotto le classi di origine. Sono inoltre presenti nodi corrispondenti alle classi di forma, connettore e diagramma.

È anche possibile scrivere codice programma per una personalizzazione più avanzata.

> [!NOTE]
> Se si desidera salvare il modello in un particolare formato, ma non è necessario ricaricarlo da tale modulo, provare a utilizzare i modelli di testo per generare l'output dal modello, anziché uno schema di serializzazione personalizzato. Per ulteriori informazioni, vedere [generazione di codice da un Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>File di modello e diagrammi

Ogni modello viene in genere salvato in due file:

- Il file del modello ha un nome, ad esempio **Model1. mydsl**. Archivia gli elementi del modello e le relazioni e le relative proprietà. L'estensione di file, ad esempio **. mydsl** , è determinata dalla proprietà **FileExtension** del nodo **Editor** nella definizione DSL.

- Il file di diagramma ha un nome, ad esempio **Model1. mydsl. Diagram**. Archivia le forme, i connettori e le relative posizioni, colori, spessori di linea e altri dettagli dell'aspetto del diagramma. Se l'utente elimina un file con **estensione Diagram** , le informazioni essenziali nel modello non vengono perse. Viene perso solo il layout del diagramma. Quando si apre il file del modello, viene creato un set predefinito di forme e di connettori.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Per modificare l'estensione di file di un linguaggio DSL

1. Aprire la definizione DSL. In DSL Explorer fare clic sul nodo Editor.

2. Nella Finestra Proprietà modificare la proprietà **FileExtension** . Non includere il "." iniziale dell'estensione del nome file.

3. In Esplora soluzioni modificare il nome dei due file modello di elemento in **DslPackage\ProjectItemTemplates**. Questi file hanno nomi che seguono il formato seguente:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Schema di serializzazione predefinito

Per creare un esempio per questo argomento, è stata usata la definizione DSL seguente.

![Modello di albero &#45; genealogico del diagramma di definizione DSL](../modeling/media/familyt_person.png)

Questo DSL è stato usato per creare un modello con il seguente aspetto sullo schermo.

![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

Questo modello è stato salvato e quindi riaperto nell'editor di testo XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Si notino i seguenti punti relativi al modello serializzato:

- Ogni nodo XML ha un nome uguale al nome di una classe di dominio, ad eccezione del fatto che la lettera iniziale è minuscola. Ad esempio, `familyTreeModel` e `person`.

- Le proprietà del dominio, ad esempio Name e BirthYear, vengono serializzate come attributi nei nodi XML. Anche in questo caso, il carattere iniziale del nome della proprietà viene convertito in lettere minuscole.

- Ogni relazione viene serializzata come nodo XML annidato all'interno dell'entità finale di origine della relazione. Il nodo ha lo stesso nome della proprietà del ruolo di origine, ma con un carattere iniziale minuscolo.

     Nella definizione DSL, ad esempio, un ruolo denominato **people** viene originato dalla classe **FamilyTree** .  Nel codice XML, è rappresentato dal nodo denominato `people` annidato all'interno del nodo `familyTreeModel`.

- L'estremità di destinazione di ogni relazione di incorporamento viene serializzata come nodo annidato sotto la relazione. Ad esempio, il nodo `people` contiene diversi nodi di `person`.

- L'estremità di destinazione di ogni relazione di riferimento viene serializzata come *moniker*, che codifica un riferimento all'elemento di destinazione.

     Ad esempio, in un nodo `person` è possibile che esista una relazione di `children`. Questo nodo contiene moniker come:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Informazioni sui moniker

I moniker vengono utilizzati per rappresentare riferimenti incrociati tra parti diverse dei file di modello e di diagramma. Vengono inoltre utilizzati nel file di `.diagram` per fare riferimento ai nodi nel file di modello. Esistono due forme di moniker:

- I *moniker ID* citano il GUID dell'elemento di destinazione. Esempio:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- I *moniker di chiave qualificati* identificano l'elemento di destinazione in base al valore di una proprietà di dominio designata denominata chiave del moniker. Il moniker dell'elemento di destinazione è preceduto dal moniker del relativo elemento padre nell'albero delle relazioni di incorporamento.

     Gli esempi seguenti sono tratti da un linguaggio DSL in cui è presente una classe di dominio denominata album, che ha una relazione di incorporamento con una classe di dominio denominata Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     I moniker di chiave qualificati verranno usati se la classe di destinazione ha una proprietà di dominio per la quale l'opzione **è la chiave del moniker** è impostata su `true` nel comportamento di **serializzazione XML**. Nell'esempio, questa opzione è impostata per le proprietà del dominio denominate "title" nelle classi di dominio "album" e "Song".

I moniker di chiave qualificati sono più facili da leggere rispetto ai moniker ID. Se si desidera che il codice XML dei file del modello venga letto dagli utenti, è consigliabile utilizzare moniker di chiave qualificati. Tuttavia, è possibile che l'utente imposti più di un elemento con la stessa chiave del moniker. Le chiavi duplicate potrebbero causare il ricaricamento non corretto del file. Se pertanto si definisce una classe di dominio a cui si fa riferimento usando moniker di chiave qualificati, è consigliabile prendere in considerazione modi per impedire all'utente di salvare un file con moniker duplicati.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Per impostare una classe di dominio a cui fare riferimento i moniker ID

1. Assicurarsi che la **chiave del moniker** sia `false` per ogni proprietà di dominio nella classe e nelle relative classi di base.

    1. In DSL Explorer espandere **XML Serialization comportamento \Class data \\ \<the classe di dominio > i dati \Element**.

    2. Verificare che la **chiave del moniker** sia `false` per ogni proprietà di dominio.

    3. Se la classe di dominio dispone di una classe di base, ripetere la procedura in tale classe.

2. Impostare l' **ID di serializzazione**  =  `true` per la classe di dominio.

     Questa proprietà è disponibile in **comportamento di serializzazione XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Per impostare una classe di dominio a cui fare riferimento da moniker di chiave qualificati

- Set **è la chiave del moniker** per una proprietà di dominio di una classe di dominio esistente. Il tipo della proprietà deve essere `string`.

    1. In DSL Explorer espandere **XML Serialization comportamento \Class data \\ \<the classe di dominio > dati \Element**, quindi selezionare la proprietà di dominio.

    2. Nel Finestra Proprietà impostare **è la chiave del moniker** su `true`.

- \- oppure -

     Creare una nuova classe di dominio usando lo strumento **classe di dominio denominato** .

     Questo strumento crea una nuova classe con una proprietà di dominio denominata Name. Il **nome dell'elemento è** e le proprietà della **chiave del moniker** di questa proprietà di dominio vengono inizializzate per `true`.

- \- oppure -

     Creare una relazione di ereditarietà dalla classe di dominio a un'altra classe che dispone di una proprietà della chiave del moniker.

### <a name="avoid-duplicate-monikers"></a>Evitare moniker duplicati

Se si usano moniker di chiave qualificati, è possibile che due elementi nel modello di un utente abbiano lo stesso valore nella proprietà chiave. Ad esempio, se il linguaggio DSL ha una classe Person con un nome di proprietà, l'utente potrebbe impostare i nomi di due elementi in modo che siano uguali. Sebbene il modello possa essere salvato in un file, non verrà ricaricato correttamente.

Sono disponibili diversi metodi che consentono di evitare questa situazione:

- Set **è il nome dell'elemento**  =  `true` per la proprietà del dominio chiave. Selezionare la proprietà di dominio nel diagramma di definizione DSL, quindi impostare il valore nell'Finestra Proprietà.

     Quando l'utente crea una nuova istanza della classe, questo valore determina l'assegnazione automatica di un valore diverso alla proprietà del dominio. Il comportamento predefinito aggiunge un numero alla fine del nome della classe. Ciò non impedisce all'utente di modificare il nome in un duplicato, ma è utile nel caso in cui l'utente non imposti il valore prima di salvare il modello.

- Abilitare la convalida per il linguaggio DSL. In DSL Explorer selezionare editor \Validation e impostare le proprietà **usi...** su `true`.

     Viene generato automaticamente un metodo di convalida che controlla le ambiguità. Il metodo si trova nella categoria `Load` convalida. In questo modo si garantisce che l'utente venga avvisato che potrebbe non essere possibile riaprire il file.

     Per ulteriori informazioni, vedere [convalida in un Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Percorsi e qualificatori del moniker

Un moniker di chiave qualificato termina con la chiave del moniker ed è preceduto dal moniker dell'elemento padre nell'albero di incorporamento. Ad esempio, se il moniker di un album è:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Uno dei brani di questo album potrebbe essere:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Tuttavia, se invece l'ID fa riferimento agli album, i moniker saranno i seguenti:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Si noti che poiché un GUID è univoco, non viene mai preceduto dal moniker del padre.

Se si è certi che una particolare proprietà del dominio avrà sempre un valore univoco all'interno di un modello, è possibile impostare il **qualificatore del moniker** su `true` per tale proprietà. Questa operazione ne determinerà l'utilizzo come qualificatore senza utilizzare il moniker dell'elemento padre. Se, ad esempio, si imposta sia il **qualificatore del moniker** sia la **chiave del moniker** per la proprietà del dominio del titolo della classe album, il nome o l'identificatore del modello non viene utilizzato nei moniker per l'album e i relativi elementi figlio incorporati:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personalizzare la struttura del codice XML

Per apportare le seguenti personalizzazioni, espandere il nodo **comportamento di serializzazione XML** in Esplora DSL. In una classe di dominio espandere il nodo dati elemento per visualizzare l'elenco delle proprietà e delle relazioni originate in questa classe. Selezionare una relazione e modificarne le opzioni nel Finestra Proprietà.

- Impostare **omette elemento** su true per omettere il nodo del ruolo di origine, lasciando solo l'elenco di elementi di destinazione. Non impostare questa opzione se è presente più di una relazione tra le classi di origine e di destinazione.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Impostare **Usa formato completo** per incorporare i nodi di destinazione nei nodi che rappresentano le istanze della relazione. Questa opzione viene impostata automaticamente quando si aggiungono le proprietà di dominio a una relazione di dominio.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

- Impostare la **rappresentazione**  = **elemento** in modo che una proprietà di dominio venga salvata come elemento anziché come valore di attributo.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Per modificare l'ordine in cui vengono serializzati gli attributi e le relazioni, fare clic con il pulsante destro del mouse su un elemento sotto dati elemento e utilizzare i comandi di menu **Sposta su** o **Sposta giù** .

## <a name="major-customization-using-program-code"></a>Personalizzazione principale mediante codice programma

È possibile sostituire parti o tutti gli algoritmi di serializzazione.

Si consiglia di studiare il codice in **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Per personalizzare la serializzazione di una classe specifica

1. Il set **è personalizzato** nel nodo per la classe in **comportamento di serializzazione XML**.

2. Trasformare tutti i modelli, compilare la soluzione ed esaminare gli errori di compilazione risultanti. I commenti vicini a ogni errore spiegano il codice che è necessario fornire.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Per fornire la propria serializzazione per l'intero modello

1. Metodi di override in Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opzioni nel comportamento di serializzazione XML

In DSL Explorer il nodo del comportamento di serializzazione XML contiene un nodo figlio per ogni classe di dominio, relazione, forma, connettore e classe del diagramma. In ognuno di questi nodi è presente un elenco di proprietà e relazioni originate da tale elemento. Le relazioni sono rappresentate sia nella propria destra che nelle classi di origine.

Nella tabella seguente sono riepilogate le opzioni che è possibile impostare in questa sezione della definizione DSL. In ogni caso, selezionare un elemento in DSL Explorer e impostare le opzioni nella Finestra Proprietà.

### <a name="xml-class-data"></a>Dati della classe XML

Questi elementi sono disponibili in Esplora DSL in **dati di serializzazione XML comportamento \Class**.

|||
|-|-|
|proprietà|Descrizione|
|Con schema di elemento personalizzato|Se true, indica che la classe di dominio ha uno schema di elemento personalizzato|
|Personalizzato|Impostare su **true** se si desidera scrivere codice di serializzazione e deserializzazione personalizzato per questa classe di dominio.<br /><br /> Compilare la soluzione ed esaminare gli errori per individuare istruzioni dettagliate.|
|Classe di dominio|Classe di dominio a cui si applica questo nodo dati della classe. Sola lettura.|
|Nome elemento|Nome del nodo XML per gli elementi di questa classe. Il valore predefinito è una versione minuscola del nome della classe di dominio.|
|Nome dell'attributo del moniker|Nome dell'attributo utilizzato negli elementi del moniker per contenere il riferimento. Se è vuoto, viene usato il nome della proprietà o dell'ID della chiave.<br /><br /> In questo esempio è "Name": `<personMoniker name="/Mike Nash"/>`|
|Nome dell'elemento moniker|Nome dell'elemento XML usato per i moniker che fanno riferimento agli elementi di questa classe.<br /><br /> Il valore predefinito è una versione minuscola del nome della classe con suffisso "moniker". Ad esempio `personMoniker`.|
|Nome del tipo di moniker|Nome del tipo XSD generato per i moniker degli elementi di questa classe. XSD è presente nel **codice Dsl\Generated \\ \*Schema. xsd**|
|ID serializzazione|Se true, il GUID dell'elemento è incluso nel file. Questo deve essere true se non è presente alcuna proprietà contrassegnata come **chiave del moniker** e il DSL definisce le relazioni di riferimento a questa classe.|
|Nome tipo|Nome del tipo XML generato in XSD dalla classe di dominio designata.|
|Note|Note informali associate a questo elemento|

### <a name="xml-property-data"></a>Dati della proprietà XML

I nodi di proprietà XML si trovano nei nodi della classe.

|||
|-|-|
|proprietà|Descrizione|
|Proprietà di dominio|Proprietà a cui si applicano i dati di configurazione della serializzazione XML. Sola lettura.|
|Chiave moniker|Se true, la proprietà viene utilizzata come chiave per la creazione di moniker che fanno riferimento a istanze di questa classe di dominio.|
|Qualificatore del moniker|Se true, la proprietà viene utilizzata per la creazione del qualificatore nei moniker. Se false e se SerializeId non è true per questa classe di dominio, i moniker vengono qualificati dal moniker dell'elemento padre nell'albero di incorporamento.|
|Rappresentazione|Se attribute, la proprietà viene serializzata come attributo XML; Se element, viene serializzato come elemento; Se ignore, non viene serializzato.|
|Nome XML|Nome usato per l'attributo o l'elemento XML che rappresenta la proprietà. Per impostazione predefinita, si tratta di una versione minuscola del nome della proprietà di dominio.|
|Note|Note informali associate a questo elemento|

### <a name="xml-role-data"></a>Dati del ruolo XML

I nodi dati del ruolo si trovano nei nodi della classe di origine.

|proprietà|Descrizione|
|-|-|
|Con moniker personalizzato|Impostare su true se si desidera fornire il proprio codice per la generazione e la risoluzione dei moniker che attraversano questa relazione.<br /><br /> Per istruzioni dettagliate, compilare la soluzione, quindi fare doppio clic sui messaggi di errore.|
|Relazione di dominio|Specifica la relazione a cui si applicano queste opzioni. Sola lettura.|
|Ometti (elemento)|Se true, il nodo XML che corrisponde al ruolo di origine viene omesso dallo schema.<br /><br /> Se esiste più di una relazione tra le classi di origine e di destinazione, questo nodo del ruolo distingue tra i collegamenti che appartengono alle due relazioni. Si consiglia pertanto di non impostare questa opzione in questo caso.|
|Nome elemento ruolo|Specifica il nome dell'elemento XML derivato dal ruolo di origine. Il valore predefinito è il nome della proprietà Role.|
|Usa formato completo|Se true, ogni elemento o moniker di destinazione è racchiuso in un nodo XML che rappresenta la relazione. Questo valore deve essere impostato su true se la relazione ha proprietà del dominio personalizzate.|

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)