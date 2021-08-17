---
title: Generazione di codice in fase di progettazione tramite modelli di testo T4
description: Informazioni su come i modelli di testo T4 in fase di progettazione consentono di generare codice programma e altri file nel Visual Studio progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c2575ae7868eb058a4d500e77bc3ff14e0492a51b751202a3ad44baf65ca98fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356162"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generazione di codice in fase di progettazione tramite modelli di testo T4

I modelli di testo T4 in fase di progettazione consentono di generare codice di programma e altri file nel Visual Studio progetto. In genere, si scrivono i modelli in modo che varino il codice generato in base ai dati di un *modello*. Un modello è un file o un database che contiene informazioni chiave sui requisiti dell'applicazione.

È ad esempio possibile usare un modello per definire un flusso di lavoro come tabella o diagramma. Dal modello è possibile generare il software che esegue il flusso di lavoro. Quando i requisiti degli utenti cambiano, è facile discutere il nuovo flusso di lavoro con gli utenti. La rigenerazione di codice dal flusso di lavoro è più attendibile dell'aggiornamento manuale del codice.

> [!NOTE]
> Un *modello* è un'origine dati che descrive un particolare aspetto di un'applicazione. Può avere qualsiasi formato, in qualsiasi tipo di file o database. Non deve avere un formato specifico, ad esempio un modello UML o un modello di linguaggio specifico di dominio. In genere i modelli hanno formato di tabelle o file XML.

Se, come è probabile, si ha già esperienza di generazione di codice, Quando si definiscono le risorse in un file con estensione **resx** nella soluzione Visual Studio, viene generato automaticamente un set di classi e metodi. Il file di risorse semplifica e rende più affidabile la modifica delle risorse rispetto alla modifica dei classi e dei metodi. I modelli di testo permettono di generare codice nello stesso modo da un'origine personalizzata.

Un modello di testo include una combinazione del testo da generare e di codice programma che genera le parti variabili del testo. Il codice del programma consente di ripetere o omettere in modo condizionale parti del testo generato. Il testo generato può essere a sua volta codice programma che genererà parte dell'applicazione.

## <a name="create-a-design-time-t4-text-template"></a>Creare un Design-Time di testo T4

1. Creare un nuovo Visual Studio progetto o aprirne uno esistente.

2. Aggiungere un file modello di testo al progetto e assegnargli un nome con estensione **tt**.

    A tale scopo, **nel Esplora soluzioni** scegliere **Aggiungi** nuovo elemento dal menu di scelta rapida  >  **del progetto.** Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Modello di **testo** nel riquadro centrale.

    Si noti che **la proprietà Strumento** personalizzato del file è **TextTemplatingFileGenerator**.

3. Open the file. Includerà già le direttive seguenti:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Se il modello è stato aggiunto a un progetto di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], l'attributo relativo al linguaggio sarà "`VB`".

4. Aggiungere testo alla fine del file. Ad esempio:

   ```
   Hello, world!
   ```

5. Salvare il file.

    Potrebbe essere visualizzata una **finestra di messaggio** Avviso di sicurezza che chiede di confermare l'esecuzione del modello. Fare clic su **OK**.

6. In **Esplora soluzioni** espandere il nodo del file modello e si troverà un file con estensione **.txt**. Il file contiene testo generato dal modello.

   > [!NOTE]
   > Se il progetto è un Visual Basic, è necessario fare clic **su Mostra** tutti i file per visualizzare il file di output.

### <a name="regenerate-the-code"></a>Rigenerare il codice

Nei casi seguenti sarà eseguito un modello, che genera il file secondario:

- Modificare il modello e quindi passare lo stato attivo a un'altra Visual Studio finestra.

- Salvare il modello.

- Fare **clic su Trasforma tutti i** modelli nel menu Compila.  In questo modo verranno trasformati tutti i modelli nella Visual Studio soluzione.

- In **Esplora soluzioni** scegliere Esegui strumento personalizzato dal menu di scelta **rapida di qualsiasi file.** Usare questo metodo per trasformare un sottoinsieme selezionato di modelli.

È anche possibile configurare un progetto Visual Studio in modo che i modelli siano eseguiti quando i file di dati letti sono stati modificati. Per altre informazioni, vedere [Rigenerazione automatica del codice.](#Regenerating)

## <a name="generate-variable-text"></a>Generare testo variabile

I modelli di testo permettono di usare il codice programma per variare il contenuto del file generato.

1. Modificare il contenuto del file `.tt`:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Salvare il file con estensione tt ed esaminare di nuovo il file con estensione txt generato. Elenca i quadrati dei numeri da 0 a 10.

   Si noti che le istruzioni sono racchiuse tra `<#...#>` e le singole espressioni tra `<#=...#>`. Per altre informazioni, vedere [Scrittura di un modello di testo T4.](../modeling/writing-a-t4-text-template.md)

   Se si scrive il codice di generazione in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], la direttiva `template` deve includere `language="VB"`. `"C#"` è l'impostazione predefinita.

