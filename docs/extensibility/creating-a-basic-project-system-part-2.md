---
title: Creazione di un Project di base, parte 2 | Microsoft Docs
description: Informazioni su come aggiungere un Visual Studio, una pagina delle proprietà e altre funzionalità a un progetto creato in un articolo precedente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 644921dac3a82da3ad618eda8787ee6866689753696268d026e73955ae286078
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452747"
---
# <a name="create-a-basic-project-system-part-2"></a>Creare un sistema di progetto di base, parte 2
La prima procedura dettagliata di questa serie, Creare un sistema di progetto di [base, parte 1,](../extensibility/creating-a-basic-project-system-part-1.md)illustra come creare un sistema di progetto di base. Questa procedura dettagliata si basa sul sistema di progetto di base aggiungendo un modello Visual Studio, una pagina delle proprietà e altre funzionalità. Prima di iniziare questa procedura dettagliata, è necessario completare la prima procedura dettagliata.

Questa procedura dettagliata illustra come creare un tipo di progetto con estensione *myproj.* Per completare la procedura dettagliata, non è necessario creare un linguaggio personalizzato perché la procedura dettagliata prende in prestito dal sistema di progetto Visual C# esistente.

Questa procedura dettagliata illustra come eseguire queste attività:

- Creare un Visual Studio modello.

- Distribuire un Visual Studio modello.

- Creare un nodo figlio di tipo progetto nella **finestra di dialogo Project** progetto .

- Abilitare la sostituzione dei parametri nel Visual Studio modello.

- Creare una pagina delle proprietà del progetto.

> [!NOTE]
> I passaggi di questa procedura dettagliata sono basati su un progetto C#. Tuttavia, ad eccezione di specifiche, ad esempio estensioni di file e codice, è possibile usare gli stessi passaggi per un Visual Basic progetto.

## <a name="create-a-visual-studio-template"></a>Creare un Visual Studio modello
- [Creare un sistema di progetto di base, la parte 1](../extensibility/creating-a-basic-project-system-part-1.md) illustra come creare un modello di progetto di base e aggiungerlo al sistema del progetto. Viene inoltre illustrato come registrare questo modello con Visual Studio usando l'attributo , che scrive il percorso completo della cartella <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> *\\ Templates\Projects\SimpleProject \\* nel Registro di sistema.

Usando un modello Visual Studio (file con estensione *vstemplate)* invece di un modello di progetto di base, è possibile controllare come viene visualizzato il modello nella finestra di dialogo Nuovo **Project** e come vengono sostituiti i parametri del modello. Un file *con estensione vstemplate* è un file XML che descrive come includere i file di origine quando viene creato un progetto usando il modello di sistema del progetto. Il sistema del progetto stesso viene compilato raccogliendo il file con estensione *vstemplate* e i file di origine in un file *.zip* e viene distribuito copiando il file *.zipin* un percorso noto Visual Studio. Questo processo viene illustrato in modo più dettagliato più avanti in questa procedura dettagliata.

1. In aprire la soluzione SimpleProject creata seguendo l'articolo Creare un sistema [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [di progetto di base, parte 1.](../extensibility/creating-a-basic-project-system-part-1.md)

2. Nel file *SimpleProjectPackage.cs* trovare l'attributo ProvideProjectFactory. Sostituire il secondo parametro (il nome del progetto) con null e il quarto parametro (il percorso della cartella del modello di progetto) con ". \\ \NullPath", come indicato di seguito.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Aggiungere un file XML denominato *SimpleProject.vstemplate* alla *\\ cartella Templates\Projects\SimpleProject. \\*

4. Sostituire il contenuto di *SimpleProject.vstemplate* con il codice seguente.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. Nella finestra **Proprietà** selezionare tutti e cinque i file nella cartella *\\ Templates\Projects\SimpleProject \\* e impostare **l'azione di** compilazione su **ZipProject**.

    ![Cartella Project semplice](../extensibility/media/simpproj2.png "SimpProj2")

    La sezione determina il percorso e l'aspetto del tipo di progetto SimpleProject nella finestra di \<TemplateData> **dialogo Nuovo Project,** come indicato di seguito:

- \<Name>L'elemento designa il modello di progetto come SimpleProject Application.

- \<Description>L'elemento contiene la descrizione visualizzata nella finestra **di dialogo Nuovo Project** quando si seleziona il modello di progetto.

- \<Icon>L'elemento specifica l'icona visualizzata insieme al tipo di progetto SimpleProject.

