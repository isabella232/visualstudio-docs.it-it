---
title: Personalizzazione dell'archiviazione dei file e della serializzazione XML
description: Informazioni sul file XML creato o aggiornato quando si salva un'istanza o un modello di un linguaggio specifico di dominio (DSL) in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cf3f80c51866f278f4cf9a72876963d60ab17e4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061311"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personalizzare l'archiviazione dei file e la serializzazione XML

Quando l'utente salva un'istanza, o modello *,* di un linguaggio specifico di dominio (DSL) in Visual Studio, viene creato o aggiornato un file XML. Il file può essere ricaricato per ricreare il modello nell'archivio.

È possibile personalizzare lo schema di serializzazione modificando le impostazioni in **Comportamento di serializzazione XML** in Esplora linguaggio DSL. È presente un nodo in **Xml Serialization Behavior** per ogni classe di dominio, proprietà e relazione. Le relazioni si trovano sotto le classi di origine. Sono presenti anche nodi corrispondenti alle classi shape, connector e diagram.

È anche possibile scrivere codice programma per una personalizzazione più avanzata.

> [!NOTE]
> Se si vuole salvare il modello in un formato specifico, ma non è necessario ricaricarlo da tale modulo, è consigliabile usare modelli di testo per generare l'output dal modello, anziché uno schema di serializzazione personalizzato. Per altre informazioni, vedere [Generazione di codice da un Domain-Specific linguaggio .](../modeling/generating-code-from-a-domain-specific-language.md)

## <a name="model-and-diagram-files"></a>File di modello e diagramma

Ogni modello viene in genere salvato in due file:

- Il file di modello ha un nome, ad esempio **Model1.mydsl.** Archivia gli elementi del modello e le relazioni e le relative proprietà. L'estensione di file, ad esempio **mydsl,** è determinata dalla proprietà **FileExtension** del nodo **Editor** nella definizione DSL.

- Il file di diagramma ha un nome, ad esempio **Model1.mydsl.diagram.** Archivia le forme, i connettori e le relative posizioni, colori, spessori di linea e altri dettagli dell'aspetto del diagramma. Se l'utente elimina un file **con estensione diagram,** le informazioni essenziali nel modello non vengono perse. Viene perso solo il layout del diagramma. Quando il file di modello viene aperto, verrà creato un set predefinito di forme e connettori.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Per modificare l'estensione di file di un DSL

1. Aprire la definizione DSL. In Esplora DSL fare clic sul nodo Editor.

2. Nel Finestra Proprietà modificare la **proprietà FileExtension.** Non includere l'iniziale "." dell'estensione di file.

3. In Esplora soluzioni modificare il nome dei due file modello di elemento in **DslPackage\ProjectItemTemplates**. Questi file hanno nomi che seguono questo formato:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Schema di serializzazione predefinito

Per creare un esempio per questo argomento, è stata usata la definizione DSL seguente.