## <a name="debugging-a-design-time-t4-text-template"></a>Debug di un modello di testo T4 in fase di progettazione

Per eseguire il debug di un modello di testo:

- Inserire `debug="true"` nella direttiva `template`. Esempio:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Impostare punti di interruzione nel modello, esattamente come per il codice normale.

- Scegliere **Debug modello T4** dal menu di scelta rapida del file modello di testo in Esplora soluzioni.

   Il modello viene eseguito e arrestato in corrispondenza dei punti di interruzione. È possibile esaminare le variabili ed eseguire il codice un'istruzione alla volta usando le procedure normali.

> [!TIP]
> `debug="true"` rende il mapping del codice generato più accurato al modello di testo, inserendo più direttive di numerazione delle righe nel codice generato. Se non si include la clausola, è possibile che i punti di interruzione arrestino l'esecuzione nello stato errato.
>
> È comunque possibile lasciare la clausola nella direttiva del modello anche quando non si esegue il debug. Ciò provoca solo un minimo calo nelle prestazioni.

## <a name="generating-code-or-resources-for-your-solution"></a>Generazione di codice o risorse per la soluzione

È possibile generare file di programma diversi in base al modello. Un modello è un input quale un database, un file di configurazione, un modello UML, un modello DSL o un'altra origine. In genere si generano diversi file di programma dallo stesso modello. Per ottenere questo risultato, creare un file di modello per ogni file di programma generato e fare in modo che tutti i modelli leggano lo stesso modello.

### <a name="to-generate-program-code-or-resources"></a>Per generare codice programma o risorse

1. Modificare la direttiva di output in modo da generare un file di tipo appropriato, ad esempio un file con estensione cs, vb, resx oppure xml.

2. Inserire codice per la generazione del codice soluzione necessario. Ad esempio, per generare tre dichiarazioni di campo con valore Integer in una classe:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Salvare il file ed esaminare il file generato, che ora contiene il codice seguente:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Codice di generazione e testo generato

Quando si genera codice programma, è molto importante evitare di confondere il codice di generazione in esecuzione nel modello e il codice generato risultante, che diventa parte della soluzione. Non è necessario che i due linguaggi siano uguali.

Nell'esempio precedente sono usate due versioni, una con codice di generazione in C# e l'altra con codice di generazione in Visual Basic. Il testo generato da entrambe è lo stesso, ovvero una classe C#.

Analogamente, è possibile usare un modello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] per generare codice in qualsiasi linguaggio. Non è necessario che il testo generato sia in un linguaggio specifico o che sia codice programma.

### <a name="structuring-text-templates"></a>Strutturazione di modelli di testo

È consigliabile separare il codice del modello in due parti:

- Una parte di configurazione o di raccolta dati, che imposta i valori nelle variabili ma non include blocchi di testo. Nell'esempio precedente questa parte corrisponde all'inizializzazione di `properties`.

   Questa è spesso definita la sezione "modello", poiché costruisce un modello in archivio e in genere legge un file di modello.

