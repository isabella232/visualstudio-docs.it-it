---
title: Creazione di un sistema di progetto di base, parte 2 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739719"
---
# <a name="create-a-basic-project-system-part-2"></a>Creare un sistema di progetto di base, parte 2
Nella prima procedura dettagliata di questa serie, [Creare un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md), viene illustrato come creare un sistema di progetto di base. Questa procedura dettagliata si basa sul sistema di progetto di base aggiungendo un modello di Visual Studio, una pagina delle proprietà e altre funzionalità. È necessario completare la prima procedura dettagliata prima di iniziare questa.

In questa procedura dettagliata viene illustrato come creare un tipo di progetto con estensione *myproj*di progetto. Per completare la procedura dettagliata, non è necessario creare un linguaggio personalizzato perché la procedura dettagliata prende in prestito dal sistema di progetto Visual C.

In questa procedura dettagliata viene illustrato come eseguire queste attività:This walkthrough teaches how to accomplish these tasks:

- Creare un modello di Visual Studio.Create a Visual Studio template.

- Distribuire un modello di Visual Studio.Deploy a Visual Studio template.

- Creare un nodo figlio di tipo progetto nella finestra di dialogo **Nuovo progetto.**

- Abilitare la sostituzione dei parametri nel modello di Visual Studio.Enable parameter substitution in the Visual Studio template.

- Creare una pagina delle proprietà del progetto.

> [!NOTE]
> I passaggi di questa procedura dettagliata sono basati su un progetto in C. Tuttavia, ad eccezione di specifiche, ad esempio le estensioni di file e il codice, è possibile utilizzare la stessa procedura per un progetto di Visual Basic.However, except for specifics such as file name extensions and code, you can use the same steps for a Visual Basic project.

## <a name="create-a-visual-studio-template"></a>Creare un modello di Visual StudioCreate a Visual Studio template
- Creare un sistema di [progetto di base, la parte 1](../extensibility/creating-a-basic-project-system-part-1.md) mostra come creare un modello di progetto di base e aggiungerlo al sistema di progetto. Viene inoltre illustrato come registrare questo modello <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> con Visual Studio utilizzando l'attributo , che scrive il percorso completo della cartella * \\Templates, Projects e SimpleProject\\ * nel Registro di sistema.

Utilizzando un modello di Visual Studio (file *.vstemplate)* anziché un modello di progetto di base, è possibile controllare la modalità di visualizzazione del modello nella finestra di dialogo **Nuovo progetto** e la modalità di sostituzione dei parametri del modello. Un file *.vstemplate* è un file XML che descrive come i file di origine devono essere inclusi quando un progetto viene creato utilizzando il modello di sistema del progetto. Il sistema del progetto stesso viene compilato raccogliendo il file *con estensione vstemplate* e i file di origine in un file *con estensione zip* e distribuito copiando il file con estensione *zip* in un percorso noto in Visual Studio. Questo processo viene illustrato in modo più dettagliato più avanti in questa procedura dettagliata.

1. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aprire la soluzione SimpleProject creata seguendo Creare un sistema di [progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. Nel file *SimpleProjectPackage.cs* individuare l'attributo ProvideProjectFactory. Sostituire il secondo parametro (il nome del progetto) con null e il quarto parametro (il percorso della cartella del modello di progetto) con ". \\"Percorso Null", come indicato di seguito.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Aggiungere un file XML denominato *SimpleProject.vstemplate* alla cartella * \\Templates, Projects, SimpleProject.\\ *

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

5. Nella finestra **Proprietà** selezionare tutti e cinque i file nella cartella * \\Modelli, Progetti e Progetto Semplici,\\ * quindi impostare l'azione di compilazione **su** Progetto **zip**.

    ![Cartella di progetto semplice](../extensibility/media/simpproj2.png "SimpProj2")

    La \<sezione> TemplateData determina il percorso e l'aspetto del tipo di progetto SimpleProject nella finestra di dialogo **Nuovo progetto,** come indicato di seguito:

- Il \<Name> elemento denomina il modello di progetto per l'applicazione SimpleProject.The Name a Name a name the project template to be SimpleProject Application.

- L'elemento \<Descrizione> contiene la descrizione visualizzata nella finestra di dialogo **Nuovo progetto** quando viene selezionato il modello di progetto.

- L'elemento \<> Icon specifica l'icona visualizzata insieme al tipo di progetto SimpleProject.

- Il \<ProjectType> elemento denomina il tipo di progetto nella finestra di dialogo **Nuovo progetto** . Questo nome sostituisce il parametro del nome del progetto dell'attributo ProvideProjectFactory.

  > [!NOTE]
  > L'elemento \<> ProjectType `LanguageVsTemplate` deve `ProvideProjectFactory` corrispondere all'argomento dell'attributo nel file di SimpleProjectPackage.cs.

  La \<sezione> TemplateContent descrive questi file generati quando viene creato un nuovo progetto:The TemplateContent> section describes these files that are generated when a new project is created:

- *Progetto Semplice.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Tutti e `ReplaceParameters` tre i file sono impostati su true, che consente la sostituzione dei parametri. Il *file* `OpenInEditor` Program.cs è impostato su true, che determina l'apertura del file nell'editor di codice quando viene creato un progetto.

  Per ulteriori informazioni sugli elementi nello schema dei modelli di Visual Studio, vedere informazioni di [riferimento sullo schema](../extensibility/visual-studio-template-schema-reference.md)dei modelli di Visual Studio .

> [!NOTE]
> Se un progetto ha più di un modello di Visual Studio, ogni modello si trova in una cartella separata. Per ogni file contenuto in tale cartella deve essere impostata **l'azione di compilazione** **su Progettozip**.

## <a name="adding-a-minimal-vsct-file"></a>Aggiunta di un file vsct minimo
 Visual Studio deve essere eseguito in modalità di installazione per riconoscere un modello di Visual Studio nuovo o modificato. La modalità di installazione richiede la presenza di un file *vsct.* Pertanto, è necessario aggiungere un file *vsct* minimo al progetto.

1. Aggiungere un file XML denominato *SimpleProject.vsct* al progetto SimpleProject.

2. Sostituire il contenuto del file *SimpleProject.vsct* con il codice seguente.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Impostare l'azione di **compilazione** di questo file su **VSCTCompile**. È possibile eseguire questa operazione solo nel file *con estensione csproj,* non nella finestra **Proprietà.** Assicurarsi che l'azione di **compilazione** di questo file sia **impostata** su Nessuno a questo punto.

    1. Fare clic con il pulsante destro del mouse sul nodo SimpleProject , quindi **scegliere Modifica SimpleProject.csproj**.

    2. Nel file *con estensione csproj* individuare l'elemento *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Modificare l'azione di compilazione in **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. il file di progetto e chiudere l'editor.

    5. Salvare il nodo SimpleProject , quindi in **Esplora soluzioni** fare clic su **Ricarica progetto**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Esaminare le istruzioni di compilazione dei modelli di Visual StudioExamine the Visual Studio template build steps
 Il sistema di compilazione del progetto VSPackage esegue in genere Visual Studio in modalità di installazione quando il file *.vstemplate* viene modificato o il progetto che contiene il file *.vstemplate* viene ricompilato. È possibile seguire impostando il livello di dettaglio di MSBuild su Normale o superiore.

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Espandere il nodo **Progetti e soluzioni** , quindi selezionare **Compila ed esegui**.

3. Impostare il **livello di dettaglio dell'output di compilazione del progetto MSBuild** su **Normal**. Fare clic su **OK**.

4. Ricompilare il progetto SimpleProject.

    L'istruzione di compilazione per creare il file di progetto *con estensione zip* dovrebbe essere simile all'esempio seguente.

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

## <a name="deploy-a-visual-studio-template"></a>Distribuire un modello di Visual StudioDeploy a Visual Studio template
I modelli di Visual Studio non contengono informazioni sul percorso. Pertanto, il file *con estensione zip* del modello deve essere distribuito in un percorso noto a Visual Studio. Il percorso della cartella ProjectTemplates è in genere *<%LOCALAPPDATA%> .*

Per distribuire la factory del progetto, il programma di installazione deve disporre dei privilegi di amministratore. Vengono distribuiti i modelli nel nodo di installazione di Visual Studio: ... . *. . .*. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

## <a name="test-a-visual-studio-template"></a>Testare un modello di Visual StudioTest a Visual Studio template
Testare la factory del progetto per verificare se crea una gerarchia di progetto usando il modello di Visual Studio.Test your project factory to see whether it creates a project hierarchy by using the Visual Studio template.

1. Reimpostare l'istanza sperimentale di Visual Studio SDK.

    Attivato: [!INCLUDE[win7](../debugger/includes/win7_md.md)]nel menu **Start** individuare la cartella Microsoft **Visual Studio/Microsoft Visual Studio SDK/Tools** e quindi selezionare **Reimposta l'istanza sperimentale**di Microsoft Visual Studio .

    Nelle versioni successive di Windows: nella schermata **Start** **digitare Reimposta la versione di Microsoft Visual Studio \<> Istanza sperimentale**.

2. Viene visualizzata una finestra del prompt dei comandi. Quando vengono visualizzate le parole **Premere un tasto qualsiasi per continuare**, fare clic su **INVIO**. Dopo la chiusura della finestra, aprire Visual Studio.After the window closes, open Visual Studio.

3. Ricompilare il progetto SimpleProject e avviare il debug. Viene visualizzata l'istanza sperimentale.

4. Nell'istanza sperimentale, creare un progetto SimpleProject.In the experimental instance, create a SimpleProject project. Nella finestra di dialogo **Nuovo progetto** selezionare **SimpleProject**.

5. Verrà visualizzata una nuova istanza di SimpleProject.You should see a new instance of SimpleProject.

    ![Nuova istanza di progetto semplice](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Nuova istanza del progetto personale](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Creare un nodo figlio del tipo di progettoCreate a project type child node
È possibile aggiungere un nodo figlio a un nodo di tipo progetto nella finestra di dialogo **Nuovo progetto.** Ad esempio, per il tipo di progetto SimpleProject, è possibile disporre di nodi figlio per applicazioni console, applicazioni finestra, applicazioni Web e così via.

I nodi figlio vengono creati modificando \<il file di \<progetto e aggiungendo OutputSubPath> elementi figlio agli elementi> . Quando un modello viene copiato durante la compilazione o la distribuzione, ogni nodo figlio diventa una sottocartella della cartella dei modelli di progetto.

In questa sezione viene illustrato come creare un nodo figlio Console per il tipo di progetto SimpleProject.This section shows how to create a Console child node for the SimpleProject project type.

1. Rinominare la * \\cartella Templates, Projects, SimpleProject\\ * in * \\Templates, Projects, ConsoleApp\\*.

2. Nella finestra **Proprietà,** selezionare tutti e cinque i file nella cartella * \\Modelli,\\ Progetti e ConsoleApp,* e assicurarsi che l'azione di **compilazione** sia impostata su **.**

3. Nel file SimpleProject.vstemplate aggiungere la riga seguente \<alla fine della sezione> TemplateData, appena prima del tag di chiusura.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    In questo modo il modello applicazione console venga visualizzato sia nel nodo figlio Console che nel nodo padre SimpleProject, che si trova di un livello al di sopra del nodo figlio.

4. Salvare il file *SimpleProject.vstemplate.*

5. Nel file *con estensione csproj,* aggiungere \<OutputSubPath> a ciascuno degli elementi di .ipProject. Scaricare il progetto, come in precedenza, e modificare il file di progetto.

6. Individuare \<gli elementi> .ipProject. A \<ogni elemento> di \<.ipProject, aggiungere un OutputSubPath> elemento e assegnargli il valore Console. Il progetto zip

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

7. Aggiungere \<questo propertyGroup> al file di progetto:Add this PropertyGroup> to the project file:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Salvare il file di progetto e ricaricare il progetto.

## <a name="test-the-project-type-child-node"></a>Testare il nodo figlio del tipo di progettoTest the project type child node
Testare il file di progetto modificato per verificare se il nodo figlio **Console** viene visualizzato nella finestra di dialogo **Nuovo progetto.**

1. Eseguire lo strumento **Reimposta istanza sperimentale** di Microsoft Visual Studio.

2. Ricompilare il progetto SimpleProject e avviare il debug. L'istanza sperimentale dovrebbe apparire

3. Nella finestra di dialogo **Nuovo progetto** fare clic sul nodo **SimpleProject.** Il modello Applicazione console dovrebbe essere visualizzato nel riquadro Modelli.The **Console Application** template should appear in the **Templates** pane.

4. Espandere il nodo **SimpleProject.** Verrà visualizzato il nodo figlio **Console.** Il modello Applicazione SimpleProject continua a essere visualizzato nel riquadro **Modelli.The** **SimpleProject Application** template continues to appear in the Templates pane.

5. Fare clic su **Annulla** e interrompere il debug.

    ![Rollup progetto semplice](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nodo Console di progetto semplice](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Sostituzione dei parametri del modello di progetto
- Creazione di un sistema di [progetto di base, la parte 1](../extensibility/creating-a-basic-project-system-part-1.md) ha illustrato come sovrascrivere il `ProjectNode.AddFileFromTemplate` metodo per eseguire un tipo di base di sostituzione dei parametri di modello. In questa sezione viene illustrato come utilizzare i parametri di modello di Visual Studio più sofisticati.

Quando si crea un progetto utilizzando un modello di Visual Studio nella finestra di dialogo **Nuovo progetto,** i parametri del modello vengono sostituiti con stringhe per personalizzare il progetto. Un parametro di modello è un token speciale che inizia e termina con un simbolo del dollaro, ad esempio, $time. I due parametri seguenti sono particolarmente utili per abilitare la personalizzazione nei progetti basati sul modello:

- $GUID[1-10] viene sostituito da un nuovo Guid. È possibile specificare fino a 10 GUID univoci, ad esempio $guid1.

- $safeprojectname è il nome fornito da un utente nella finestra di dialogo **Nuovo progetto,** modificato per rimuovere tutti i caratteri e gli spazi non sicuri.

  Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Per sostituire i parametri del modello di progetto

1. Nel file *SimpleProjectNode.cs,* `AddFileFromTemplate` rimuovere il metodo.

2. Nel file * \\Templates,Projects,ConsoleApp/SimpleProject.myproj* individuare \<la proprietà rootNamespace> e modificarne il valore in $safeprojectname.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Nel file * \\Templates,Projects/SimpleProject/Program.cs* sostituire il contenuto del file con il codice seguente:

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

5. Creare una nuova applicazione SimpleProject Console.Create a new SimpleProject Console application. Nel riquadro **Tipi** progetto selezionare **SimpleProject**. In **Modelli Visual Studio installati**selezionare Applicazione **console**.)

6. Nel progetto appena creato aprire *Program.cs*. Dovrebbe essere simile al seguente (i valori GUID nel file saranno diversi.):

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

## <a name="create-a-project-property-page"></a>Creare una pagina delle proprietà del progettoCreate a project property page
È possibile creare una pagina delle proprietà per il tipo di progetto in modo che gli utenti possano visualizzare e modificare le proprietà nei progetti basati sul modello. In questa sezione viene illustrato come creare una pagina delle proprietà indipendente dalla configurazione. Questa pagina delle proprietà di base usa una griglia delle proprietà per visualizzare le proprietà pubbliche esposte nella classe della pagina delle proprietà.

Derivare la classe `SettingsPage` della pagina delle proprietà dalla classe di base. La griglia delle `SettingsPage` proprietà fornita dalla classe è a conoscenza della maggior parte dei tipi di dati primitivi e sa come visualizzarli. Inoltre, la `SettingsPage` classe sa come rendere persistenti i valori delle proprietà nel file di progetto.

La pagina delle proprietà creata in questa sezione consente di modificare e salvare le proprietà del progetto seguenti:The property page you create in this section lets you alter and save these project properties:

- AssemblyName

- OutputType

- Rootnamespace.

1. Nel file *di* SimpleProjectPackage.cs `ProvideObject` aggiungere `SimpleProjectPackage` questo attributo alla classe:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    In questo modo viene `GeneralPropertyPage` eseguita la classe della pagina delle proprietà con COM.

2. Nel file *SimpleProjectNode.cs* aggiungere questi due metodi `SimpleProjectNode` sottoposti a override alla classe:

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

    Entrambi questi metodi restituiscono una matrice di GUID della pagina delle proprietà. Il GUID GeneralPropertyPage è l'unico elemento nella matrice, pertanto la finestra di dialogo **Pagine delle proprietà** verrà visualizzata una sola pagina.

3. Aggiungere un file di classe denominato GeneralPropertyPage.cs al progetto SimpleProject.Add a class file named *GeneralPropertyPage.cs* to the SimpleProject project.

4. Sostituire il contenuto di questo file utilizzando il codice seguente:

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

    La `GeneralPropertyPage` classe espone le tre proprietà pubbliche AssemblyName, OutputType e RootNamespace. Poiché AssemblyName non dispone di alcun metodo set, viene visualizzato come proprietà di sola lettura. OutputType è una costante enumerata, pertanto viene visualizzato come elenco a discesa.

    La `SettingsPage` classe `ProjectMgr` base fornisce per rendere persistenti le proprietà. Il `BindProperties` metodo `ProjectMgr` utilizza per recuperare i valori delle proprietà persistenti e impostare le proprietà corrispondenti. Il `ApplyChanges` metodo `ProjectMgr` utilizza per ottenere i valori delle proprietà e persisterli nel file di progetto. Il metodo set `IsDirty` di proprietà imposta su true per indicare che le proprietà devono essere rese persistenti. La persistenza si verifica quando si salva il progetto o la soluzione.

5. Ricompilare la soluzione SimpleProject e avviare il debug. Verrà visualizzata l'istanza sperimentale.

6. Nell'istanza sperimentale, creare una nuova applicazione SimpleProject.In the experimental instance, create a new SimpleProject Application.

7. Visual Studio chiama la factory del progetto per creare un progetto usando il modello di Visual Studio.Visual Studio calls your project factory to create a project by using the Visual Studio template. Il nuovo *file Program.cs* viene aperto nell'editor di codice.

8. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni**, quindi **scegliere Proprietà**. Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

    ![Pagina delle proprietà progetto semplice](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testare la pagina delle proprietà del progettoTest the project property page
È ora possibile verificare se è possibile modificare e modificare i valori delle proprietà.

1. Nella finestra di dialogo **Pagine delle proprietà MyConsoleApplication** modificare **DefaultNamespace** in **MyApplication**.

2. Selezionare la proprietà **OutputType** , quindi scegliere **Libreria di classi**.

3. Fare clic su **Applica** e quindi su **OK**.

4. Riaprire la finestra di dialogo **Pagine delle proprietà** e verificare che le modifiche siano state rese persistenti.

5. Chiudere l'istanza sperimentale di Visual Studio.

6. Riaprire l'istanza sperimentale.

7. Riaprire la finestra di dialogo **Pagine delle proprietà** e verificare che le modifiche siano state rese persistenti.

8. Chiudere l'istanza sperimentale di Visual Studio.
    ![Chiudere l'istanza sperimentale](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