![Diagramma di definizione DSL &#45; albero genealogico](../modeling/media/familyt_person.png)

Questo DSL è stato usato per creare un modello con l'aspetto seguente sullo schermo.

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

Si notino i punti seguenti sul modello serializzato:

- Ogni nodo XML ha un nome uguale a quello di una classe di dominio, ad eccezione del fatto che la lettera iniziale è minuscola. Ad esempio, `familyTreeModel` e `person`.

- Le proprietà di dominio, ad esempio Name e BirthYear, vengono serializzate come attributi nei nodi XML. Anche in questo caso, il carattere iniziale del nome della proprietà viene convertito in minuscolo.

- Ogni relazione viene serializzata come nodo XML annidato all'interno dell'estremità di origine della relazione. Il nodo ha lo stesso nome della proprietà del ruolo di origine, ma con un carattere iniziale minuscolo.

     Ad esempio, nella definizione DSL un ruolo denominato **People** viene creato nella **classe FamilyTree.**  Nel codice XML è rappresentato dal nodo denominato `people` annidato all'interno del `familyTreeModel` nodo.

- L'estremità di destinazione di ogni relazione di incorporamento viene serializzata come nodo annidato nella relazione. Ad esempio, il `people` nodo contiene diversi `person` nodi.

- L'estremità di destinazione di ogni relazione di riferimento viene serializzata come *moniker*, che codifica un riferimento all'elemento di destinazione.

     Ad esempio, in un `person` nodo può essere presente una `children` relazione. Questo nodo contiene moniker come:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Informazioni su Moniker

I moniker vengono usati per rappresentare i riferimenti incrociati tra le diverse parti del modello e i file di diagramma. Vengono inoltre usati nel `.diagram` file per fare riferimento ai nodi nel file di modello. Esistono due forme di moniker:

- *I moniker ID* virgolette il GUID dell'elemento di destinazione. Esempio:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *I moniker di chiave qualificati* identificano l'elemento di destinazione in base al valore di una proprietà di dominio designata denominata chiave moniker. Il moniker dell'elemento di destinazione è preceduto dal moniker dell'elemento padre nell'albero delle relazioni di incorporamento.

     Gli esempi seguenti sono presi da un DSL in cui è presente una classe di dominio denominata Album, che ha una relazione di incorporamento con una classe di dominio denominata Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     I moniker di chiave qualificati verranno usati se la classe di destinazione ha una proprietà di dominio per cui l'opzione **Is Moniker Key** è impostata su in Xml Serialization `true` **Behavior**. Nell'esempio questa opzione è impostata per le proprietà di dominio denominate "Title" nelle classi di dominio "Album" e "Song".

I moniker di chiave qualificati sono più facili da leggere rispetto ai moniker ID. Se si prevede che il codice XML dei file di modello sia letto dagli utenti, è consigliabile usare moniker di chiave qualificati. Tuttavia, è possibile che l'utente imposta più di un elemento con la stessa chiave del moniker. Le chiavi duplicate potrebbero causare il non ricaricamento corretto del file. Pertanto, se si definisce una classe di dominio a cui viene fatto riferimento usando moniker di chiave qualificati, è consigliabile prendere in considerazione la possibilità di impedire all'utente di salvare un file con moniker duplicati.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Per impostare una classe di dominio a cui fare riferimento dai moniker ID

1. Assicurarsi che **Is Moniker Key sia** per ogni proprietà di dominio nella classe e nelle relative classi di `false` base.

    1. In Esplora linguaggio DSL espandere **Comportamento di serializzazione XML\Dati \\ \<the domain class> classe \Dati elemento**.

    2. Verificare che **Is Moniker Key sia** per ogni proprietà di `false` dominio.

    3. Se la classe di dominio ha una classe di base, ripetere la procedura in tale classe.

2. Impostare **l'ID di**  =  `true` serializzazione per la classe di dominio.

     Questa proprietà è disponibile in **Comportamento di serializzazione XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Per impostare una classe di dominio a cui i moniker di chiave qualificati fanno riferimento

- Impostare **Is Moniker Key** per una proprietà di dominio di una classe di dominio esistente. Il tipo della proprietà deve essere `string` .

    1. In Esplora linguaggio DSL espandere **Xml Serialization Behavior\Class Data \\ \<the domain class> \Element Data** e quindi selezionare la proprietà domain.

    2. Nella finestra Finestra Proprietà impostare **Is Moniker Key** su `true` .

- \- - oppure -

     Creare una nuova classe di dominio usando lo **strumento Classe di dominio** denominata.

     Questo strumento crea una nuova classe con una proprietà di dominio denominata Name. Le **proprietà Is Element Name** e Is **Moniker Key** di questa proprietà di dominio vengono inizializzate su `true` .

- \- - oppure -

     Creare una relazione di ereditarietà dalla classe di dominio a un'altra classe con una proprietà chiave del moniker.

### <a name="avoid-duplicate-monikers"></a>Evitare moniker duplicati

Se si usano moniker di chiave qualificati, è possibile che due elementi nel modello di un utente potrebbero avere lo stesso valore nella proprietà key. Ad esempio, se il DSL ha una classe Person con una proprietà Name, l'utente può impostare i nomi di due elementi in modo che siano uguali. Anche se il modello può essere salvato in un file, non verrebbe ricaricato correttamente.

Esistono diversi metodi che consentono di evitare questa situazione:

- Impostare **è il nome dell'elemento** per la proprietà del dominio della  =  `true` chiave. Selezionare la proprietà domain nel diagramma di definizione DSL e quindi impostare il valore nel Finestra Proprietà.

     Quando l'utente crea una nuova istanza della classe , questo valore determina l'assegnazione automatica di un valore diverso alla proprietà di dominio. Il comportamento predefinito aggiunge un numero alla fine del nome della classe. Ciò non impedisce all'utente di modificare il nome in un duplicato, ma è utile nel caso in cui l'utente non imposta il valore prima di salvare il modello.

- Abilitare la convalida per il DSL. In Esplora DSL selezionare Editor\Convalida e impostare le proprietà **Usa** su `true` .

     Esiste un metodo di convalida generato automaticamente che verifica la presenza di ambiguità. Il metodo si trova nella `Load` categoria di convalida. In questo modo si garantisce che l'utente venga avvisato che potrebbe non essere possibile aprire nuovamente il file.

     Per altre informazioni, vedere [Convalida in un linguaggio Domain-Specific.](../modeling/validation-in-a-domain-specific-language.md)

### <a name="moniker-paths-and-qualifiers"></a>Percorsi e qualificatori moniker

Un moniker di chiave qualificato termina con la chiave del moniker ed è preceduto dal moniker del relativo elemento padre nell'albero di incorporamento. Ad esempio, se il moniker di un album è:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Uno dei brani dell'album potrebbe quindi essere:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Tuttavia, se invece si fa riferimento ad Albums in base all'ID, i moniker saranno i seguenti:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Si noti che poiché un GUID è univoco, non viene mai preceduto dal moniker del relativo elemento padre.

Se si sa che una determinata proprietà di dominio avrà sempre un valore univoco all'interno di un modello, è possibile impostare **Qualificatore moniker** is su `true` per tale proprietà. In questo modo verrà usato come qualificatore, senza usare il moniker dell'elemento padre. Ad esempio, se si impostano sia Is Moniker Qualifier (Qualificatore moniker Is) che **Is Moniker Key** (Chiave moniker is) per la proprietà title domain (Titolo) della classe Album, il nome o l'identificatore del modello non viene usato nei **moniker** per Album e i relativi elementi figlio incorporati:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personalizzare la struttura del codice XML

Per apportare le personalizzazioni seguenti, espandere il **nodo Comportamento di serializzazione XML** in Esplora DSL. In una classe di dominio espandere il nodo Dati elemento per visualizzare l'elenco delle proprietà e delle relazioni che hanno origine in questa classe. Selezionare una relazione e modificarne le opzioni nella Finestra Proprietà.

- Impostare **Omit Element (Ometti** elemento) su true per omettere il nodo del ruolo di origine, lasciando solo l'elenco degli elementi di destinazione. È consigliabile non impostare questa opzione se è presente più di una relazione tra le classi di origine e di destinazione.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Impostare **Usa modulo completo per** incorporare i nodi di destinazione nei nodi che rappresentano le istanze della relazione. Questa opzione viene impostata automaticamente quando si aggiungono proprietà di dominio a una relazione di dominio.

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

- Impostare **Representation**  =  **Element in** modo che una proprietà di dominio sia salvata come elemento anziché come valore di attributo.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Per modificare l'ordine di serializzazione degli attributi e delle relazioni, fare  clic con il pulsante destro del mouse su un elemento in Dati elementoe usare i comandi di menu Sposta su o **Sposta giù** .

## <a name="major-customization-using-program-code"></a>Personalizzazione principale tramite codice programma

È possibile sostituire parti o tutti gli algoritmi di serializzazione.

È consigliabile studiare il codice in **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Per personalizzare la serializzazione di una classe specifica

1. Impostare **Is Custom nel** nodo per la classe in Comportamento di **serializzazione XML**.

2. Trasformare tutti i modelli, compilare la soluzione ed esaminare gli errori di compilazione risultanti. I commenti accanto a ogni errore illustrano il codice da fornire.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Per fornire la serializzazione personalizzata per l'intero modello

1. Eseguire l'override dei metodi in Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opzioni nel comportamento di serializzazione XML

In Esplora DSL il nodo Comportamento di serializzazione XML contiene un nodo figlio per ogni classe di dominio, relazione, forma, connettore e classe diagramma. In ognuno di questi nodi è disponibile un elenco di proprietà e relazioni che hanno origine in corrispondenza di tale elemento. Le relazioni sono rappresentate sia nel proprio diritto che nelle relative classi di origine.

La tabella seguente riepiloga le opzioni che è possibile impostare in questa sezione della definizione DSL. In ogni caso, selezionare un elemento in Esplora DSL e impostare le opzioni nel Finestra Proprietà.

### <a name="xml-class-data"></a>Dati della classe XML

Questi elementi sono disponibili in Esplora DSL in **Comportamento di serializzazione XML\Dati classe**.

|Proprietà|Descrizione|
|-|-|
|Ha uno schema di elemento personalizzato|Se True, indica che la classe di dominio ha uno schema di elemento personalizzato|
|È personalizzato|Impostare questa proprietà **su True** se si vuole scrivere codice di serializzazione e deserializzazione personalizzato per questa classe di dominio.<br /><br /> Compilare la soluzione ed esaminare gli errori per individuare istruzioni dettagliate.|
|Classe di dominio|Classe di dominio a cui si applica questo nodo dati della classe. Di sola lettura.|
|Nome dell'elemento|Nome del nodo XML per gli elementi di questa classe. Il valore predefinito è una versione in lettere minuscole del nome della classe di dominio.|
|Nome attributo moniker|Nome dell'attributo utilizzato negli elementi del moniker per contenere il riferimento. Se vuoto, viene utilizzato il nome o l'ID della proprietà chiave.<br /><br /> In questo esempio è "name":  `<personMoniker name="/Mike Nash"/>`|
|Nome dell'elemento Moniker|Nome dell'elemento xml utilizzato per i moniker che fanno riferimento agli elementi di questa classe.<br /><br /> Il valore predefinito è una versione minuscola del nome della classe con suffisso "Moniker". Ad esempio, `personMoniker`.|
|Nome del tipo di moniker|Nome del tipo XSD generato per i moniker a elementi di questa classe. Lo schema XSD si trova in **Dsl\Generated Code \\ \* Schema.xsd**|
|Serialize Id|Se True, il GUID dell'elemento viene incluso nel file. Deve essere true se non è presente alcuna proprietà contrassegnata come **Is Moniker Key** e il DSL definisce relazioni di riferimento a questa classe.|
|Nome tipo|Nome del tipo XML generato in XSD dalla classe di dominio designata.|
|Note|Note informali associate a questo elemento|

### <a name="xml-property-data"></a>Dati delle proprietà XML

I nodi delle proprietà XML si trovano sotto i nodi della classe .

|Proprietà|Descrizione|
|-|-|
|Proprietà Domain|Proprietà a cui si applicano i dati di configurazione della serializzazione XML. Di sola lettura.|
|Chiave del moniker|Se True, la proprietà viene usata come chiave per la creazione di moniker che fanno riferimento a istanze di questa classe di dominio.|
|Qualificatore di moniker|Se True, la proprietà viene utilizzata per la creazione del qualificatore nei moniker. Se false e se SerializeId non è true per questa classe di dominio, i moniker vengono qualificati dal moniker dell'elemento padre nell'albero di incorporamento.|
|Rappresentazione|Se Attribute, la proprietà viene serializzata come attributo XML, se Element, viene serializzata come elemento; se Ignore, non viene serializzata.|
|Nome XML|Nome utilizzato per l'attributo o l'elemento XML che rappresenta la proprietà. Per impostazione predefinita, si tratta di una versione in lettere minuscole del nome della proprietà di dominio.|
|Note|Note informali associate a questo elemento|

### <a name="xml-role-data"></a>Dati del ruolo XML

I nodi dati del ruolo si trovano nei nodi della classe di origine.

|Proprietà|Descrizione|
|-|-|
|Ha moniker personalizzato|Impostare questa proprietà su true se si vuole fornire il proprio codice per la generazione e la risoluzione dei moniker che attraversano questa relazione.<br /><br /> Per istruzioni dettagliate, compilare la soluzione e quindi fare doppio clic sui messaggi di errore.|
|Relazione di dominio|Specifica la relazione a cui si applicano queste opzioni. Di sola lettura.|
|Elemento Omit|Se true, il nodo XML che corrisponde al ruolo di origine viene omesso dallo schema.<br /><br /> Se è presente più di una relazione tra le classi di origine e di destinazione, questo nodo del ruolo distingue tra i collegamenti che appartengono alle due relazioni. È pertanto consigliabile non impostare questa opzione in questo caso.|
|Nome dell'elemento Role|Specifica il nome dell'elemento XML derivato dal ruolo di origine. Il valore predefinito è il nome della proprietà del ruolo.|
|Usa modulo completo|Se true, ogni elemento o moniker di destinazione è racchiuso in un nodo XML che rappresenta la relazione. Deve essere impostato su true se la relazione ha proprietà di dominio proprie.|

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)
