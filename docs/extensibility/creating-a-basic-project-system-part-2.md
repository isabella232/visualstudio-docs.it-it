---
title: Creazione di un sistema di progetto di base, parte 2 | Microsoft Docs
description: Informazioni su come aggiungere un modello di Visual Studio, una pagina delle proprietà e altre funzionalità a un progetto creato in un articolo precedente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ceef95f90d2f54ad7b527ccc8c00322c77491fb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853152"
---
# <a name="create-a-basic-project-system-part-2"></a>Creazione di un sistema di progetto di base, parte 2
La prima procedura dettagliata della serie, [creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md), Mostra come creare un sistema di progetto di base. Questa procedura dettagliata si basa sul sistema di progetto di base aggiungendo un modello di Visual Studio, una pagina delle proprietà e altre funzionalità. Prima di iniziare, è necessario completare la prima procedura dettagliata.

In questa procedura dettagliata viene illustrato come creare un tipo di progetto con estensione del nome file di progetto *. PROG*. Per completare la procedura dettagliata, non è necessario creare la propria lingua perché la procedura dettagliata prende in prestito dal sistema del progetto Visual C# esistente.

Questa procedura dettagliata illustra come eseguire queste attività:

- Creare un modello di Visual Studio.

- Distribuire un modello di Visual Studio.

- Creare un nodo figlio del tipo di progetto nella finestra di dialogo **nuovo progetto** .

- Abilitare la sostituzione dei parametri nel modello di Visual Studio.

- Creare una pagina delle proprietà del progetto.

> [!NOTE]
> I passaggi descritti in questa procedura dettagliata sono basati su un progetto C#. Tuttavia, ad eccezione delle specifiche, ad esempio le estensioni di file e il codice, è possibile usare la stessa procedura per un progetto Visual Basic.

## <a name="create-a-visual-studio-template"></a>Creare un modello di Visual Studio
- [Creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) Mostra come creare un modello di progetto di base e aggiungerlo al sistema del progetto. Illustra anche come registrare questo modello con Visual Studio usando l' <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo, che scrive il percorso completo della cartella *\\ Templates\Projects\SimpleProject \\* nel registro di sistema.

Usando un modello di Visual Studio (file con *estensione vstemplate* ) invece di un modello di progetto di base, è possibile controllare il modo in cui il modello viene visualizzato nella finestra di dialogo **nuovo progetto** e come sostituire i parametri del modello. Un file con *estensione vstemplate* è un file XML che descrive il modo in cui i file di origine devono essere inclusi quando un progetto viene creato usando il modello di sistema del progetto. Il sistema del progetto stesso viene compilato raccogliendo il file con estensione *vstemplate* e i file di origine in un file con *estensione zip* e distribuiti copiando il file *zip* in un percorso noto a Visual Studio. Questo processo viene illustrato in modo più dettagliato più avanti in questa procedura dettagliata.

1. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire la soluzione SimpleProject creata seguendo la procedura [creare un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. Nel file *SimpleProjectPackage.cs* trovare l'attributo ProvideProjectFactory. Sostituire il secondo parametro (il nome del progetto) con null e il quarto parametro (il percorso della cartella del modello di progetto) con ". \\ \NullPath ", come indicato di seguito.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Aggiungere un file XML denominato *SimpleProject. vstemplate* alla cartella *\\ Templates\Projects\SimpleProject \\* .

4. Sostituire il contenuto di *SimpleProject. vstemplate* con il codice seguente.

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

5. Nella finestra **Proprietà** selezionare tutti e cinque i file nella cartella *\\ Templates\Projects\SimpleProject \\* e impostare l' **azione di compilazione** su **ZipProject**.

    ![Cartella di progetto semplice](../extensibility/media/simpproj2.png "SimpProj2")

    La \<TemplateData> sezione determina la posizione e l'aspetto del tipo di progetto SimpleProject nella finestra di dialogo **nuovo progetto** , come indicato di seguito:

- L' \<Name> elemento assegna un nome al modello di progetto da applicare come SimpleProject.

- L' \<Description> elemento contiene la descrizione che viene visualizzata nella finestra di dialogo **nuovo progetto** quando viene selezionato il modello di progetto.

- L' \<Icon> elemento specifica l'icona visualizzata insieme al tipo di progetto SimpleProject.

- L' \<ProjectType> elemento assegna un nome al tipo di progetto nella finestra di dialogo **nuovo progetto** . Questo nome sostituisce il parametro del nome del progetto dell'attributo ProvideProjectFactory.

  > [!NOTE]
  > L' \<ProjectType> elemento deve corrispondere all' `LanguageVsTemplate` argomento dell' `ProvideProjectFactory` attributo nel file SimpleProjectPackage.cs.

  La \<TemplateContent> sezione descrive questi file che vengono generati quando viene creato un nuovo progetto:

- *SimpleProject. PROG*

- *Program.cs*

- *AssemblyInfo.cs*

  Tutti e tre i file sono `ReplaceParameters` impostati su true, che consente la sostituzione dei parametri. Il file *Program.cs* è `OpenInEditor` impostato su true, che determina l'apertura del file nell'editor di codice quando viene creato un progetto.

  Per altre informazioni sugli elementi nello schema dei modelli di Visual Studio, vedere [riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Se un progetto ha più di un modello di Visual Studio, ogni modello si trova in una cartella separata. Ogni file in tale cartella deve avere l' **azione di compilazione** impostata su **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Aggiunta di un file con estensione vsct minimo
 È necessario eseguire Visual Studio in modalità di installazione per riconoscere un modello di Visual Studio nuovo o modificato. Per la modalità di installazione è necessario che sia presente un file con *estensione vsct* . Pertanto, è necessario aggiungere al progetto un file con *estensione vsct* minimo.

1. Aggiungere un file XML denominato *SimpleProject. vsct* al progetto SimpleProject.

2. Sostituire il contenuto del file *SimpleProject. vsct* con il codice seguente.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Impostare l' **azione di compilazione** del file su **VSCTCompile**. Questa operazione può essere eseguita solo nel file con *estensione csproj* , non nella finestra **Proprietà** . Verificare che l' **azione di compilazione** del file sia impostata su **None** in questo punto.

    1. Fare clic con il pulsante destro del mouse sul nodo SimpleProject, quindi scegliere **modifica SimpleProject. csproj**.

    2. Nel file con *estensione csproj* individuare l'elemento *SimpleProject. vsct* .

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Modificare l'azione di compilazione in **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. il file di progetto e chiudere l'editor.

    5. Salvare il nodo SimpleProject, quindi nella **Esplora soluzioni** fare clic su **Ricarica progetto**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Esaminare i passaggi di compilazione dei modelli di Visual Studio
 Il sistema di compilazione del progetto VSPackage esegue in genere Visual Studio in modalità di installazione quando il file con *estensione vstemplate* viene modificato o il progetto che contiene il file con *estensione vstemplate* viene ricompilato. È possibile seguire la procedura impostando il livello di dettaglio di MSBuild su Normal o un valore superiore.

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Espandere il nodo **progetti e soluzioni** e quindi selezionare **Compila ed Esegui**.

3. Impostare il livello di **dettaglio dell'output di compilazione del progetto MSBuild** su **Normal**. Fare clic su **OK**.

4. Ricompilare il progetto SimpleProject.

    L'istruzione di compilazione per creare il file di progetto *zip* dovrebbe essere simile all'esempio seguente.

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

## <a name="deploy-a-visual-studio-template"></a>Distribuire un modello di Visual Studio
I modelli di Visual Studio non contengono informazioni sul percorso. Pertanto, il file con *estensione zip* del modello deve essere distribuito in un percorso noto a Visual Studio. Il percorso della cartella ProjectTemplates è in genere *<% LocalAppData% > \microsoft\visualstudio\14.0exp\projecttemplates*.

Per distribuire la factory del progetto, è necessario che il programma di installazione disponga dei privilegi di amministratore. Distribuisce i modelli nel nodo di installazione di Visual Studio: *. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testare un modello di Visual Studio
Testare la factory del progetto per verificare se crea una gerarchia di progetto usando il modello di Visual Studio.

1. Reimposta l'istanza sperimentale di Visual Studio SDK.

    In [!INCLUDE[win7](../debugger/includes/win7_md.md)] : nel menu **Start** individuare la cartella **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** , quindi selezionare **Reimposta Microsoft Visual Studio istanza sperimentale**.

    Nelle versioni successive di Windows: nella schermata **Start** digitare **Reset the Microsoft Visual Studio \<version> istanza sperimentale**.

2. Viene visualizzata una finestra del prompt dei comandi. Quando vengono visualizzate le parole **premere un tasto qualsiasi per continuare**, fare clic su **invio**. Dopo la chiusura della finestra, aprire Visual Studio.

3. Ricompilare il progetto SimpleProject e avviare il debug. Viene visualizzata l'istanza sperimentale.

4. Nell'istanza sperimentale creare un progetto SimpleProject. Nella finestra di dialogo **nuovo progetto** selezionare **SimpleProject**.

5. Verrà visualizzata una nuova istanza di SimpleProject.

    ![Nuova istanza del progetto semplice](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Nuova istanza del progetto](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Creare un nodo figlio di tipo progetto
È possibile aggiungere un nodo figlio a un nodo del tipo di progetto nella finestra di dialogo **nuovo progetto** . Per il tipo di progetto SimpleProject, ad esempio, è possibile avere nodi figlio per applicazioni console, applicazioni Windows, applicazioni Web e così via.

I nodi figlio vengono creati modificando il file di progetto e aggiungendo \<OutputSubPath> elementi figlio agli \<ZipProject> elementi. Quando un modello viene copiato durante la compilazione o la distribuzione, ogni nodo figlio diventa una sottocartella della cartella dei modelli di progetto.

In questa sezione viene illustrato come creare un nodo figlio console per il tipo di progetto SimpleProject.

1. Rinominare la cartella *\\ Templates\Projects\SimpleProject \\* in *\\ Templates\Projects\ConsoleApp \\*.

2. Nella finestra **Proprietà** selezionare tutti e cinque i file nella cartella *\\ Templates\Projects\ConsoleApp \\* e assicurarsi che l' **azione di compilazione** sia impostata su **ZipProject**.

3. Nel file SimpleProject. vstemplate aggiungere la riga seguente alla fine della \<TemplateData> sezione, immediatamente prima del tag di chiusura.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    In questo modo il modello di applicazione console verrà visualizzato sia nel nodo figlio della console che nel nodo padre SimpleProject, che è un livello al di sopra del nodo figlio.

4. Salvare il file *SimpleProject. vstemplate* .

5. Nel file con *estensione csproj* aggiungere \<OutputSubPath> a ogni elemento ZipProject. Scaricare il progetto, come in precedenza, e modificare il file di progetto.

6. Individuare gli \<ZipProject> elementi. Aggiungere a ogni \<ZipProject> elemento un \<OutputSubPath> elemento e assegnargli il valore console. ZipProject

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

7. Aggiungere \<PropertyGroup> il file al progetto:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Salvare il file di progetto e ricaricare il progetto.

## <a name="test-the-project-type-child-node"></a>Testare il nodo figlio del tipo di progetto
Testare il file di progetto modificato per verificare se il nodo figlio della **console** viene visualizzato nella finestra di dialogo **nuovo progetto** .

1. Eseguire lo strumento **Reimposta l'istanza sperimentale di Microsoft Visual Studio** .

2. Ricompilare il progetto SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale

3. Nella finestra di dialogo **nuovo progetto** fare clic sul nodo **SimpleProject** . Il modello **applicazione console** verrà visualizzato nel riquadro **modelli** .

4. Espandere il nodo **SimpleProject** . Verrà visualizzato il nodo figlio della **console** . Il modello di **applicazione SimpleProject** continua a essere visualizzato nel riquadro **modelli** .

5. Fare clic su **Annulla** e arrestare il debug.

    ![Rollup progetto semplice](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nodo console progetto semplice](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Sostituire i parametri del modello di progetto
- La [creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) ha mostrato come sovrascrivere il `ProjectNode.AddFileFromTemplate` metodo per eseguire un tipo di base di sostituzione dei parametri di modello. Questa sezione illustra come usare i parametri più sofisticati per i modelli di Visual Studio.

Quando si crea un progetto usando un modello di Visual Studio nella finestra di dialogo **nuovo progetto** , i parametri di modello vengono sostituiti con stringhe per personalizzare il progetto. Un parametro di modello è un token speciale che inizia e termina con un segno di dollaro, ad esempio $time $. I due parametri seguenti sono particolarmente utili per l'abilitazione della personalizzazione nei progetti basati sul modello:

- $GUID [1-10] $ viene sostituito da un nuovo GUID. È possibile specificare fino a 10 GUID univoci, ad esempio $guid $1.

- $safeprojectname $ è il nome fornito da un utente nella finestra di dialogo **nuovo progetto** , modificato per rimuovere tutti i caratteri e gli spazi non sicuri.

  Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Per sostituire i parametri del modello di progetto

1. Nel file *SimpleProjectNode.cs* rimuovere il `AddFileFromTemplate` metodo.

2. Nel file *\\ Templates\Projects\ConsoleApp\SimpleProject.MyProj* individuare la \<RootNamespace> proprietà e modificarne il valore in $safeprojectname $.

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

5. Creare una nuova applicazione console SimpleProject. Nel riquadro **Tipi progetto** selezionare **SimpleProject**. In **modelli Visual Studio installati** selezionare **applicazione console**.

6. Nel progetto appena creato aprire *Program.cs*. Il risultato dovrebbe essere simile al seguente (i valori GUID nel file saranno diversi):

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

## <a name="create-a-project-property-page"></a>Creazione di una pagina delle proprietà del progetto
È possibile creare una pagina delle proprietà per il tipo di progetto in modo che gli utenti possano visualizzare e modificare le proprietà nei progetti basati sul modello. In questa sezione viene illustrato come creare una pagina delle proprietà indipendente dalla configurazione. Questa pagina delle proprietà di base utilizza una griglia proprietà per visualizzare le proprietà pubbliche esposte nella classe della pagina delle proprietà.

Derivare la classe della pagina delle proprietà dalla `SettingsPage` classe di base. La griglia delle proprietà fornita dalla `SettingsPage` classe è compatibile con la maggior parte dei tipi di dati primitivi e sa come visualizzarli. Inoltre, la `SettingsPage` classe sa come salvare in modo permanente i valori delle proprietà nel file di progetto.

La pagina delle proprietà creata in questa sezione consente di modificare e salvare le proprietà del progetto:

- AssemblyName

- OutputType

- RootNamespace.

1. Nel file *SimpleProjectPackage.cs* aggiungere questo `ProvideObject` attributo alla `SimpleProjectPackage` classe:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Viene registrata la classe della pagina delle proprietà `GeneralPropertyPage` con com.

2. Nel file *SimpleProjectNode.cs* aggiungere questi due metodi sottoposti a override alla `SimpleProjectNode` classe:

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

    Entrambi questi metodi restituiscono una matrice di GUID della pagina delle proprietà. Il GUID GeneralPropertyPage è l'unico elemento nella matrice, quindi nella finestra di dialogo **pagine delle proprietà** verrà visualizzata solo una pagina.

3. Aggiungere un file di classe denominato *GeneralPropertyPage.cs* al progetto SimpleProject.

4. Sostituire il contenuto del file usando il codice seguente:

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

    La `GeneralPropertyPage` classe espone le tre proprietà pubbliche AssemblyName, OutputType e RootNamespace. Poiché AssemblyName non dispone di un metodo set, viene visualizzato come proprietà di sola lettura. OutputType è una costante enumerata, quindi viene visualizzata come elenco a discesa.

    La `SettingsPage` classe base fornisce `ProjectMgr` per salvare in modo permanente le proprietà. Il `BindProperties` metodo usa `ProjectMgr` per recuperare i valori di proprietà salvati in modo permanente e impostare le proprietà corrispondenti. Il `ApplyChanges` metodo usa `ProjectMgr` per ottenere i valori delle proprietà e salvarli in modo permanente nel file di progetto. Il metodo set di proprietà imposta `IsDirty` su true per indicare che le proprietà devono essere rese permanente. La persistenza si verifica quando si salva il progetto o la soluzione.

5. Ricompilare la soluzione SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale.

6. Nell'istanza sperimentale creare una nuova applicazione SimpleProject.

7. Visual Studio chiama la factory del progetto per creare un progetto usando il modello di Visual Studio. Il nuovo file *Program.cs* viene aperto nell'editor di codice.

8. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni**, quindi scegliere **Proprietà**. Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

    ![Pagina delle proprietà del progetto semplice](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testare la pagina delle proprietà del progetto
A questo punto è possibile verificare se è possibile modificare e modificare i valori delle proprietà.

1. Nella finestra di dialogo **pagine delle proprietà di MyConsoleApplication** modificare **una proprietà DefaultNamespace** in **MyApplication**.

2. Selezionare la proprietà **OutputType** , quindi scegliere **libreria di classi**.

3. Fare clic su **Applica** e quindi su **OK**.

4. Riaprire la finestra di dialogo **pagine delle proprietà** e verificare che le modifiche siano state rese permanente.

5. Chiudere l'istanza sperimentale di Visual Studio.

6. Riaprire l'istanza sperimentale.

7. Riaprire la finestra di dialogo **pagine delle proprietà** e verificare che le modifiche siano state rese permanente.

8. Chiudere l'istanza sperimentale di Visual Studio.
    ![Chiudere l'istanza sperimentale](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