- \<ProjectType>L'elemento Project il tipo di dati nella finestra di **Project.** Questo nome sostituisce il parametro del nome del progetto dell'attributo ProvideProjectFactory.

  > [!NOTE]
  > \<ProjectType>L'elemento deve corrispondere `LanguageVsTemplate` all'argomento `ProvideProjectFactory` dell'attributo nel file SimpleProjectPackage.cs.

  La \<TemplateContent> sezione descrive questi file generati quando viene creato un nuovo progetto:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Tutti e tre i file `ReplaceParameters` sono impostati su true, che consente la sostituzione dei parametri. Il file *Program.cs* è impostato su true, che determina l'apertura del file nell'editor di codice `OpenInEditor` quando viene creato un progetto.

  Per altre informazioni sugli elementi nello schema Visual Studio template, vedere le informazioni Visual Studio [riferimento allo schema del modello.](../extensibility/visual-studio-template-schema-reference.md)

> [!NOTE]
> Se un progetto ha più di un modello Visual Studio, ogni modello si trova in una cartella separata. Per ogni file in tale cartella l'azione **di compilazione deve** essere impostata su **ZipProject.**

## <a name="adding-a-minimal-vsct-file"></a>Aggiunta di un file con estensione vsct minimo
 Visual Studio essere eseguito in modalità di installazione per riconoscere un modello di Visual Studio modificato. Per la modalità di installazione è *necessario che* sia presente un file vsct. Pertanto, è necessario aggiungere un file *con estensione vsct* minimo al progetto.

1. Aggiungere un file XML denominato *SimpleProject.vsct* al progetto SimpleProject.

2. Sostituire il contenuto del file *SimpleProject.vsct* con il codice seguente.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Impostare **l'azione di** compilazione di questo file su **VSCTCompile**. È possibile eseguire questa operazione solo nel file *con estensione csproj,* non nella **finestra** Proprietà. Assicurarsi che **l'azione di** compilazione di questo file sia impostata su **Nessuna** a questo punto.

    1. Fare clic con il pulsante destro del mouse sul nodo SimpleProject e quindi **scegliere Modifica SimpleProject.csproj**.

    2. Nel file *con estensione csproj* individuare l'elemento *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Modificare l'azione di compilazione in **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. il file di progetto e chiudere l'editor.

    5. Salvare il nodo SimpleProject e quindi nella Esplora soluzioni fare clic **su** **Ricarica Project**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Esaminare le istruzioni Visual Studio di compilazione del modello
 Il sistema di compilazione del progetto VSPackage viene in genere eseguito Visual Studio in modalità di installazione quando il file con estensione *vstemplate* viene modificato o viene ricompilato il progetto che contiene il file con estensione *vstemplate.* È possibile seguire questa procedura impostando il livello di dettaglio di MSBuild su Normale o superiore.

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Espandere il **nodo Progetti e soluzioni** e quindi selezionare Compila ed **esegui**.

3. Impostare **MSBuild livello di dettaglio dell'output di compilazione del progetto** su **Normale.** Fare clic su **OK**.

4. Ricompilare il progetto SimpleProject.

    L'istruzione di compilazione per creare *.zip* file di progetto dovrebbe essere simile all'esempio seguente.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Distribuire un modello Visual Studio distribuzione
Visual Studio modelli non contengono informazioni sul percorso. Pertanto, il *file.zip* modello deve essere distribuito in un percorso noto Visual Studio. Il percorso della cartella ProjectTemplates è *in genere<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates.*

Per distribuire la factory del progetto, il programma di installazione deve avere privilegi di amministratore. Distribuisce i modelli nel nodo Visual Studio di installazione: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testare un Visual Studio modello
Testare la factory del progetto per verificare se crea una gerarchia di progetto usando il Visual Studio modello.

1. Reimpostare l'istanza sperimentale Visual Studio SDK.

    In : nel menu Start individuare la [!INCLUDE[win7](../debugger/includes/win7_md.md)] **cartella Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** e quindi selezionare Reset the Microsoft Visual Studio Experimental instance (Reimposta istanza sperimentale Microsoft Visual Studio **sperimentale).** 

    Nelle versioni successive di Windows: nella **schermata Start** digitare Reset the Microsoft Visual Studio **Experimental \<version> Instance**.

2. Viene visualizzata una finestra del prompt dei comandi. Quando vengono visualizzati i termini **Premere un tasto qualsiasi per continuare,** fare clic su **INVIO.** Dopo la chiusura della finestra, aprire Visual Studio.

3. Ricompilare il progetto SimpleProject e avviare il debug. Viene visualizzata l'istanza sperimentale.