- La parte di generazione del testo (`foreach(...){...}` nell'esempio), che usa i valori delle variabili.

   Questa separazione non è necessaria, ma semplifica la lettura del modello, riducendo la complessità della parte che include il testo.

## <a name="reading-files-or-other-sources"></a>Lettura di file o di altre origini

Per accedere a un file di modello o a un database, il codice del modello può usare assembly quali System.XML. Per ottenere l'accesso a questi assembly, è necessario inserire direttive simili alle seguenti:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

La `assembly` direttiva rende disponibile l'assembly specificato per il codice del modello, nello stesso modo della sezione Riferimenti di un Visual Studio progetto. Non è necessario includere un riferimento a System.dll, perché i riferimenti a questo file sono automatici. La direttiva `import` consente di usare tipi senza usare i rispettivi nomi completi, in modo simile alla direttiva `using` in un normale file di programma.

Ad esempio, dopo aver importato **System.IO**, è possibile scrivere:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Apertura di un file con un nome di percorso relativo

Per caricare un file da un percorso relativo al modello di testo, è possibile usare `this.Host.ResolvePath()`. Per usare this.Host, occorre impostare `hostspecific="true"` in `template`:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

È quindi possibile scrivere, ad esempio:

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Si può anche usare `this.Host.TemplateFile`, che identifica il nome del file di modello corrente.

Il tipo di `this.Host` (in VB `Me.Host`) è `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Recupero di dati da Visual Studio

Per usare i servizi forniti in Visual Studio, impostare `hostSpecific` l'attributo e caricare `EnvDTE` l'assembly. Importare `Microsoft.VisualStudio.TextTemplating` , che contiene il metodo di `GetCOMService()` estensione.  Sarà quindi possibile usare IServiceProvider.GetCOMService() per accedere a DTE e ad altri servizi. Esempio:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Un modello di testo è eseguito nel rispettivo dominio di app e l'accesso ai servizi è effettuato tramite marshalling. In questa circostanza, GetCOMService() è più affidabile di GetService().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Rigenerazione automatica del codice

In genere, più file in una Visual Studio vengono generati con un modello di input. Ogni file è generato dal modello corrispondente, ma i modelli fanno tutti riferimento allo stesso modello.

In caso di modifica al modello di origine, è consigliabile eseguire di nuovo tutti i modelli della soluzione. Per eseguire questa operazione manualmente, **scegliere Trasforma tutti i** modelli dal menu Compila. 

Se è stato installato Visual Studio Modeling SDK, è possibile trasformare automaticamente tutti i modelli ogni volta che si esegue una compilazione. A tale scopo, modificare il file di progetto (con estensione csproj o vbproj) in un editor di testo e quindi aggiungere le righe seguenti vicino alla fine del file, dopo eventuali altre istruzioni `<import>`:

> [!NOTE]
> Text Template Transformation SDK e Visual Studio Modeling SDK vengono installati automaticamente quando si installano funzionalità specifiche di Visual Studio. Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Per altre informazioni, vedere [Generazione di codice in un processo di compilazione.](../modeling/code-generation-in-a-build-process.md)

## <a name="error-reporting"></a>Errore di segnalazione

Per inserire messaggi di errore e di avviso nella Visual Studio di errore, è possibile usare questi metodi:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Conversione di un file esistente in un modello

Una funzionalità utile dei modelli consiste nel fatto che il loro aspetto è molto simile a quello dei file generati, anche se includono codice programma. Ciò suggerisce un metodo utile per la creazione di un modello. Creare innanzitutto un file comune come prototipo, ad esempio un file, e quindi introdurre gradualmente codice di generazione [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] che varia il file risultante.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Per convertire un file esistente in un modello in fase di esecuzione

1. Al progetto Visual Studio, aggiungere un file del tipo che si vuole generare, ad esempio `.cs` un file , o `.vb` `.resx` .

2. Testare il nuovo file per assicurarsi che funzioni correttamente.

3. In Esplora soluzioni modificare l'estensione del nome file in **.tt**.

4. Verificare le proprietà seguenti del file **con estensione tt:**

   |Proprietà |Impostazione |
   |-|-|
   | **Strumento personalizzato =** | **TextTemplatingFileGenerator** |
   | **Operazione di compilazione =** | **Nessuno** |

5. Inserire le righe seguenti all'inizio del file:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Per scrivere il codice di generazione del modello in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], impostare l'attributo `language` su `"VB"` invece che su `"C#"`.

    Impostare l'attributo `extension` sull'estensione del nome file per il tipo di file che si vuole generare, ad esempio `.cs`, `.resx` o `.xml`.

6. Salvare il file.

    Sarà creato un file secondario, con l'estensione specificata. Le relative proprietà sono corrette per il tipo di file. Ad esempio, la **proprietà Azione di** compilazione di un file con estensione cs sarà **Compila**.

    Verificare che il file generato includa lo stesso contenuto del file originale.

7. Identificare una parte del file da variare. Ad esempio, una parte visualizzata solo in determinate condizioni o una parte ripetuta o che include valori variabili specifici. Inserire codice di generazione. Salvare il file e verificare che il file secondario sia stato generato correttamente. Ripetere questo passaggio.

## <a name="guidelines-for-code-generation"></a>Linee guida per la generazione di codice

Vedere Linee [guida per la scrittura di modelli di testo T4.](../modeling/guidelines-for-writing-t4-text-templates.md)

## <a name="next-steps"></a>Passaggi successivi

|Passaggio successivo|Argomento|
|-|-|
|Scrivere un modello di testo più avanzato, con codice che usa funzioni ausiliarie, file inclusi e dati esterni, ed eseguirne il debug.|[Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)|
|Generare documenti dai modelli in fase di esecuzione.|[Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Eseguire la generazione di testo al di fuori Visual Studio.|[Generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Trasformare i dati nel formato di un linguaggio specifico di dominio.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Vedi anche

- [Linee guida per la scrittura di modelli di testo T4](../modeling/guidelines-for-writing-t4-text-templates.md)
