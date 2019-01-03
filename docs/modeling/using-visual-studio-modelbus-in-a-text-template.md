---
title: Usare ModelBus in un modello di testo
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 69884d3dd52f2aaab04dac8f32f18d286f5929af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828238"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilizzo di ModelBus di Visual Studio in un modello di testo
Se si scrivono modelli di testo che leggono un modello che contiene i riferimenti ModelBus di Visual Studio, è possibile risolvere i riferimenti per accedere ai modelli di destinazione. In tal caso, è necessario adattare i modelli di testo e i riferimento linguaggi specifici di dominio (DSL):

-   Il linguaggio DSL di destinazione dei riferimenti è necessario un adattatore ModelBus configurato per l'accesso dai modelli di testo. Se inoltre si accede il linguaggio DSL da altro codice, l'adapter la riconfigurazione è necessario oltre all'adattatore ModelBus standard.

     Il gestore di adattatori deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> e deve avere l'attributo `[HostSpecific(HostName)]`.

-   Il modello deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

> [!NOTE]
>  Se si desidera leggere i modelli di linguaggio specifico di dominio che non contengono riferimenti ModelBus, è possibile usare processori di direttive che vengono generati nei progetti DSL. Per altre informazioni, vedere [l'accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).

 Per altre informazioni sui modelli di testo, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Creazione di un adattatore ModelBus per l'accesso dai modelli di testo
 Per risolvere un riferimento ModelBus in un modello di testo, il linguaggio DSL di destinazione deve avere una scheda compatibile. Eseguire i modelli di testo in un AppDomain separato dall'editor di documento di Visual Studio, e pertanto l'adapter deve caricare il modello anziché accedervi tramite DTE.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Per creare un adattatore ModelBus è compatibile con i modelli di testo

1.  Se la soluzione DSL di destinazione non dispone di un **ModelBusAdapter** del progetto, crearne uno tramite la procedura guidata estensione Modelbus:

    1.  Scaricare e installare l'estensione di ModelBus di Visual Studio, se non è stato già fatto. Per altre informazioni, vedere [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  Aprire il file di definizione del linguaggio specifico di dominio. Fare doppio clic nell'area di progettazione e quindi fare clic su **Abilita Modelbus**.

    3.  Nella finestra di dialogo, selezionare **desidero esporre questo DSL a ModelBus**. È possibile selezionare entrambe le opzioni se si desidera che questo linguaggio specifico di dominio esponga i propri modelli e usi riferimenti ad altri modelli.

    4.  Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" verrà aggiunto alla soluzione relativa al linguaggio specifico di dominio.

    5.  Fare clic su **Trasforma tutti i modelli**.

    6.  Ricompilare la soluzione.

2.  Se si desidera accedere DSL da un modello di testo e da altro codice, ad esempio di comando, duplicare il **ModelBusAdapter** progetto:

    1.  In Windows Explorer, copiare e incollare la cartella che contiene **ModelBusAdapter.csproj**.

    2.  Rinominare il file di progetto (ad esempio, per **T4ModelBusAdapter.csproj**).

    3.  Nella **Esplora soluzioni**, fare doppio clic sul nodo della soluzione, scegliere **Add**, quindi fare clic su **progetto esistente**. Individuare il nuovo progetto di adattatore **T4ModelBusAdapter.csproj**.

    4.  In ogni `*.tt` file del nuovo progetto, modificare lo spazio dei nomi.

    5.  Fare doppio clic su Nuovo progetto in Esplora soluzioni e quindi fare clic su proprietà. Nell'editor delle proprietà, modificare i nomi di assembly generato e lo spazio dei nomi predefinito.

    6.  Nel progetto DslPackage, aggiungere un riferimento al nuovo progetto di adapter in modo che includa i riferimenti a entrambe le schede.

    7.  In DslPackage\source.extension.tt, aggiungere una linea che fa riferimento il nuovo progetto di adapter.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8.  **Trasforma tutti i modelli** e ricompilare la soluzione. Non dovrebbero verificarsi alcun errore di compilazione.

3.  Nel nuovo progetto di adapter, aggiungere i riferimenti agli assembly seguenti:

    -   Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4.  Nel file AdapterManager.tt:

    -   Modificare la dichiarazione di adaptermanagerbase e impostarla in modo che erediti da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    -   Verso la fine del file, sostituire l'attributo HostSpecific prima della classe AdapterManager. Rimuovere la riga seguente:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserire la riga seguente:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Questo attributo filtra il set di adattatori che è disponibile quando si esegue la ricerca per un adattatore di un consumer di modelbus.

5.  **Trasforma tutti i modelli** e ricompilare la soluzione. Non dovrebbero verificarsi alcun errore di compilazione.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Scrittura di un modello di testo che può risolvere i riferimenti ModelBus
 In genere, si inizia con un modello che legge e genera i file da un linguaggio DSL di "origine". Questo modello Usa la direttiva generata nel progetto DSL di origine per leggere i file di modello di origine nel modo descritto nella [l'accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md). Tuttavia, il linguaggio DSL di origine contiene un riferimento ModelBus a un DSL "target". Pertanto si desidera abilitare il codice del modello risolvere i riferimenti e accedere al linguaggio DSL di destinazione. È pertanto necessario adattare il modello seguendo questa procedura:

-   Modificare la classe di base del modello da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

-   Includere `hostspecific="true"` nella direttiva del modello.

-   Aggiungere riferimenti ad assembly per il linguaggio DSL di destinazione e sul relativo adattatore e abilitare ModelBus.

-   Non è necessaria la direttiva che viene generata come parte del linguaggio DSL di destinazione.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Quando viene eseguito questo modello di testo, il `SourceDsl` direttiva carica il file `Sample.source`. Il modello può accedere agli elementi del modello, a partire da `this.ModelRoot`. Il codice può usare le classi di dominio e le proprietà di tale linguaggio DSL.

 Inoltre, il modello può risolvere i riferimenti ModelBus. In cui i riferimenti puntano al modello di destinazione, le direttive dell'assembly lasciare che il codice usare le classi di dominio e le proprietà del DSL del modello.

-   Se non si utilizza una direttiva che viene generata da un progetto DSL, è necessario anche includere quanto segue.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

-   Usare `this.ModelBus` per ottenere l'accesso a ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procedura dettagliata: Test di un modello di testo che utilizza ModelBus
 In questa procedura dettagliata seguire questi passaggi:

1.  Creare due linguaggi specifici di dominio. Un linguaggio DSL, il *Consumer*, ha una `ModelBusReference` proprietà che possono fare riferimento all'altro linguaggio specifico di dominio, il *Provider*.

2.  Creare due adattatori ModelBus nel Provider: uno per l'accesso dai modelli di testo, l'altro per il codice normale.

3.  Creare modelli di istanza di DSL in un unico progetto sperimentale.

4.  Impostare una proprietà di dominio in un modello in modo che punti all'altro modello.

5.  Scrivere un gestore di doppio clic che si apre il modello che fa riferimento.

6.  Scrivere un modello di testo che può caricare il primo modello, seguire il riferimento all'altro modello e l'altro modello di lettura.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Creare un linguaggio DSL è accessibile da ModelBus

1. Creare una nuova soluzione DSL. Per questo esempio, selezionare il modello di soluzione flusso attività. Impostare il nome della lingua su `MBProvider` e l'estensione del nome file ".provide".

2. Nel diagramma di definizione DSL, fare doppio clic su una parte vuota del diagramma che non è presente nella parte superiore e quindi fare clic su **Abilita Modelbus**.

   -   Se non viene visualizzata **Abilita Modelbus**, è necessario scaricare e installare l'estensione ModelBus VMSDK. Cercala su sito VMSDK: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

3. Nel **Abilita Modelbus** finestra di dialogo **Esponi questo DSL a ModelBus**, quindi fare clic su **OK**.

    Un nuovo progetto, `ModelBusAdapter`, viene aggiunto alla soluzione.

   È ora disponibile un linguaggio DSL è accessibile da modelli di testo tramite ModelBus. Riferimenti a esso possono essere risolti nel codice di comandi, i gestori eventi o le regole, che operano nel dominio applicazione dell'editor di file di modello. Tuttavia, i modelli di testo eseguite in un AppDomain separato e non possono accedere a un modello quando viene modificato. Se si desidera accedere a un riferimento ModelBus a questo linguaggio DSL da un modello di testo, è necessario disporre di un oggetto ModelBusAdapter separato.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Per creare un adattatore ModelBus configurato per i modelli di testo

1. In Windows Explorer, copiare e incollare la cartella che contiene ModelBusAdapter.csproj.

    Denominare la cartella T4ModelBusAdapter.

    Rinominare il file di progetto T4ModelBusAdapter.csproj.

2. In Esplora soluzioni aggiungere T4ModelBusAdapter alla soluzione MBProvider. Pulsante destro del mouse sul nodo della soluzione, scegliere **Add**, quindi fare clic su **progetto esistente**.

3. Fare doppio clic sul nodo del progetto T4ModelBusAdapter e quindi fare clic su proprietà. Nella finestra delle proprietà del progetto, modificare il **nome dell'Assembly** e **Namespace predefinito** a `Company.MBProvider.T4ModelBusAdapters`.

4. In ogni file tt T4ModelBusAdapter, inserire "T4" l'ultima parte dello spazio dei nomi, in modo che la riga è simile al seguente.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. Nel `DslPackage` del progetto, aggiungere un riferimento al progetto `T4ModelBusAdapter`.

6. In DslPackage\source.extension.tt, aggiungere la riga seguente sotto `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Nel `T4ModelBusAdapter` del progetto, aggiungere un riferimento a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Aprire T4ModelBusAdapter\AdapterManager.tt:

   1.  Modificare la classe di base di AdapterManagerBase e impostarla su <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Questa parte del file è ora simile alla seguente.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {

       ```

   2.  Verso la fine del file, inserire il seguente attributo aggiuntivo davanti alla classe AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Il risultato è simile al seguente.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }

       ```

9. Fare clic su **Trasforma tutti i modelli** nella barra del titolo della soluzione Esplora.

10. Ricompilare la soluzione. Premere F5.

11. Verificare che il linguaggio DSL funzioni premendo F5. Nel progetto sperimentale aprire `Sample.provider`. Chiudere l'istanza sperimentale di Visual Studio.

    Riferimenti ModelBus per questo DSL ora possono essere risolti nei modelli di testo e anche nel codice normale.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Creare un linguaggio DSL con una proprietà di dominio di riferimento ModelBus

1. Creare un nuovo linguaggio specifico di dominio usando il modello di soluzione di linguaggio minimo. Denominare il linguaggio MBConsumer e impostare l'estensione del nome file ".consume".

2. Nel progetto DSL, aggiungere un riferimento all'assembly MBProvider DSL. Fare doppio clic su `MBConsumer\Dsl\References` e quindi fare clic su **Aggiungi riferimento**. Nel **Sfoglia** , individuare `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    In questo modo è possibile creare codice che usa il linguaggio specifico di dominio. Se si desidera creare riferimenti a linguaggi specifici di dominio diversi, aggiungerli anche.

3. Nel diagramma di definizione DSL, pulsante destro del mouse nel diagramma e quindi fare clic su **Abilita ModelBus**. Nella finestra di dialogo, selezionare **abilita questo DSL per l'uso di ModelBus**.

4. Nella classe `ExampleElement`, aggiungere una nuova proprietà di dominio `MBR`e nella finestra Proprietà impostare il relativo tipo su `ModelBusReference`.

5. Fare doppio clic su proprietà di dominio sul diagramma e quindi fare clic su **proprietà specifiche di ModelBusReference modifica**. Nella finestra di dialogo, selezionare **un elemento del modello**.

    Impostare il filtro di file come segue.

    `Provider File|*.provide`

    La sottostringa dopo "&#124;" è un filtro per la finestra di dialogo Selezione file. È possibile impostarlo per consentire tutti i file utilizzando *.\*

    Nel **tipo di elemento del modello** elenco, immettere i nomi di uno o dominio altre classi nel provider del linguaggio specifico di dominio (ad esempio, Company.MBProvider.Task). Possono essere classi astratte. Se si omette l'elenco, l'utente può impostare il riferimento a qualsiasi elemento.

6. Chiudere la finestra di dialogo e **Trasforma tutti i modelli**.

   È stato creato un modello DSL che possono contenere riferimenti a elementi in un altro linguaggio specifico di dominio.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Creare un riferimento ModelBus a un altro file nella soluzione

1. Nella soluzione MBConsumer, premere CTRL+F5. Un'istanza sperimentale di Visual Studio viene aperto nel **MBConsumer\Debugging** progetto.

2. Aggiungere una copia di Sample.provide per il **MBConsumer\Debugging** progetto. Ciò è necessario perché un riferimento ModelBus deve fare riferimento a un file nella stessa soluzione.

   1.  Fare clic sul progetto di debug, scegliere **Add**, quindi fare clic su **elemento esistente**.

   2.  Nel **Aggiungi elemento** finestra di dialogo, impostare il filtro **tutti i file (\*.\*)** .

   3.  Passare a `MBProvider\Debugging\Sample.provide` e quindi fare clic su **Add**.

3. Aprire `Sample.consume`.

4. Fare clic su una forma di esempio e nella finestra Proprietà, fare clic su **[...]**  nella proprietà MBR. Nella finestra di dialogo, fare clic su **esplorare** e selezionare `Sample.provide`. Nella finestra di elementi, espandere il tipo di attività e selezionare uno degli elementi.

5. Salvare il file.

    (Non ancora chiudere l'istanza sperimentale di Visual Studio.)

   È stato creato un modello che contiene un riferimento ModelBus a un elemento in un altro modello.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Risolvere un riferimento ModelBus in un modello di testo

1.  Nell'istanza sperimentale di Visual Studio, aprire un file di modello di testo di esempio. Impostarne il contenuto come indicato di seguito.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     È importante tenere presente i punti seguenti:

    1.  Il `hostSpecific` e `inherits` attributi del `template` direttiva deve essere impostata.

    2.  Il modello di consumer è accessibile nel modo usuale tramite il processore di direttiva generato in tale linguaggio DSL.

    3.  Le direttive di importazione e l'assembly devono essere in grado di accedere a ModelBus e i tipi di provider di DSL.

    4.  Se si conoscono gli MBR molte sono collegati allo stesso modello, è preferibile chiamare CreateAdapter solo una volta.

2.  Salvare il modello. Verificare che il file di testo risultante sarà simile al seguente.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Risolvere un riferimento ModelBus in un gestore movimenti

1.  Chiudere l'istanza sperimentale di Visual Studio, se è in esecuzione.

2.  Aggiungere un file denominato MBConsumer\Dsl\Custom.cs e impostarne il contenuto al seguente.

    ```

    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }

    ```

3.  Premere CTRL+F5.

4.  Nell'istanza sperimentale di Visual Studio, aprire `Debugging\Sample.consume`.

5.  Fare doppio clic su una forma.

     Se è stato impostato il MBR in quell'elemento, viene aperto il modello di cui viene fatto riferimento e si seleziona l'elemento cui si fa riferimento.

## <a name="see-also"></a>Vedere anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
