---
title: Usare ModelBus in un modello di testo
description: Informazioni su come risolvere i riferimenti per accedere ai modelli di destinazione se si scrivono modelli di testo che leggono un modello che Visual Studio riferimenti a ModelBus.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 40c4b9abdef57012e2bdd59b1f3a4e86ac9a05668fc4c53b5da2f8a655baff1c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231340"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilizzo di ModelBus di Visual Studio in un modello di testo

Se si scrivono modelli di testo che leggono un modello che contiene riferimenti Visual Studio ModelBus, è possibile risolvere i riferimenti per accedere ai modelli di destinazione. In tal caso, è necessario adattare i modelli di testo e le lingue specifiche del dominio (DSL) a cui si fa riferimento:

- Il DSL che è la destinazione dei riferimenti deve avere un adattatore ModelBus configurato per l'accesso dai modelli di testo. Se si accede anche a DSL da altro codice, l'adapter riconfigurato è necessario oltre all'adapter ModelBus standard.

     Il gestore dell'adapter deve ereditare [da VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) e deve avere l'attributo `[HostSpecific(HostName)]` .

- Il modello deve ereditare da [ModelBusEnabledTextTransformation.](/previous-versions/ee844263(v=vs.140))

> [!NOTE]
> Per leggere i modelli DSL che non contengono riferimenti ModelBus, è possibile usare i processori di direttiva generati nei progetti DSL. Per altre informazioni, vedere [Accesso ai modelli da modelli di testo.](../modeling/accessing-models-from-text-templates.md)