4. Nell'istanza sperimentale creare un progetto SimpleProject. Nella finestra **di dialogo Nuovo Project** selezionare **SimpleProject**.

5. Verrà visualizzata una nuova istanza di SimpleProject.

    ![Nuova Project semplice](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Nuova Project my](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Creare un nodo figlio del tipo di progetto
È possibile aggiungere un nodo figlio a un nodo del tipo di progetto nella **finestra di dialogo Project** progetto . Ad esempio, per il tipo di progetto SimpleProject è possibile avere nodi figlio per applicazioni console, applicazioni finestra, applicazioni Web e così via.

I nodi figlio vengono creati modificando il file di progetto e aggiungendo \<OutputSubPath> elementi figlio agli elementi \<ZipProject> . Quando un modello viene copiato durante la compilazione o la distribuzione, ogni nodo figlio diventa una sottocartella della cartella dei modelli di progetto.

Questa sezione illustra come creare un nodo figlio console per il tipo di progetto SimpleProject.

1. Rinominare la *\\ cartella Templates\Projects\SimpleProject \\* in *\\ Templates\Projects\ConsoleApp \\*.

2. Nella finestra **Proprietà** selezionare tutti e cinque i file nella cartella *\\ Templates\Projects\ConsoleApp \\* e assicurarsi che l'azione di compilazione **sia** impostata su **ZipProject**.

3. Nel file SimpleProject.vstemplate aggiungere la riga seguente alla fine della \<TemplateData> sezione, subito prima del tag di chiusura.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    In questo modo il modello Applicazione console viene visualizzato sia nel nodo figlio console che nel nodo padre SimpleProject, che si trova a un livello superiore al nodo figlio.

4. Salvare il file *SimpleProject.vstemplate.*

5. Nel file *con estensione csproj* aggiungere \<OutputSubPath> a ogni elemento ZipProject. Scaricare il progetto, come in precedenza, e modificare il file di progetto.

6. Individuare gli \<ZipProject> elementi. A ogni \<ZipProject> elemento aggiungere un elemento e \<OutputSubPath> assegnargli il valore Console. The ZipProject

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Aggiungere questo \<PropertyGroup> codice al file di progetto:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Salvare il file di progetto e ricaricare il progetto.

## <a name="test-the-project-type-child-node"></a>Testare il nodo figlio del tipo di progetto
Testare il file di progetto modificato per verificare se il nodo figlio **Console** viene visualizzato nella finestra **di dialogo Project** nuova console.

1. Eseguire lo **strumento Reset the Microsoft Visual Studio Experimental Instance** (Reimposta istanza sperimentale).

2. Ricompilare il progetto SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale

3. Nella finestra **di dialogo Project** nuovo progetto fare clic sul nodo **SimpleProject** . Il **modello Applicazione** console dovrebbe essere visualizzato nel **riquadro** Modelli.

4. Espandere il **nodo SimpleProject.** Verrà visualizzato il nodo figlio **Console.** Il **modello SimpleProject Application** continua a essere visualizzato nel **riquadro** Modelli.

5. Fare clic **su Annulla** e arrestare il debug.

    ![Rollup Project semplice](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nodo della console Project semplice](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Sostituire i parametri del modello di progetto
- [Creazione di un sistema di progetto di base, la](../extensibility/creating-a-basic-project-system-part-1.md) parte 1 ha illustrato come sovrascrivere il metodo per eseguire un tipo `ProjectNode.AddFileFromTemplate` di base di sostituzione dei parametri di modello. In questa sezione viene illustrato come usare i parametri del modello Visual Studio più sofisticati.

Quando si crea un progetto usando un modello Visual Studio nella finestra di dialogo **Nuovo Project,** i parametri del modello vengono sostituiti con stringhe per personalizzare il progetto. Un parametro di modello è un token speciale che inizia e termina con un simbolo di dollaro, ad esempio $time$. I due parametri seguenti sono particolarmente utili per abilitare la personalizzazione nei progetti basati sul modello:

- $GUID[1-10]$ viene sostituito da un nuovo GUID. È possibile specificare fino a 10 GUID univoci, ad esempio $guid 1$.

- $safeprojectname$ è il nome fornito da un utente nella finestra di dialogo Nuovo **Project,** modificato per rimuovere tutti gli spazi e i caratteri non sicuri.

  Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Per sostituire i parametri del modello di progetto

1. Nel file *SimpleProjectNode.cs* rimuovere il `AddFileFromTemplate` metodo .

2. Nel file *\\ Templates\Projects\ConsoleApp\SimpleProject.myproj* individuare la proprietà e modificarne il valore \<RootNamespace> $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Nel file *\\ Templates\Projects\SimpleProject\Program.cs* sostituire il contenuto del file con il codice seguente:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Ricompilare il progetto SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale.

5. Creare una nuova applicazione SimpleProject Console. Nel riquadro **Project tipi** di progetto selezionare **SimpleProject.** In **Visual Studio modelli installati** selezionare Applicazione **console.**

6. Nel progetto appena creato aprire *Program.cs.* Dovrebbe essere simile al seguente (i valori GUID nel file saranno diversi):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Creare una pagina delle proprietà del progetto
È possibile creare una pagina delle proprietà per il tipo di progetto in modo che gli utenti possano visualizzare e modificare le proprietà nei progetti basati sul modello. Questa sezione illustra come creare una pagina delle proprietà indipendente dalla configurazione. Questa pagina delle proprietà di base usa una griglia delle proprietà per visualizzare le proprietà pubbliche espore nella classe della pagina delle proprietà.

Derivare la classe della pagina delle proprietà dalla `SettingsPage` classe di base. La griglia delle proprietà fornita dalla classe riconosce la maggior parte dei tipi di dati `SettingsPage` primitivi e sa come visualizzarli. Inoltre, la classe `SettingsPage` sa come rendere persistenti i valori delle proprietà nel file di progetto.

La pagina delle proprietà creata in questa sezione consente di modificare e salvare queste proprietà del progetto:

- AssemblyName

- OutputType

- Rootnamespace.

1. Nel file *SimpleProjectPackage.cs* aggiungere questo `ProvideObject` attributo alla classe `SimpleProjectPackage` :

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Questa operazione registra la classe della pagina delle `GeneralPropertyPage` proprietà con COM.

2. Nel file *SimpleProjectNode.cs* aggiungere questi due metodi sottoposti a override alla `SimpleProjectNode` classe :

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Entrambi questi metodi restituiscono una matrice di GUID della pagina delle proprietà. Il GUID di GeneralPropertyPage è l'unico  elemento nella matrice, quindi nella finestra di dialogo Pagine delle proprietà verrà visualizzata una sola pagina.

3. Aggiungere un file di classe *denominato GeneralPropertyPage.cs* al progetto SimpleProject.

4. Sostituire il contenuto di questo file usando il codice seguente:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    La `GeneralPropertyPage` classe espone le tre proprietà pubbliche AssemblyName, OutputType e RootNamespace. Poiché AssemblyName non ha alcun metodo impostato, viene visualizzato come proprietà di sola lettura. OutputType è una costante enumerata, quindi viene visualizzato come elenco a discesa.

    La `SettingsPage` classe base fornisce per rendere `ProjectMgr` persistenti le proprietà. Il `BindProperties` metodo usa per recuperare i valori delle proprietà `ProjectMgr` persistenti e impostare le proprietà corrispondenti. Il `ApplyChanges` metodo usa per ottenere i valori delle proprietà e per rendere `ProjectMgr` persistenti i valori nel file di progetto. Il metodo set di proprietà `IsDirty` imposta su true per indicare che le proprietà devono essere rese persistenti. La persistenza si verifica quando si salva il progetto o la soluzione.

5. Ricompilare la soluzione SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale.

6. Nell'istanza sperimentale creare una nuova applicazione SimpleProject.

7. Visual Studio chiama la factory del progetto per creare un progetto usando il Visual Studio predefinito. Il nuovo file *Program.cs* viene aperto nell'editor di codice.

8. Fare clic con il pulsante destro del mouse **sul nodo Esplora soluzioni** e quindi scegliere **Proprietà.** Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

    ![Pagina delle Project semplice](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testare la pagina delle proprietà del progetto
È ora possibile verificare se è possibile modificare e modificare i valori delle proprietà.

1. Nella finestra di dialogo Pagine delle **proprietà di MyConsoleApplication** impostare **DefaultNamespace** su **MyApplication**.

2. Selezionare la **proprietà OutputType** e quindi libreria **di classi.**

3. Fare clic su **Applica** e quindi su **OK**.

4. **Riaprire la finestra di** dialogo Pagine delle proprietà e verificare che le modifiche siano state salvate in modo permanente.

5. Chiudere l'istanza sperimentale di Visual Studio.

6. Riaprire l'istanza sperimentale.

7. **Riaprire la finestra di** dialogo Pagine delle proprietà e verificare che le modifiche siano state salvate in modo permanente.

8. Chiudere l'istanza sperimentale di Visual Studio.
    ![Chiudere l'istanza sperimentale](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
