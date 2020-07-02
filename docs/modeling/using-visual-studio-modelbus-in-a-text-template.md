---
title: Usare ModelBus in un modello di testo
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a6c9cb035637347ffd501b5cf3b1038cd09369
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535941"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Utilizzo di ModelBus di Visual Studio in un modello di testo

Se si scrivono modelli di testo che leggono un modello contenente Visual Studio ModelBus riferimenti, potrebbe essere necessario risolvere i riferimenti per accedere ai modelli di destinazione. In tal caso, è necessario adattare i modelli di testo e i linguaggi specifici di dominio (DSLs) a cui viene fatto riferimento:

- Il DSL che rappresenta la destinazione dei riferimenti deve disporre di un adattatore ModelBus configurato per l'accesso da modelli di testo. Se si accede anche al linguaggio DSL da altro codice, l'adattatore riconfigurato è necessario oltre all'adapter ModelBus standard.

     Il gestore dell'adapter deve ereditare da [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) e deve avere l'attributo `[HostSpecific(HostName)]` .

- Il modello deve ereditare da [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Se si desidera leggere modelli DSL che non contengono riferimenti a ModelBus, è possibile utilizzare i processori di direttiva generati nei progetti DSL. Per altre informazioni, vedere [accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).

Per ulteriori informazioni sui modelli di testo, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Creare una scheda bus di modello per l'accesso da modelli di testo

Per risolvere un riferimento ModelBus in un modello di testo, è necessario che il linguaggio DSL di destinazione disponga di un adattatore compatibile. I modelli di testo vengono eseguiti in un AppDomain separato dagli editor di documenti di Visual Studio, pertanto l'adapter deve caricare il modello anziché accedervi tramite DTE.

1. Se la soluzione DSL di destinazione non dispone di un progetto **ModelBusAdapter** , crearne uno usando la procedura guidata di estensione ModelBus:

    1. Scaricare e installare l'estensione Visual Studio ModelBus, se non è già stato fatto. Per altre informazioni, vedere [SDK di visualizzazione e modellazione](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Aprire il file di definizione del linguaggio specifico di dominio. Fare clic con il pulsante destro del mouse sull'area di progettazione e quindi scegliere **Abilita ModelBus**.

    3. Nella finestra di dialogo selezionare si **desidera esporre questo DSL al ModelBus**. È possibile selezionare entrambe le opzioni se si desidera che questo DSL esponga i propri modelli e utilizzi riferimenti ad altri DSLs.

    4. Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" verrà aggiunto alla soluzione relativa al linguaggio specifico di dominio.

    5. Fare clic su **trasforma tutti i modelli**.

    6. Ricompilare la soluzione.

2. Se si vuole accedere al linguaggio DSL da un modello di testo e da altro codice, ad esempio Command, duplicare il progetto **ModelBusAdapter** :

    1. In Esplora risorse copiare e incollare la cartella che contiene **ModelBusAdapter. csproj**.

    2. Rinominare il file di progetto (ad esempio, in **T4ModelBusAdapter. csproj**).

    3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**. Individuare il nuovo progetto di adapter, **T4ModelBusAdapter. csproj**.

    4. In ogni `*.tt` file del nuovo progetto modificare lo spazio dei nomi.

    5. Fare clic con il pulsante destro del mouse sul nuovo progetto in **Esplora soluzioni** , quindi scegliere **Proprietà**. Nell'editor delle proprietà modificare i nomi dell'assembly generato e dello spazio dei nomi predefinito.

    6. Nel progetto DslPackage aggiungere un riferimento al nuovo progetto di adapter in modo che includa riferimenti a entrambi gli adapter.

    7. In DslPackage source.Extension.tt aggiungere una riga che fa riferimento al nuovo progetto di adapter.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Trasformare tutti i modelli** e ricompilare la soluzione. Non devono verificarsi errori di compilazione.

3. Nel nuovo progetto di adapter aggiungere riferimenti agli assembly seguenti:

    - Microsoft. VisualStudio. TextTemplating. 11.0
    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

4. In AdapterManager.tt:

    - Modificare la dichiarazione di AdapterManagerBase in modo che erediti da [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - In prossimità della fine del file, sostituire l'attributo HostSpecific prima della classe AdapterManager. Rimuovere la riga seguente:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserire la riga seguente:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Questo attributo filtra il set di adapter disponibili quando un consumer ModelBus Cerca un adapter.

5. **Trasformare tutti i modelli** e ricompilare la soluzione. Non devono verificarsi errori di compilazione.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Scrivere un modello di testo in grado di risolvere i riferimenti ModelBus

Si inizia in genere con un modello che legge e genera file da un linguaggio DSL "di origine". Questo modello usa la direttiva generata nel progetto DSL di origine per leggere i file del modello di origine nel modo descritto in [accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md). Tuttavia, il linguaggio DSL di origine contiene riferimenti ModelBus a un linguaggio DSL di destinazione. Si desidera quindi abilitare il codice del modello per risolvere i riferimenti e accedere al linguaggio DSL di destinazione. È pertanto necessario adattare il modello attenendosi alla procedura seguente:

- Modificare la classe di base del modello in [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Includere `hostspecific="true"` nella direttiva template.

- Aggiungere riferimenti ad assembly al linguaggio DSL di destinazione e alla relativa scheda e per abilitare ModelBus.

- Non è necessaria la direttiva generata come parte del linguaggio DSL di destinazione.

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

 Quando questo modello di testo viene eseguito, la `SourceDsl` direttiva carica il file `Sample.source` . Il modello può accedere agli elementi del modello, a partire da `this.ModelRoot` . Il codice può usare le classi di dominio e le proprietà di tale DSL.

 Inoltre, il modello può risolvere i riferimenti ModelBus. Quando i riferimenti puntano al modello di destinazione, le direttive di assembly consentono al codice di usare le classi e le proprietà del dominio DSL del modello.

- Se non si utilizza una direttiva generata da un progetto DSL, è necessario includere anche quanto segue.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Utilizzare `this.ModelBus` per ottenere l'accesso al ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Procedura dettagliata: test di un modello di testo che usa ModelBus
 In questa procedura dettagliata si seguono i passaggi seguenti:

1. Costruire due DSLs. Un DSL, il *consumer*, ha una `ModelBusReference` proprietà che può fare riferimento all'altro DSL, il *provider*.

2. Creare due schede ModelBus nel provider: una per l'accesso tramite modelli di testo, l'altra per il codice ordinario.

3. Creazione di modelli di istanza di DSLs in un singolo progetto sperimentale.

4. Impostare una proprietà di dominio in un modello in modo che punti all'altro modello.

5. Scrivere un gestore di doppio clic che apre il modello a cui si fa riferimento.

6. Scrivere un modello di testo in grado di caricare il primo modello, seguire il riferimento all'altro modello e leggere l'altro modello.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Costruire un linguaggio DSL accessibile a ModelBus

1. Creare una nuova soluzione DSL. Per questo esempio, selezionare il modello di soluzione flusso attività. Impostare il nome della lingua su `MBProvider` e l'estensione del nome di file su ". provide".

2. Nel diagramma di definizione DSL, fare clic con il pulsante destro del mouse su una parte vuota del diagramma che non si trova nella parte superiore, quindi fare clic su **Abilita ModelBus**.

   Se non viene visualizzato **Abilita ModelBus**, scaricare e installare l'estensione ModelBus VMSDK.

3. Nella finestra di dialogo **Abilita ModelBus** selezionare **esporre questo DSL al ModelBus**, quindi fare clic su **OK**.

    Un nuovo progetto, `ModelBusAdapter` , viene aggiunto alla soluzione.

È ora disponibile un linguaggio DSL a cui è possibile accedere tramite modelli di testo tramite ModelBus. I riferimenti a esso possono essere risolti nel codice di comandi, gestori eventi o regole, tutti che operano nell'AppDomain dell'editor dei file di modello. Tuttavia, i modelli di testo vengono eseguiti in un AppDomain separato e non possono accedere a un modello durante la modifica. Se si desidera accedere ai riferimenti ModelBus a questo DSL da un modello di testo, è necessario disporre di un ModelBusAdapter separato.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Creare un adapter ModelBus configurato per i modelli di testo

1. In Esplora file copiare e incollare la cartella che contiene *ModelBusAdapter. csproj*.

    Denominare la cartella **T4ModelBusAdapter**.

    Rinominare il file di progetto *T4ModelBusAdapter. csproj*.

2. In Esplora soluzioni aggiungere T4ModelBusAdapter alla soluzione MBProvider. Fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**.

3. Fare clic con il pulsante destro del mouse sul nodo del progetto T4ModelBusAdapter, quindi scegliere Proprietà. Nella finestra Proprietà progetto modificare il nome dell' **assembly** e **lo spazio dei nomi predefinito** in `Company.MBProvider.T4ModelBusAdapters` .

4. In ogni file *. TT in T4ModelBusAdapter inserire "T4" nell'ultima parte dello spazio dei nomi, in modo che la riga sia simile a quella riportata di seguito.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. Nel `DslPackage` progetto aggiungere un riferimento al progetto `T4ModelBusAdapter` .

6. In DslPackage source.Extension.tt aggiungere la riga seguente sotto `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Nel `T4ModelBusAdapter` progetto aggiungere un riferimento a: **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**

8. Apri T4ModelBusAdapter\AdapterManager.tt:

   1. Modificare la classe di base di AdapterManagerBase in [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Questa parte del file è ora simile alla seguente.

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

   2. Alla fine del file, inserire l'attributo aggiuntivo seguente davanti alla classe AdapterManager.

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

9. Fare clic su **trasforma tutti i modelli** nella barra del titolo di Esplora soluzioni.

10. Premere **F5**.

11. Verificare che il linguaggio DSL funzioni correttamente. Nel progetto sperimentale aprire `Sample.provider` . Chiudere l'istanza sperimentale di Visual Studio.

    I riferimenti ModelBus a questo DSL possono ora essere risolti in modelli di testo e anche nel codice normale.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Costruire un linguaggio DSL con una proprietà di dominio di riferimento ModelBus

1. Creare un nuovo linguaggio DSL usando il modello di soluzione per il linguaggio minimo. Assegnare al linguaggio il nome MBConsumer e impostare l'estensione del nome file su ". consume".

2. Nel progetto DSL aggiungere un riferimento all'assembly DSL MBProvider. Fare clic con il pulsante destro del mouse `MBConsumer\Dsl\References` e scegliere **Aggiungi riferimento**. Nella scheda **Sfoglia** individuare`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    In questo modo è possibile creare codice che usa l'altro DSL. Se si desidera creare riferimenti a diversi DSLs, aggiungerli anche.

3. Nel diagramma di definizione DSL fare clic con il pulsante destro del mouse sul diagramma e quindi scegliere **Abilita ModelBus**. Nella finestra di dialogo selezionare **Abilita questo DSL per utilizzare ModelBus**.

4. Nella classe `ExampleElement` aggiungere una nuova proprietà `MBR` del dominio e, nel finestra Proprietà, impostarne il tipo su `ModelBusReference` .

5. Fare clic con il pulsante destro del mouse sulla proprietà Domain del diagramma, quindi scegliere **modifica proprietà specifiche di ModelBusReference**. Nella finestra di dialogo selezionare **un elemento del modello**.

    Impostare il filtro della finestra di dialogo file su quanto segue.

    `Provider File|*.provide`

    La sottostringa dopo "&#124;" è un filtro per la finestra di dialogo di selezione file. È possibile impostarlo in modo da consentire qualsiasi file utilizzando *.\*

    Nell'elenco **tipo di elemento del modello** , immettere i nomi di una o più classi di dominio nel DSL del provider (ad esempio, Company. MBProvider. Task). Possono essere classi astratte. Se si lascia vuoto l'elenco, l'utente può impostare il riferimento a qualsiasi elemento.

6. Chiudere la finestra di dialogo e **trasformare tutti i modelli**.

   È stato creato un linguaggio DSL che può contenere riferimenti a elementi in un altro DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Creare un riferimento ModelBus a un altro file nella soluzione

1. Nella soluzione MBConsumer, premere CTRL + F5. Nel progetto **MBConsumer\Debugging** verrà aperta un'istanza sperimentale di Visual Studio.

2. Aggiungere una copia di Sample. fornire al progetto **MBConsumer\Debugging** . Questa operazione è necessaria perché un riferimento ModelBus deve fare riferimento a un file nella stessa soluzione.

   1. Fare clic con il pulsante destro del mouse sul progetto di debug, scegliere **Aggiungi**, quindi fare clic su **elemento esistente**.

   2. Nella finestra di dialogo **Aggiungi elemento** impostare il filtro su **tutti i file ( \* . \* )**.

   3. Passare a `MBProvider\Debugging\Sample.provide` e quindi fare clic su **Aggiungi**.

3. Aprire `Sample.consume`.

4. Fare clic su una forma di esempio e nella finestra Proprietà fare clic su **[...]** nella proprietà MBR. Nella finestra di dialogo fare clic su **Sfoglia** e selezionare `Sample.provide` . Nella finestra elementi espandere l'attività tipo e selezionare uno degli elementi.

5. Salvare il file. Non chiudere ancora l'istanza sperimentale di Visual Studio.

   È stato creato un modello che contiene un riferimento ModelBus a un elemento in un altro modello.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Risolvere un riferimento ModelBus in un modello di testo

1. Nell'istanza sperimentale di Visual Studio aprire un file di modello di testo di esempio. Impostarne il contenuto come segue.

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

    - `hostSpecific` `inherits` È necessario impostare gli attributi e della `template` direttiva.

    - È possibile accedere al modello consumer nel modo consueto tramite il processore di direttiva generato in tale DSL.

    - Le direttive assembly e Import devono essere in grado di accedere a ModelBus e ai tipi del DSL del provider.

    - Se si è certi che molti MBR sono collegati allo stesso modello, è preferibile chiamare CreateAdapter solo una volta.

2. Salvare il modello. Verificare che il file di testo risultante sia simile al seguente.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Risolvere un riferimento ModelBus in un gestore movimenti

1. Chiudere l'istanza sperimentale di Visual Studio, se è in esecuzione.

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

## <a name="see-also"></a>Vedere anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