Per altre informazioni sui modelli di testo, vedere Generazione di codice in fase di [progettazione tramite modelli di testo T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Creare un adattatore bus di modello per l'accesso da modelli di testo

Per risolvere un riferimento a ModelBus in un modello di testo, il DSL di destinazione deve avere un adattatore compatibile. I modelli di testo vengono eseguiti in un AppDomain separato dagli editor di documenti Visual Studio e pertanto l'adapter deve caricare il modello anziché accedervi tramite DTE.

1. Se la soluzione DSL di destinazione non ha un **progetto ModelBusAdapter,** crearne uno usando la procedura guidata dell'estensione Modelbus:

    1. Scaricare e installare l'Visual Studio ModelBus, se non è già stato fatto. Per altre informazioni, vedere [Visualization and Modeling SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Aprire il file di definizione del linguaggio specifico di dominio. Fare clic con il pulsante destro del mouse sull'area di progettazione e **quindi scegliere Abilita Modelbus**.

    3. Nella finestra di dialogo selezionare **I want to expose this DSL to the ModelBus**. È possibile selezionare entrambe le opzioni se si vuole che questa DSL esponga i relativi modelli e per utilizzare i riferimenti ad altre DSL.

    4. Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" verrà aggiunto alla soluzione relativa al linguaggio specifico di dominio.

    5. Fare **clic su Trasforma tutti i modelli**.

    6. Ricompilare la soluzione.

2. Se si vuole accedere al DSL sia da un modello di testo che da altro codice, ad esempio il comando , duplicare il **progetto ModelBusAdapter:**

    1. In Windows Explorer copiare e incollare la cartella che contiene **ModelBusAdapter.csproj.**

    2. Rinominare il file di progetto ( ad esempio, **in T4ModelBusAdapter.csproj**).

    3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere Aggiungi e quindi fare clic su **Project**.  Individuare il nuovo progetto **adapter, T4ModelBusAdapter.csproj.**

    4. In ogni `*.tt` file del nuovo progetto modificare lo spazio dei nomi .

    5. Fare clic con il pulsante destro del mouse sul **nuovo progetto** Esplora soluzioni quindi scegliere **Proprietà**. Nell'editor delle proprietà modificare i nomi dell'assembly generato e lo spazio dei nomi predefinito.

    6. Nel progetto DslPackage aggiungere un riferimento al nuovo progetto adapter in modo che abbia riferimenti a entrambi gli adapter.

    7. In DslPackage\source.extension.tt aggiungere una riga che faccia riferimento al nuovo progetto adapter.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Trasformare tutti i modelli** e ricompilare la soluzione. Non devono verificarsi errori di compilazione.

3. Nel nuovo progetto adapter aggiungere riferimenti agli assembly seguenti:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. In AdapterManager.tt:

    - Modificare la dichiarazione di AdapterManagerBase in modo che erediti da [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Alla fine del file sostituire l'attributo HostSpecific prima della classe AdapterManager. Rimuovere la riga seguente:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserire la riga seguente:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Questo attributo filtra il set di adattatori disponibile quando un consumer modelbus cerca un adapter.

5. **Trasformare tutti i modelli** e ricompilare la soluzione. Non devono verificarsi errori di compilazione.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Scrivere un modello di testo in grado di risolvere i riferimenti modelbus

In genere, si inizia con un modello che legge e genera file da un DSL "di origine". Questo modello usa la direttiva generata nel progetto DSL di origine per leggere i file del modello di origine nel modo descritto in Accesso ai modelli da modelli [di testo](../modeling/accessing-models-from-text-templates.md). Tuttavia, il DSL di origine contiene riferimenti ModelBus a un DSL di "destinazione". Si vuole quindi abilitare il codice del modello per risolvere i riferimenti e accedere al DSL di destinazione. È pertanto necessario adattare il modello seguendo questa procedura:

- Modificare la classe di base del modello in [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Includere `hostspecific="true"` nella direttiva del modello.

- Aggiungere riferimenti ad assembly al DSL di destinazione e al relativo adapter e per abilitare ModelBus.

- Non è necessaria la direttiva generata come parte del DSL di destinazione.

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

 Quando viene eseguito questo modello di testo, `SourceDsl` la direttiva carica il file `Sample.source` . Il modello può accedere agli elementi del modello, a partire da `this.ModelRoot` . Il codice può usare le classi di dominio e le proprietà di tale DSL.

 Inoltre, il modello può risolvere i riferimenti ModelBus. Dove i riferimenti puntano al modello di destinazione, le direttive assembly consentono al codice di usare le classi di dominio e le proprietà del DSL del modello.

- Se non si usa una direttiva generata da un progetto DSL, è necessario includere anche quanto segue.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Usare `this.ModelBus` per ottenere l'accesso a ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procedura dettagliata: Test di un modello di testo che usa ModelBus
 In questa procedura dettagliata si segue questa procedura:

1. Costruire due DSL. Un DSL, *consumer*, dispone di una proprietà che può fare riferimento `ModelBusReference` all'altro DSL, *il provider*.

2. Creare due adattatori ModelBus nel provider: uno per l'accesso tramite modelli di testo, l'altro per il codice normale.

3. Creare modelli di istanza delle DSL in un singolo progetto sperimentale.

4. Impostare una proprietà di dominio in un modello in modo che punti all'altro modello.

5. Scrivere un gestore di doppio clic che apre il modello a cui punta.

6. Scrivere un modello di testo in grado di caricare il primo modello, seguire il riferimento all'altro modello e leggere l'altro modello.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Costruire un linguaggio DSL accessibile a ModelBus

1. Creare una nuova soluzione DSL. Per questo esempio, selezionare il modello di Flow attività. Impostare il nome della lingua su `MBProvider` e l'estensione del nome file su ".provide".

2. Nel diagramma di definizione DSL fare clic con il pulsante destro del mouse su una parte vuota del diagramma che non si trova nella parte superiore e quindi scegliere **Abilita Modelbus**.

   Se l'opzione Abilita **Modelbus** non è visualizzata, scaricare e installare l'estensione VMSDK ModelBus.

3. Nella finestra di dialogo Enable Modelbus (Abilita **Modelbus)** selezionare **Expose this DSL to the ModelBus**(Esporre questo DSL a ModelBus) e quindi fare clic su **OK.**

    Un nuovo progetto, `ModelBusAdapter` , viene aggiunto alla soluzione.

È ora disponibile un DSL accessibile dai modelli di testo tramite ModelBus. I riferimenti ad esso possono essere risolti nel codice di comandi, gestori eventi o regole, che operano tutti nell'AppDomain dell'editor di file del modello. Tuttavia, i modelli di testo vengono eseguiti in un AppDomain separato e non possono accedere a un modello in fase di modifica. Per accedere ai riferimenti ModelBus a questo DSL da un modello di testo, è necessario disporre di un oggetto ModelBusAdapter separato.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Creare un adattatore ModelBus configurato per i modelli di testo

1. In Esplora file copiare e incollare la cartella che contiene *ModelBusAdapter.csproj.*

    Assegnare alla cartella **il nome T4ModelBusAdapter**.

    Rinominare il file di *progetto T4ModelBusAdapter.csproj*.

2. In Esplora soluzioni aggiungere T4ModelBusAdapter alla soluzione MBProvider. Fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi** e quindi fare clic su **Project**.

3. Fare clic con il pulsante destro del mouse sul nodo del progetto T4ModelBusAdapter e quindi scegliere Proprietà. Nella finestra delle proprietà del progetto impostare Nome **assembly** e Spazio **dei nomi predefinito** su `Company.MBProvider.T4ModelBusAdapters` .

4. In ogni file *.tt in T4ModelBusAdapter inserire "T4" nell'ultima parte dello spazio dei nomi, in modo che la riga sia simile alla seguente.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. Nel progetto `DslPackage` aggiungere un riferimento al progetto a `T4ModelBusAdapter` .

6. In DslPackage\source.extension.tt aggiungere la riga seguente in `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Nel progetto `T4ModelBusAdapter` aggiungere un riferimento a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Aprire T4ModelBusAdapter\AdapterManager.tt:

   1. Modificare la classe base di AdapterManagerBase in [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Questa parte del file è ora simile alla seguente.

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

   2. Verso la fine del file, inserire l'attributo aggiuntivo seguente davanti alla classe AdapterManager.

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

9. Fare **clic su Trasforma tutti** i modelli nella barra del titolo Esplora soluzioni.

10. Premere **F5**.

11. Verificare che il DSL funzioni. Nel progetto sperimentale aprire `Sample.provider` . Chiudere l'istanza sperimentale di Visual Studio.

    I riferimenti ModelBus a questo DSL possono ora essere risolti nei modelli di testo e anche nel codice normale.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Costruire un linguaggio DSL con una proprietà di dominio di riferimento modelbus

1. Creare un nuovo linguaggio DSL usando il modello di soluzione Linguaggio minimo. Assegnare al linguaggio il nome MBConsumer e impostare l'estensione del nome file su ".consume".

2. Nel progetto DSL aggiungere un riferimento all'assembly DSL MBProvider. Fare clic con il pulsante `MBConsumer\Dsl\References` destro del mouse su e quindi scegliere Aggiungi **riferimento.** Nella **scheda Sfoglia** individuare `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    In questo modo è possibile creare codice che usa l'altro DSL. Se si desidera creare riferimenti a più DSL, aggiungerli anche.

3. Nel diagramma di definizione DSL fare clic con il pulsante destro del mouse sul diagramma e quindi scegliere **Abilita ModelBus.** Nella finestra di dialogo selezionare **Enable this DSL to Consume the ModelBus**.

4. Nella classe `ExampleElement` aggiungere una nuova proprietà di dominio e nella Finestra Proprietà `MBR` impostarne il tipo su `ModelBusReference` .

5. Fare clic con il pulsante destro del mouse sulla proprietà del dominio nel diagramma e quindi scegliere **Modifica proprietà specifiche modelBusReference**. Nella finestra di dialogo selezionare un **elemento del modello**.

    Impostare il filtro della finestra di dialogo file sul valore seguente.

    `Provider File|*.provide`

    La sottostringa dopo "&#124;" è un filtro per la finestra di dialogo di selezione file. È possibile impostarlo in modo da consentire qualsiasi file usando *.\*

    **Nell'elenco Tipo di** elemento modello immettere i nomi di una o più classi di dominio nel DSL del provider, ad esempio Company.MBProvider.Task. Possono essere classi astratte. Se si lascia vuoto l'elenco, l'utente può impostare il riferimento a qualsiasi elemento.

6. Chiudere la finestra di dialogo e **trasformare tutti i modelli.**

   È stato creato un DSL che può contenere riferimenti a elementi in un altro DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Creare un riferimento ModelBus a un altro file nella soluzione

1. Nella soluzione MBConsumer premere CTRL+F5. Un'istanza sperimentale Visual Studio viene aperta nel **progetto MBConsumer\Debugging.**

2. Aggiungere una copia di Sample.provide al **progetto MBConsumer\Debugging.** Ciò è necessario perché un riferimento ModelBus deve fare riferimento a un file nella stessa soluzione.

   1. Fare clic con il pulsante destro del mouse sul progetto Debug, **scegliere Aggiungi**, quindi fare clic su **Elemento esistente**.

   2. Nella finestra **di dialogo Aggiungi** elemento impostare il filtro su Tutti i file ( . **\* \* )**.

   3. Passare a `MBProvider\Debugging\Sample.provide` e quindi fare clic su **Aggiungi**.

3. Aprire `Sample.consume`.

4. Fare clic su una forma di esempio e nella Finestra Proprietà fare clic su **[...]** nella proprietà MBR. Nella finestra di dialogo fare clic **su Sfoglia** e selezionare `Sample.provide` . Nella finestra degli elementi espandere il tipo Attività e selezionare uno degli elementi.

5. Salvare il file. Non chiudere ancora l'istanza sperimentale di Visual Studio.

   È stato creato un modello che contiene un riferimento ModelBus a un elemento in un altro modello.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Risolvere un riferimento modelbus in un modello di testo

1. Nell'istanza sperimentale di Visual Studio aprire un file di modello di testo di esempio. Impostarne il contenuto come indicato di seguito.

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

    - Gli `hostSpecific` attributi e della direttiva devono essere `inherits` `template` impostati.

    - L'accesso al modello consumer avviene normalmente tramite il processore di direttiva generato in tale DSL.

    - Le direttive assembly e import devono essere in grado di accedere a ModelBus e ai tipi del DSL del provider.

    - Se si sa che molti MBR sono collegati allo stesso modello, è meglio chiamare CreateAdapter una sola volta.

2. Salvare il modello. Verificare che il file di testo risultante sia simile al seguente.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Risolvere un riferimento ModelBus in un gestore movimenti

1. Chiudere l'istanza sperimentale Visual Studio, se è in esecuzione.

2. Aggiungere un file denominato *MBConsumer\Dsl\Custom.cs* e impostarne il contenuto come segue:

    ```csharp
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

3. Premere **CTRL** + **F5**.

4. Nell'istanza sperimentale di Visual Studio aprire `Debugging\Sample.consume` .

5. Fare doppio clic su una forma.

    Se l'MBR è stato impostato su tale elemento, viene aperto il modello a cui si fa riferimento e viene selezionato l'elemento a cui si fa riferimento.

## <a name="see-also"></a>Vedi anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
