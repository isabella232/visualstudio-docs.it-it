---
title: Personalizzazione dell'archiviazione dei file e della serializzazione XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8a21067eab6e55f3fb031e57fa2257b0d40a7eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886461"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personalizzare l'archiviazione dei file e la serializzazione XML

Quando l'utente salva un'istanza, oppure *modello*, di un linguaggio specifico di dominio (DSL) in Visual Studio, viene creato o aggiornato un file XML. Il file può essere ricaricato per ricreare il modello di Store.

È possibile personalizzare lo schema di serializzazione modificando le impostazioni in **comportamento di serializzazione Xml** in DSL Explorer. È presente un nodo sotto **comportamento di serializzazione Xml** per ogni classe di dominio, proprietà e relazioni. Le relazioni si trovano sotto le classi di origine. Sono inoltre presenti nodi corrispondenti per la forma, connettore e diagramma classi.

È anche possibile scrivere codice programma di personalizzazione più avanzata.

> [!NOTE]
> Se si desidera salvare il modello in un formato specifico, ma non è necessario ricaricarlo da tale modulo, considerare l'utilizzo di modelli di testo per generare l'output dal modello, invece di uno schema di serializzazione personalizzata. Per altre informazioni, vedere [generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>File di modello e diagramma

Ogni modello viene in genere salvato in due file:

-   Il file del modello ha un nome, ad esempio **Model1.mydsl**. Archivia gli elementi del modello e le relazioni e le relative proprietà. L'estensione di file, ad esempio **.mydsl** varia a seconda di **FileExtension** proprietà del **Editor** nodo nella definizione DSL.

-   Il file del diagramma ha un nome, ad esempio **Model1.mydsl.diagram**. Archivia le forme, connettori e le relative posizioni, colori, spessore di linea e altri dettagli dell'aspetto del diagramma. Se l'utente elimina un **. Diagram** file, le informazioni essenziali nel modello non vengono perse. Solo il layout del diagramma verrà perso. Quando viene aperto il file del modello, imposta un valore predefinito di forme e connettori verranno creati.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Per modificare l'estensione del file di un linguaggio DSL

1.  Aprire la definizione DSL. In DSL Explorer, fare clic sul nodo di Editor.

2.  Nella finestra Proprietà modificare il **FileExtension** proprietà. Non includere iniziale "." dell'estensione di file.

3.  In Esplora soluzioni, modificare il nome di file di modello di due elementi nel **DslPackage\ProjectItemTemplates**. Questi file presentano nomi che seguono questo formato:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Lo schema di serializzazione predefinito

Per creare un esempio di questo argomento, è stata usata la seguente definizione DSL.

![Diagramma di definizione DSL &#45; modello di albero genealogico](../modeling/media/familyt_person.png)

Questo linguaggio DSL è stato usato per creare un modello che ha l'aspetto seguente sullo schermo.

![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

Questo modello è stato salvato e quindi nuovamente aperto nell'editor di testo XML:

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

Notare gli aspetti seguenti relativi al modello serializzato:

-   Tutti i nodi XML ha un nome che corrisponde a quello di un nome di classe di dominio, ad eccezione del fatto che la lettera iniziale è in minuscola. Ad esempio, `familyTreeModel` e `person`.

-   Proprietà di dominio, ad esempio nome e DataNascita vengono serializzate come attributi in nodi XML. Anche in questo caso, il carattere iniziale del nome della proprietà viene convertito in caratteri minuscoli.

-   Ogni relazione viene serializzata come un nodo XML annidato all'interno della fine di origine della relazione. Il nodo ha lo stesso nome di proprietà del ruolo di origine, ma con un carattere iniziale minuscola.

     Ad esempio, nella definizione DSL, un ruolo denominato **persone** ha come origine il **albero genealogico FamilyTree** classe.  Nel XML schema, questo è rappresentato dal nodo denominato `people` annidato all'interno di `familyTreeModel` nodo.

-   Estremità di destinazione di ogni relazione di incorporamento viene serializzata come un nodo annidato sotto la relazione. Ad esempio, il `people` nodo contiene numerosi `person` nodi.

-   Estremità di destinazione di ogni relazione di riferimento viene serializzato come un *moniker*, che codifica un riferimento all'elemento di destinazione.

     Ad esempio, in un `person` nodo, può essere presente un `children` relazione. Questo nodo contiene i moniker, ad esempio:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Comprendere i moniker

Moniker vengono usati per rappresentare i riferimenti incrociati tra diverse parti dei file di modello e diagramma. Vengono usati anche nel `.diagram` file per fare riferimento ai nodi nel file del modello. Esistono due forme di moniker:

-   *Moniker di ID* citare il GUID dell'elemento di destinazione. Ad esempio:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Qualificato chiave moniker* identificare l'elemento di destinazione, il valore di una proprietà di dominio designata denominata chiave del moniker. Il moniker dell'elemento di destinazione viene aggiunto come prefisso il moniker dell'elemento padre nell'albero delle relazioni di incorporamento.

     Negli esempi seguenti vengono eseguiti da un linguaggio DSL in cui vi è una classe di dominio denominata Album, che ha una relazione di incorporamento a un dominio denominata brano di classe:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Completo chiave moniker verrà usato se la classe di destinazione dispone di una proprietà di dominio per cui l'opzione **chiave Moniker** è impostata su `true` nelle **comportamento di serializzazione Xml**. Nell'esempio, questa opzione è impostata per le proprietà di dominio denominate "Title" nelle classi di dominio "Album" e "Brano".

Completo chiave moniker sono più facili da leggere rispetto moniker ID. Se si vuole che il codice XML dei file di modello per essere letto da persone, prendere in considerazione l'utilizzo di moniker chiavi completo. Tuttavia, è possibile l'utente può impostare più di un elemento per avere la stessa chiave del moniker. Chiavi duplicate potrebbe causare il file non di ricaricare in modo corretto. Pertanto, se si definisce una classe di dominio a cui si fa riferimento l'utilizzo di moniker chiave completo, è consigliabile modi impedendo all'utente di salvare un file con moniker duplicati.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Per impostare una classe di dominio a cui fa riferimento il moniker di ID

1.  Verificare che l'opzione **chiave Moniker** è `false` per ogni proprietà di dominio nella classe e le relative classi base.

    1.  In DSL Explorer, espandere **dati di serializzazione Behavior\Class\\\<la classe di dominio > \Element dati**.

    2.  Verificare che **chiave Moniker** è `false` per ogni proprietà di dominio.

    3.  Se la classe di dominio dispone di una classe di base, ripetere la procedura descritta in tale classe.

2.  Impostare **serializza Id**  =  `true` per la classe di dominio.

     Questa proprietà sono disponibili in **comportamento di serializzazione Xml**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Per impostare una classe di dominio a cui fa riferimento qualificato chiave moniker

-   Impostare **chiave Moniker** per una proprietà di dominio di una classe di dominio esistente. Il tipo della proprietà deve essere `string`.

    1.  In DSL Explorer, espandere **dati di serializzazione Behavior\Class\\\<la classe di dominio > \Element dati**e quindi selezionare la proprietà di dominio.

    2.  Nella finestra Proprietà impostare **chiave Moniker** a `true`.

-   \- oppure -

     Creare una nuova classe di dominio utilizzando il **classe di dominio denominata** dello strumento.

     Questo strumento crea una nuova classe che dispone di una proprietà di dominio denominata Name. Il **è nome elemento** e **chiave Moniker** le proprietà di questa proprietà di dominio vengono inizializzate `true`.

-   \- oppure -

     Creare una relazione di ereditarietà dalla classe di dominio a un'altra classe che ha una proprietà chiave del moniker.

### <a name="avoid-duplicate-monikers"></a>Evitare i moniker duplicati

Se si usano i moniker chiave completi, è possibile che due elementi nel modello a un utente potrebbe avere lo stesso valore nella proprietà di chiave. Ad esempio, se il linguaggio DSL dispone di una persona che ha un nome di proprietà di classe, l'utente è stato possibile impostare i nomi di due elementi sia lo stesso. Anche se il modello può essere salvata in file, sarebbe non ricaricare in modo corretto.

Esistono diversi metodi che consentono di evitare questa situazione:

-   Impostare **è nome elemento**  =  `true` per la proprietà di dominio principale. Selezionare la proprietà di dominio nel diagramma di definizione DSL e quindi impostare il valore nella finestra Proprietà.

     Quando l'utente crea una nuova istanza della classe, questo valore fa sì che la proprietà di dominio venga assegnato automaticamente un valore diverso. Il comportamento predefinito viene aggiunto un numero alla fine del nome della classe. Ciò non impedisce all'utente di modificare il nome di un duplicato, ma utile nel caso quando l'utente non è impostato il valore prima di salvare il modello.

-   Abilitare la convalida per il linguaggio DSL. In DSL Explorer selezionare editor\convalida e impostare il **Usa...**  proprietà `true`.

     È disponibile un metodo di convalida generato automaticamente che controlli per le ambiguità. Il metodo è racchiuso il `Load` categoria di convalida. Ciò assicura che l'utente verrà visualizzato un avviso che potrebbe non essere possibile riaprire il file.

     Per altre informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>I percorsi di moniker e i qualificatori

Un moniker di chiave completo termina con la chiave del moniker e viene anteposto con il moniker dell'elemento padre nell'albero di incorporamento. Ad esempio, se il moniker di un Album è:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Quindi potrebbe essere uno dei brani che contiene:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Tuttavia, se gli album fanno riferimento invece ID, quindi i moniker verrà visualizzata come indicato di seguito:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Si noti che poiché un GUID è univoco, che non è mai preceduto dal moniker del relativo padre.

Se si sa che una proprietà di dominio specifica avrà sempre un valore univoco all'interno di un modello, è possibile impostare **è il qualificatore del Moniker** a `true` per tale proprietà. In questo modo può essere usato come qualificatore, senza usare il moniker dell'elemento padre. Ad esempio, se si impostano entrambe **è il qualificatore del Moniker** e **chiave Moniker** per la proprietà di dominio Title della classe Album, nome o l'identificatore del modello non viene usato nei moniker per Album e relativo incorporato elementi figlio:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personalizzare la struttura del codice XML

Per apportare le seguenti personalizzazioni, espandere la **comportamento di serializzazione Xml** nodo in Esplora DSL. In una classe di dominio, espandere il nodo dell'elemento dati per visualizzare l'elenco di proprietà e relazioni che hanno origine in questa classe. Selezionare una relazione e regolare le opzioni nella finestra Proprietà.

-   Impostare **omettere elemento** su true per non includere il nodo ruolo di origine, lasciando solo l'elenco di elementi di destinazione. È necessario impostare questa opzione se non esiste più di una relazione tra le classi di origine e di destinazione.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Impostare **forma completa usare** per incorporare i nodi di destinazione nei nodi che rappresentano le istanze della relazione. Questa opzione viene impostata automaticamente quando si aggiungono le proprietà di dominio a una relazione di dominio.

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

-   Impostare **rappresentazione** = **elemento** disponga di una proprietà di dominio salvata come elemento anziché come valore di attributo.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Per modificare l'ordine in cui vengono serializzate gli attributi e relazioni, fare doppio clic su un elemento sotto l'elemento dati e usare la **Move Up** oppure **Sposta giù** i comandi di menu.

## <a name="major-customization-using-program-code"></a>Personalizzazione principale usando codice programma

È possibile sostituire parti o tutti gli algoritmi di serializzazione.

È consigliabile esaminare il codice nel **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Personalizzare la serializzazione di una determinata classe

1.  Impostare **personalizzata viene** nel nodo per tale classe sotto **comportamento di serializzazione Xml**.

2.  Trasforma tutti i modelli, compilare la soluzione e analizzare gli errori di compilazione risultante. Commenti quasi ogni errore illustrano il codice è necessario fornire.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Per fornire la serializzazione personalizzata per l'intero modello

1.  Eseguire l'override di metodi in Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opzioni di comportamento di serializzazione Xml

In Esplora DSL, il nodo di comportamento di serializzazione Xml contiene un nodo figlio per ogni classe di dominio, relazione, forma, connettore e classe diagramma. In ognuna di tali nodi è un elenco di proprietà e relazioni originate in quell'elemento. Le relazioni sono rappresentate in proprio a destra e sotto le classi di origine.

Nella tabella seguente vengono riepilogate le opzioni che è possibile impostare in questa sezione della definizione DSL. In ogni caso, selezionare un elemento in Esplora DSL e impostare le opzioni nella finestra Proprietà.

### <a name="xml-class-data"></a>Dati XML (classe)

Questi elementi sono disponibili in Esplora DSL sotto **dati Behavior\Class della serializzazione Xml**.

|||
|-|-|
|Proprietà|Descrizione|
|È lo Schema di elemento personalizzato|Se True, indica che la classe di dominio ha uno schema di elemento personalizzati|
|È personalizzato|Impostare questa opzione su **True** se si desidera scrivere codice di serializzazione e deserializzazione per questa classe di dominio.<br /><br /> Compilare la soluzione, esaminare gli errori per individuare le istruzioni dettagliate.|
|Classe di dominio|Classe di dominio a cui si applica questo nodo di dati di classe. Sola lettura.|
|Nome elemento|Nome del nodo XML per gli elementi di questa classe. Il valore predefinito è una versione con caratteri minuscoli del nome della classe di dominio.|
|Nome di attributo moniker|Nome dell'attributo utilizzato in elementi del moniker per contenere il riferimento. Se vuoto, viene utilizzato il nome della proprietà chiave o id.<br /><br /> In questo esempio è "name":  `<personMoniker name="/Mike Nash"/>`|
|Nome di elemento moniker|Nome dell'elemento xml utilizzato per i moniker che fanno riferimento agli elementi di questa classe.<br /><br /> Il valore predefinito è una versione in caratteri minuscoli del nome della classe aggiunto il suffisso "Moniker". Ad esempio `personMoniker`.|
|Nome del tipo di moniker|Nome del tipo xsd generato per i moniker a elementi di questa classe. il XSD è nel **codice Dsl\Generated\\\*schema. xsd**|
|Serializzare Id|Se True, il GUID elemento è incluso nel file. Deve essere true se è presente nessuna proprietà contrassegnato **chiave Moniker** e il linguaggio DSL definisce le relazioni di riferimento a questa classe.|
|Nome tipo|Nome del tipo xml generato in xsd dalla classe di dominio designata.|
|Note|Note informali associate all'elemento|

### <a name="xml-property-data"></a>Dati di proprietà XML

I nodi di proprietà XML si trovano sotto i nodi di classe.

|||
|-|-|
|Proprietà|Descrizione|
|Proprietà di dominio|Proprietà a cui si applicano i dati di configurazione della serializzazione xml. Sola lettura.|
|È di Moniker chiave|Se True, la proprietà viene utilizzata come chiave per la creazione di moniker che fanno riferimento alle istanze di questa classe di dominio.|
|È il qualificatore del Moniker|Se True, la proprietà viene utilizzata per la creazione del qualificatore nei moniker. Se false, e se non è true per questa classe di dominio SerializeId, i moniker sono qualificati dal moniker dell'elemento padre nell'albero di incorporamento.|
|Rappresentazione|Se Attribute, la proprietà viene serializzata come attributo xml; Se l'elemento è serializzato come elemento. Se Ignore, non è serializzato.|
|Nome XML|Nome utilizzato per l'attributo o elemento xml che rappresenta la proprietà. Per impostazione predefinita, questa è una versione con caratteri minuscoli del nome della proprietà di dominio.|
|Note|Note informali associate all'elemento|

### <a name="xml-role-data"></a>Dati del ruolo di XML

Nodi di ruolo dati si trovano in nodi di classe di origine.

|Proprietà|Descrizione|
|-|-|
|È di Moniker personalizzato|Impostare su true se si desidera fornire il proprio codice per la generazione e la risoluzione di moniker che passano attraverso questa relazione.<br /><br /> Per istruzioni dettagliate, compilare la soluzione e quindi fare doppio clic sui messaggi di errore.|
|Relazione di dominio|Specifica la relazione in cui queste opzioni si applicano. Sola lettura.|
|Omettere l'elemento|Se true, il nodo XML che corrisponde al ruolo di origine viene omesso dallo schema.<br /><br /> Se è presente più di una relazione tra le classi di origine e di destinazione, questo nodo del ruolo viene fatta distinzione tra i collegamenti che appartengono a due relazioni. È pertanto consigliabile non impostare questa opzione in questo caso.|
|Nome dell'elemento ruolo|Specifica il nome dell'elemento XML che deriva dal ruolo di origine. Il valore predefinito è il nome di proprietà del ruolo.|
|Usare il modulo completo|Se true, ogni elemento di destinazione o il moniker è racchiuso in un nodo XML che rappresenta la relazione. Questo deve essere impostato su true se la relazione ha le proprie proprietà di dominio.|

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)