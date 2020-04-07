---
title: Creazione di un sistema di progetto di base, parte 1 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739731"
---
# <a name="create-a-basic-project-system-part-1"></a>Creare un sistema di progetto di base, parte 1
In Visual Studio i progetti sono i contenitori utilizzati dagli sviluppatori per organizzare i file di codice sorgente e altri asset. I progetti vengono visualizzati come elementi figlio di soluzioni in **Esplora soluzioni**. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente e creare riferimenti a servizi Web, database e altre risorse.

 I progetti vengono definiti nei file di progetto, ad esempio in un file *con estensione csproj* per un progetto di Visual C. È possibile creare un tipo di progetto personalizzato con estensione di file di progetto. Per ulteriori informazioni sui tipi di progetto, vedere [Tipi di progetto](../extensibility/internals/project-types.md).

> [!NOTE]
> Se è necessario estendere Visual Studio con un tipo di progetto personalizzato, è consigliabile sfruttare il sistema di progetto di Visual Studio (VSPS) che presenta una serie di vantaggi rispetto alla compilazione di un sistema di progetto da zero:If you need to extend Visual Studio with a custom project type, we strongly recommend leveraging the [Visual Studio project system](https://github.com/Microsoft/VSProjectSystem) (VSPS) which has a number of advantages over building a project system from scratch:
>
> - Più facile onboarding.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  Sfruttando VSPS riduce il costo di onboarding a pochi clic prima di essere pronti a personalizzarlo in base alle proprie esigenze.
> - Manutenzione più semplice.  Sfruttando VSPS, è sufficiente mantenere i propri scenari.  Gestiamo la manutenzione di tutta l'infrastruttura del sistema di progetto.
>
>   Se è necessario utilizzare VSPS in un'estensione di Visual Studio di destinazione rispetto a Visual Studio 2013, non sarà possibile sfruttare VSPS in un'estensione di Visual Studio.If you need to target versions of Visual Studio older than Visual Studio 2013, you will not be able to leverage VSPS in a Visual Studio extension.  In questo caso, questa procedura dettagliata è un buon punto di partenza.

 In questa procedura dettagliata viene illustrato come creare un tipo di progetto con estensione *myproj*di progetto. In questa procedura dettagliata viene presa in prestito dal sistema di progetto Visual C.

> [!NOTE]
> Per altri esempi di progetti di estensione, vedere [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 In questa procedura dettagliata viene illustrato come eseguire queste attività:This walkthrough teaches how to accomplish these tasks:

- Creare un tipo di progetto di base.

- Creare un modello di progetto di base.

- Registrare il modello di progetto con Visual Studio.Register the project template with Visual Studio.

- Creare un'istanza di progetto aprendo la finestra di dialogo **Nuovo progetto** e quindi utilizzando il modello.

- Creare una factory del progetto per il sistema del progetto.

- Creare un nodo di progetto per il sistema del progetto.

- Aggiungere icone personalizzate per il sistema del progetto.

- Implementare la sostituzione dei parametri di modello di base.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

 È inoltre necessario scaricare il codice sorgente per il [Framework di pacchetto gestito per i progetti](https://github.com/tunnelvisionlabs/MPFProj10). Estrarre il file in un percorso accessibile alla soluzione che si intende creare.

## <a name="create-a-basic-project-type"></a>Creare un tipo di progetto di baseCreate a basic project type
 Creare un progetto VSIX in C, denominato **SimpleProject**. (**File** > **Nuovo** > **progetto** e quindi Progetto**VSIX**di**estensibilità** > di Visual **C** > . Aggiungere un modello di elemento di progetto di pacchetto di Visual Studio (in **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **nuovo elemento**, quindi passare a **Extensibility** > **Visual Studio Package**). Denominare il file *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creazione di un modello di progetto di base
 A questo punto, è possibile modificare questo vsPackage di base per implementare il nuovo tipo di progetto *con estensione myproj.* Per creare un progetto basato sul tipo di progetto *con estensione myproj,* Visual Studio deve sapere quali file, risorse e riferimenti aggiungere al nuovo progetto. Per fornire queste informazioni, inserire i file di progetto in una cartella del modello di progetto. Quando un utente utilizza il progetto *con estensione myproj* per creare un progetto, i file vengono copiati nel nuovo progetto.

### <a name="to-create-a-basic-project-template"></a>Per creare un modello di progetto di baseTo create a basic project template

1. Aggiungere al progetto tre cartelle, una nell'altra: *Modelli, Progetti e SimpleProject*. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto **SimpleProject** , **scegliere Aggiungi**, quindi fare clic su **Nuova cartella**. Assegnare alla cartella il nome *Modelli*. Nella cartella *Modelli* aggiungere una cartella denominata *Progetti*. Nella cartella *Progetti* aggiungere una cartella denominata *SimpleProject*.)

2. Aggiungere *Templates\Projects\SimpleProject* un file di immagine bitmap da utilizzare come icona denominata *SimpleProject.ico*. Quando si fa clic su **Aggiungi**, viene aperto l'editor di icone.

3. Rendere l'icona distintiva. Questa icona verrà visualizzata nella finestra di dialogo **Nuovo progetto** più avanti nella procedura dettagliata.

    ![Icona Progetto semplice](../extensibility/media/simpleprojicon.png "Proprietà SimpleProjIcon")

4. Salvare l'icona e chiudere l'editor di icone.

5. Nella cartella *Templates,Projects/SimpleProject* aggiungere un elemento **Class** denominato *Program.cs*.

6. Sostituire il codice esistente con le righe seguenti.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Questa non è la forma finale del codice *Program.cs;* i parametri di sostituzione verranno trattati in un passaggio successivo. È possibile visualizzare errori di compilazione, ma finché il file **BuildAction** è **Content**, dovrebbe essere possibile compilare ed eseguire il progetto come di consueto.

7. Salvare il file.

8. Copiare il *file di AssemblyInfo.cs* dalla cartella *Proprietà* alla cartella *Progetti/ProgettoSemplice.*

9. Nella cartella *Progetti/Progetto/_* aggiungere un file XML denominato *SimpleProject.myproj*.

   > [!NOTE]
   > L'estensione del nome file per tutti i progetti di questo tipo è *.myproj*. Se si desidera modificarlo, è necessario modificarlo ovunque sia menzionato nella procedura dettagliata.

10. Sostituire il contenuto esistente con le righe seguenti.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Salvare il file.

12. Nella finestra **Proprietà** impostare **l'azione** di compilazione *di AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*e *SimpleProject.myproj* su **Contenuto**, quindi includere le relative proprietà **Include in VSIX** su **True**.

    In questo modello di progetto viene descritto un progetto di base di Visual C, che dispone sia di una configurazione Di debug che di una configurazione di rilascio. Il progetto include due file di origine, *AssemblyInfo.cs* e *Program.cs*, e diversi riferimenti all'assembly. Quando viene creato un progetto dal modello, il valore ProjectGuid viene sostituito automaticamente da un nuovo GUID.

    In **Esplora soluzioni**la cartella **Modelli** espansa dovrebbe essere visualizzata come segue:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Creare una factory di progetto di baseCreate a basic project factory
 È necessario indicare a Visual Studio il percorso della cartella del modello di progetto. A tale scopo, aggiungere un attributo per il VSPackage classe che implementa la factory del progetto in modo che il percorso del modello viene scritto nel Registro di sistema quando viene compilato il pacchetto VSPackage. Iniziare creando una factory del progetto di base identificata da un GUID di factory del progetto. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> l'attributo per connettere la factory del progetto alla `SimpleProjectPackage` classe .

### <a name="to-create-a-basic-project-factory"></a>Per creare una factory di progetto di baseTo create a basic project factory

1. Creare GUID per la factory del progetto (scegliere **Crea GUID**dal menu **Strumenti** ) oppure utilizzare quello nell'esempio seguente. Aggiungere i GUID alla `SimpleProjectPackage` classe accanto alla sezione `PackageGuidString`con il già definito . I GUID devono essere in formato GUID e stringa. Il codice risultante dovrebbe essere simile all'esempio seguente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Aggiungere una classe alla cartella *SimpleProject* superiore denominata *SimpleProjectFactory.cs*.

3. Aggiungere le seguenti direttive using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Aggiungere un attributo `SimpleProjectFactory` GUID alla classe. Il valore dell'attributo è il nuovo GUID della factory del progetto.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Ora è possibile registrare il modello di progetto.

### <a name="to-register-the-project-template"></a>Per registrare il modello di progetto

1. In *SimpleProjectPackage.cs*, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> aggiungere `SimpleProjectPackage` un attributo alla classe, come indicato di seguito.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Ricompilare la soluzione e verificare che venga compilata senza errori.

    La ricostruzione registra il modello di progetto.

   I `defaultProjectExtension` parametri `possibleProjectExtensions` e vengono impostati sull'estensione del nome file di progetto (*.myproj*). Il `projectTemplatesDirectory` parametro viene impostato sul percorso relativo della cartella *Templates.* Durante la compilazione, questo percorso verrà convertito in una compilazione completa e aggiunto al Registro di sistema per registrare il sistema del progetto.

## <a name="test-the-template-registration"></a>Testare la registrazione del modello
 La registrazione del modello indica a Visual Studio il percorso della cartella del modello di progetto in modo che Visual Studio possa visualizzare il nome e l'icona del modello nella finestra di dialogo **Nuovo progetto.**

### <a name="to-test-the-template-registration"></a>Per testare la registrazione del modello

1. Premere **F5** per avviare il debug di un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, creare un nuovo progetto del tipo di progetto appena creato. Nella finestra di dialogo **Nuovo progetto** verrà visualizzato **SimpleProject** in **Modelli installati**.

   A questo punto si dispone di una factory del progetto che viene registrata. Tuttavia, non può ancora creare un progetto. Il pacchetto del progetto e la factory del progetto lavorano insieme per creare e inizializzare un progetto.

## <a name="add-the-managed-package-framework-code"></a>Aggiungere il codice del framework di pacchetto gestitoAdd the Managed Package Framework code
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.

- Importare i file di codice sorgente per il framework del pacchetto gestito.

    1. Scaricare il progetto SimpleProject (in **Esplora soluzioni**, selezionare il nodo del progetto e dal menu di scelta rapida fare clic su **Scarica progetto**.) e aprire il file di progetto nell'editor XML.

    2. Aggiungere i blocchi seguenti al file \<di progetto (appena sopra i blocchi di> di importazione). Impostare `ProjectBasePath` sul percorso del file *ProjectBase.files* nel codice del framework del pacchetto gestito appena scaricato. Potrebbe essere necessario aggiungere una barra rovesciata al nome del percorso. In caso contrario, il progetto potrebbe non riuscire a trovare il codice sorgente del framework del pacchetto gestito.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Non dimenticare la barra rovesciata alla fine del percorso.

    3. Ricaricare il progetto.

    4. Aggiungere riferimenti agli assembly riportati di seguito:

        - `Microsoft.VisualStudio.Designer.Interfaces`(in * \<VSSDK installare> , VisualStudioIntegration , Common , Assemblies , v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Per inizializzare la factory del progetto

1. Nel file *SimpleProjectPackage.cs* aggiungere `using` la direttiva seguente.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivare `SimpleProjectPackage` la `Microsoft.VisualStudio.Package.ProjectPackage`classe da .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrare la factory del progetto. Aggiungere la riga `SimpleProjectPackage.Initialize` seguente al `base.Initialize`metodo , subito dopo .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementare la `ProductUserContext`proprietà astratta :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. In *SimpleProjectFactory.cs*aggiungere `using` la direttiva `using` seguente dopo le direttive esistenti.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivare `SimpleProjectFactory` la `ProjectFactory`classe da .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aggiungere il seguente metodo fittizio alla `SimpleProjectFactory` classe. Questo metodo verrà implementato in una sezione successiva.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Aggiungere il campo e `SimpleProjectFactory` il costruttore seguenti alla classe. Questo `SimpleProjectPackage` riferimento viene memorizzato nella cache in un campo privato in modo che possa essere utilizzato nell'impostazione di un sito del provider di servizi.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Ricompilare la soluzione e verificare che venga compilata senza errori.

## <a name="test-the-project-factory-implementation"></a>Testare l'implementazione della factory del progettoTest the project factory implementation
 Verificare se viene chiamato il costruttore per l'implementazione factory del progetto.

### <a name="to-test-the-project-factory-implementation"></a>Per testare l'implementazione della factory del progettoTo test the project factory implementation

1. Nel *file SimpleProjectFactory.cs* impostare un punto di `SimpleProjectFactory` interruzione nella riga seguente del costruttore.

    ```csharp
    this.package = package;
    ```

2. Premere **F5** per avviare un'istanza sperimentale di Visual Studio.

3. Nell'istanza sperimentale, iniziare a creare un nuovo progetto. Nella finestra di dialogo **Nuovo progetto** selezionare il tipo di progetto **SimpleProject** , quindi scegliere **OK**. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

4. Cancellare il punto di interruzione e interrompere il debug. Poiché non è ancora stato creato un nodo di progetto, il codice di creazione del progetto genera comunque eccezioni.

## <a name="extend-the-projectnode-class"></a>Estendere la classe ProjectNodeExtend the ProjectNode class
 A questo punto `SimpleProjectNode` è possibile implementare `ProjectNode` la classe , che deriva dalla classe . La `ProjectNode` classe base gestisce le attività seguenti di creazione del progetto:The base class handles the following tasks of project creation:

- Copia il file del modello di progetto, *SimpleProject.myproj*, nella nuova cartella di progetto. La copia viene rinominata in base al nome immesso nella finestra di dialogo **Nuovo progetto.** Il `ProjectGuid` valore della proprietà viene sostituito da un nuovo GUID.

- Attraversa gli elementi MSBuild del file del modello di progetto, `Compile` *SimpleProject.myproj*, e cerca gli elementi. Per `Compile` ogni file di destinazione, copia il file nella nuova cartella del progetto.

  La `SimpleProjectNode` classe derivata gestisce queste attività:The derived class handles these tasks:

- Consente di creare o selezionare le icone per i nodi di progetto e file in **Esplora soluzioni.**

- Consente di specificare ulteriori sostituzioni di parametri del modello di progetto.

### <a name="to-extend-the-projectnode-class"></a>Per estendere la classe ProjectNode

1. Aggiungere una classe denominata `SimpleProjectNode.cs`.

2. Sostituire il codice esistente con quello seguente.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Questa `SimpleProjectNode` implementazione della classe dispone di questi metodi sottoposti a override:This class implementation has these overridden methods:

- `ProjectGuid`, che restituisce il GUID di factory del progetto.

- `ProjectType`, che restituisce il nome localizzato del tipo di progetto.

- `AddFileFromTemplate`, che copia i file selezionati dalla cartella dei modelli al progetto di destinazione. Questo metodo viene ulteriormente implementato in una sezione successiva.

  Il `SimpleProjectNode` costruttore, `SimpleProjectFactory` come il `SimpleProjectPackage` costruttore, memorizza nella cache un riferimento in un campo privato per un utilizzo successivo.

  Per connettere `SimpleProjectFactory` la `SimpleProjectNode` classe alla classe, `SimpleProjectNode` è `SimpleProjectFactory.CreateProject` necessario creare un'istanza di un nuovo nel metodo e memorizzarlo nella cache in un campo privato per un utilizzo successivo.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Per connettere la classe factory del progetto e la classe node

1. Nel file *SimpleProjectFactory.cs* aggiungere `using` la direttiva seguente:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Sostituire `SimpleProjectFactory.CreateProject` il metodo utilizzando il codice seguente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Ricompilare la soluzione e verificare che venga compilata senza errori.

## <a name="test-the-projectnode-class"></a>Testare la classe ProjectNodeTest the ProjectNode class
 Testare la factory del progetto per verificare se crea una gerarchia di progetto.

### <a name="to-test-the-projectnode-class"></a>Per testare la classe ProjectNode

1. Premere **F5** per avviare il debug. Nell'istanza sperimentale, creare un nuovo SimpleProject.In the experimental instance, create a new SimpleProject.

2. Visual Studio deve chiamare la factory del progetto per creare un progetto.

3. Chiudere l'istanza sperimentale di Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Aggiungere un'icona del nodo di progetto personalizzatoAdd a custom project node icon
 L'icona del nodo del progetto nella sezione precedente è un'icona predefinita. È possibile modificarlo in un'icona personalizzata.

### <a name="to-add-a-custom-project-node-icon"></a>Per aggiungere un'icona del nodo di progetto personalizzatoTo add a custom project node icon

1. Nella cartella **Risorse** aggiungere un file bitmap denominato *SimpleProjectNode.bmp*.

2. Nelle finestre **Proprietà,** ridurre la bitmap a 16 x 16 pixel. Rendere la bitmap distintiva.

    ![Comando Progetto semplice](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm (informazioni in base ai modelli semplici)")

3. Nella finestra **Proprietà** modificare l'azione **Compila** della bitmap in **Risorsa incorporata**.

4. In *SimpleProjectNode.cs*aggiungere `using` le direttive seguenti:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aggiungere il campo statico e `SimpleProjectNode` il costruttore seguenti alla classe.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aggiungere la proprietà seguente all'inizio della `SimpleProjectNode` classe.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Sostituire il costruttore di istanza con il codice seguente.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Durante la `SimpleProjectNode` costruzione statica, recupera la bitmap del nodo del progetto dalle risorse del manifesto dell'assembly e la memorizza nella cache in un campo privato per un utilizzo successivo. Si noti <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> la sintassi del percorso dell'immagine. Per visualizzare i nomi delle risorse del manifesto <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> incorporate in un assembly, utilizzare il metodo . Quando questo metodo viene `SimpleProject` applicato all'assembly, i risultati devono essere i seguenti:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la costruzione `ProjectNode` dell'istanza, la classe base carica *Resources.imagelis.bmp*, in cui sono incorporate bitmap 16 x 16 da *Resources , imagelis.bmp*. Questo elenco bitmap viene `SimpleProjectNode` `ImageHandler.ImageList`reso disponibile come . `SimpleProjectNode`aggiunge la bitmap del nodo del progetto all'elenco. L'offset della bitmap del nodo del progetto nell'elenco immagini `ImageIndex` viene memorizzato nella cache per un utilizzo successivo come valore della proprietà pubblica. Visual Studio usa questa proprietà per determinare quale bitmap visualizzare come icona del nodo del progetto.

## <a name="test-the-custom-project-node-icon"></a>Testare l'icona del nodo del progetto personalizzatoTest the custom project node icon
 Testare la factory del progetto per verificare se crea una gerarchia di progetto con l'icona del nodo del progetto personalizzato.

### <a name="to-test-the-custom-project-node-icon"></a>Per testare l'icona del nodo del progetto personalizzatoTo test the custom project node icon

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.Start debugging, and in the experimental instance create a new SimpleProject.

2. Nel progetto appena creato, si noti che *SimpleProjectNode.bmp* viene utilizzato come icona del nodo del progetto.

     ![Progetto semplice, nuovo nodo di progetto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode (SimpleProjNewProjectNode)")

3. Aprire *Program.cs* nell'editor di codice. Verrà visualizzato il codice sorgente simile al codice seguente.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Si noti che i parametri di modello $nameSpace e $className non dispongono di nuovi valori. Si apprenderà come implementare la sostituzione dei parametri di modello nella sezione successiva.

## <a name="substitute-template-parameters"></a>Sostituzione dei parametri del modello
 In una sezione precedente è stato registrato il `ProvideProjectFactory` modello di progetto con Visual Studio usando l'attributo . La registrazione del percorso di una cartella di modelli in questo modo consente `ProjectNode.AddFileFromTemplate` di abilitare la sostituzione dei parametri di modello di base eseguendo l'override e l'espansione della classe. Per ulteriori informazioni, vedere [Generazione di nuovi progetti: sotto il cofano, parte due](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Aggiungere ora il `AddFileFromTemplate` codice sostitutivo alla classe.

### <a name="to-substitute-template-parameters"></a>Per sostituire i parametri del modello

1. Nel file *SimpleProjectNode.cs* aggiungere `using` la direttiva seguente.

   ```csharp
   using System.IO;
   ```

2. Sostituire `AddFileFromTemplate` il metodo utilizzando il codice seguente.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Impostare un punto di interruzione `className` nel metodo, subito dopo l'istruzione di assegnazione.

   Le istruzioni di assegnazione determinano valori ragionevoli per uno spazio dei nomi e un nuovo nome di classe. Le `ProjectNode.FileTemplateProcessor.AddReplace` due chiamate al metodo sostituiscono i valori dei parametri di modello corrispondenti utilizzando questi nuovi valori.

## <a name="test-the-template-parameter-substitution"></a>Testare la sostituzione dei parametri di modelloTest the template parameter substitution
 A questo punto è possibile testare la sostituzione dei parametri di modello.

### <a name="to-test-the-template-parameter-substitution"></a>Per testare la sostituzione dei parametri di modelloTo test the template parameter substitution

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.Start debugging, and in the experimental instance create a new SimpleProject.

2. L'esecuzione si interrompe `AddFileFromTemplate` in corrispondenza del punto di interruzione nel metodo.

3. Esaminare i `nameSpace` valori `className` per i parametri e .

   - `nameSpace`viene assegnato il \<valore dell'elemento> RootNamespace nel file del modello di progetto *.* In questo caso il valore è `MyRootNamespace`.

   - `className`viene assegnato il valore del nome del file di origine della classe, senza l'estensione del nome file. In questo caso, il primo file da copiare nella cartella di destinazione è *AssemblyInfo.cs;* pertanto, il valore `AssemblyInfo`di className è .

4. Rimuovere il punto di interruzione e premere **F5** per continuare l'esecuzione.

    Visual Studio deve completare la creazione di un progetto.

5. Aprire *Program.cs* nell'editor di codice. Verrà visualizzato il codice sorgente simile al codice seguente.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Si noti che `MyRootNamespace` lo spazio dei `Program`nomi è ora e il nome della classe è ora .

6. Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX!!!" nella finestra della console.

    ![Comando Progetto semplice](../extensibility/media/simpleprojcommand.png "Comando SimpleProjCommand")

   Congratulazioni! È stato implementato un sistema di progetto gestito di base.
