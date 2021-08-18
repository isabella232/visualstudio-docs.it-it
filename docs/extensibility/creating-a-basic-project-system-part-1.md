---
title: Creating a Basic Project System, Part 1 | Microsoft Docs
description: Informazioni su come creare un tipo di progetto denominato extension.myproj. In Visual Studio, i progetti sono contenitori usati per organizzare i file di codice sorgente e altri asset.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a166f33222515163b330ac0f8a22a7d36b10177a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051222"
---
# <a name="create-a-basic-project-system-part-1"></a>Creare un sistema di progetto di base, parte 1
In Visual Studio i progetti sono i contenitori che gli sviluppatori usano per organizzare i file di codice sorgente e altri asset. I progetti vengono visualizzati come elementi figlio delle soluzioni **nel Esplora soluzioni**. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente e creare riferimenti a servizi Web, database e altre risorse.

 I progetti vengono definiti nei file di progetto, ad esempio un file *con estensione csproj* per un progetto Visual C#. È possibile creare un tipo di progetto personalizzato con la propria estensione di file di progetto. Per altre informazioni sui tipi di progetto, vedere [tipi Project .](../extensibility/internals/project-types.md)

> [!NOTE]
> Se è necessario estendere Visual Studio con un tipo di progetto personalizzato, è consigliabile sfruttare il sistema di progetto [Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), che offre numerosi vantaggi rispetto alla creazione di un sistema di progetto da zero:
>
> - Onboarding più semplice.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  L'uso di VSPS riduce il costo di onboarding a pochi clic prima di essere pronti per personalizzarlo in base alle proprie esigenze.
> - Manutenzione semplificata.  Sfruttando VSPS, è necessario gestire solo i propri scenari.  Viene gestita la manutenzione di tutta l'infrastruttura del sistema del progetto.
>
>   Se è necessario usare come destinazione versioni di Visual Studio precedenti a Visual Studio 2013, non sarà possibile usare VSPS in un'estensione Visual Studio.  In questo caso, questa procedura dettagliata è un buon punto di partenza.

 Questa procedura dettagliata illustra come creare un tipo di progetto con estensione *myproj.* Questa procedura dettagliata prende in prestito il sistema di progetto Visual C# esistente.

> [!NOTE]
> Per altri esempi di progetti di estensione, vedere [Esempi di VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

 Questa procedura dettagliata illustra come eseguire queste attività:

- Creare un tipo di progetto di base.

- Creare un modello di progetto di base.

- Registrare il modello di progetto con Visual Studio.

- Creare un'istanza del progetto aprendo la **finestra di dialogo Project** e quindi usando il modello.

- Creare una factory del progetto per il sistema del progetto.

- Creare un nodo di progetto per il sistema del progetto.

- Aggiungere icone personalizzate per il sistema del progetto.

- Implementare la sostituzione dei parametri di modello di base.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

 È anche necessario scaricare il codice sorgente per [Managed Package Framework per i progetti](https://github.com/tunnelvisionlabs/MPFProj10). Estrarre il file in un percorso accessibile alla soluzione che si sta per creare.

## <a name="create-a-basic-project-type"></a>Creare un tipo di progetto di base
 Creare un progetto VSIX C# denominato **SimpleProject.** (**File**  >  **Nuovo**  >  **Project** e visual **C#**  >  **Extensibility**  >  **VSIX Project**). Aggiungere un Visual Studio di elemento di progetto Esplora soluzioni (nel **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere Aggiungi nuovo elemento , quindi passare a  >   **Extensibility**  >  **Visual Studio Package**). Assegnare al file *il nome SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creazione di un modello di progetto di base
 A questo punto, è possibile modificare questo VSPackage di base per implementare il nuovo tipo di progetto con estensione *myproj.* Per creare un progetto basato sul tipo di progetto *myproj,* Visual Studio deve conoscere quali file, risorse e riferimenti aggiungere al nuovo progetto. Per fornire queste informazioni, inserire i file di progetto in una cartella del modello di progetto. Quando un utente usa il *progetto con estensione myproj* per creare un progetto, i file vengono copiati nel nuovo progetto.

### <a name="to-create-a-basic-project-template"></a>Per creare un modello di progetto di base

1. Aggiungere tre cartelle al progetto, una sotto l'altra: *Templates\Projects\SimpleProject.* In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto **SimpleProject,** scegliere Aggiungi **e** quindi fare clic su **Nuova cartella.** Assegnare alla cartella il *nome Templates*. Nella cartella *Modelli* aggiungere una cartella denominata *Projects*. Nella cartella *Progetti* aggiungere una cartella denominata *SimpleProject.*

2. Nella cartella *Templates\Projects\SimpleProject* aggiungere un file di immagine bitmap da usare come icona denominata *SimpleProject.ico*. Quando si fa clic **su Aggiungi**, viene aperto l'editor delle icone.

3. Rendere distintiva l'icona. Questa icona verrà visualizzata nella finestra **di dialogo Nuovo Project** più avanti nella procedura dettagliata.

    ![Icona Progetto semplice](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Salvare l'icona e chiudere l'editor delle icone.

5. Nella cartella *Templates\Projects\SimpleProject* aggiungere un **elemento Class** denominato *Program.cs.*

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
   > Questa non è la forma finale del *codice Program.cs.* I parametri di sostituzione verranno esaminati in un passaggio successivo. Potrebbero essere visualizzati errori di compilazione, ma se **buildAction** del file è **Content,** dovrebbe essere possibile compilare ed eseguire il progetto come di consueto.

7. Salvare il file.

8. Copiare il file *AssemblyInfo.cs* dalla *cartella Properties* alla *cartella Projects\SimpleProject.*

9. Nella cartella *Projects\SimpleProject* aggiungere un file XML denominato *SimpleProject.myproj.*

   > [!NOTE]
   > L'estensione del nome file per tutti i progetti di questo tipo *è myproj.* Se si vuole modificarlo, è necessario modificarlo ovunque sia menzionato nella procedura dettagliata.

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

12. Nella **finestra** Proprietà impostare  l'azione di compilazione di *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* e *SimpleProject.myproj* su **Contente** impostare le relative proprietà **Include in VSIX** su **True**.

    Questo modello di progetto descrive un progetto Visual C# di base con una configurazione di debug e una configurazione di rilascio. Il progetto include due file di origine, *AssemblyInfo.cs* e *Program.cs,* e diversi riferimenti ad assembly. Quando viene creato un progetto dal modello, il valore ProjectGuid viene automaticamente sostituito da un nuovo GUID.

    In **Esplora soluzioni**, la cartella **Templates** espansa dovrebbe essere visualizzata come segue:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Creare una factory di progetto di base
 È necessario indicare Visual Studio percorso della cartella del modello di progetto. A tale scopo, aggiungere un attributo alla classe VSPackage che implementa la factory del progetto in modo che il percorso del modello sia scritto nel Registro di sistema quando viene compilato il pacchetto VSPackage. Iniziare creando una factory di progetto di base identificata da un GUID di factory del progetto. Usare <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> l'attributo per connettere la factory del progetto alla `SimpleProjectPackage` classe .

### <a name="to-create-a-basic-project-factory"></a>Per creare una factory di progetto di base

1. Creare GUID per la factory del progetto (scegliere Crea **GUID** dal **menu** Strumenti) oppure usare quello nell'esempio seguente. Aggiungere i GUID alla classe `SimpleProjectPackage` accanto alla sezione con l'oggetto già `PackageGuidString` definito. I GUID devono essere sia in formato GUID che in formato stringa. Il codice risultante dovrebbe essere simile all'esempio seguente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Aggiungere una classe alla cartella *SimpleProject superiore* denominata *SimpleProjectFactory.cs.*

3. Aggiungere le seguenti direttive using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Aggiungere un attributo GUID alla `SimpleProjectFactory` classe . Il valore dell'attributo è il nuovo GUID della factory del progetto.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   È ora possibile registrare il modello di progetto.

### <a name="to-register-the-project-template"></a>Per registrare il modello di progetto

1. In *SimpleProjectPackage.cs* aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo alla classe , come indicato di `SimpleProjectPackage` seguito.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Ricompilare la soluzione e verificarne la compilazione senza errori.

    La ricompilazione registra il modello di progetto.

   I parametri `defaultProjectExtension` e `possibleProjectExtensions` sono impostati sull'estensione del nome file di progetto (*.myproj*). Il `projectTemplatesDirectory` parametro è impostato sul percorso relativo della cartella *Templates.* Durante la compilazione, questo percorso verrà convertito in una compilazione completa e aggiunto al Registro di sistema per registrare il sistema del progetto.

## <a name="test-the-template-registration"></a>Testare la registrazione del modello
 Registrazione modello indica Visual Studio percorso della cartella del modello di progetto in modo che Visual Studio possa visualizzare il nome del modello e l'icona nella finestra **di dialogo Project** nuovo modello.

### <a name="to-test-the-template-registration"></a>Per testare la registrazione del modello

1. Premere **F5 per** avviare il debug di un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale creare un nuovo progetto del tipo di progetto appena creato. Nella finestra **di dialogo Project** nuovo progetto verrà visualizzato **SimpleProject** in **Modelli installati**.

   A questo punto si dispone di una factory del progetto registrata. Tuttavia, non può ancora creare un progetto. Il pacchetto del progetto e la factory del progetto funzionano insieme per creare e inizializzare un progetto.

## <a name="add-the-managed-package-framework-code"></a>Aggiungere il codice del framework del pacchetto gestito
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.

- Importare i file del codice sorgente per Managed Package Framework.

    1. Scaricare il progetto SimpleProject **(in Esplora soluzioni** selezionare il nodo del progetto e scegliere Scarica **Project** dal menu di scelta rapida) e aprire il file di progetto nell'editor XML.

    2. Aggiungere i blocchi seguenti al file di progetto (appena sopra i \<Import> blocchi ). Impostare `ProjectBasePath` sul percorso del file *ProjectBase.files* nel codice del framework del pacchetto gestito appena scaricato. Potrebbe essere necessario aggiungere una barra rovesciata al percorso. In caso contrario, il progetto potrebbe non riuscire a trovare il codice sorgente del framework del pacchetto gestito.

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

        - `Microsoft.VisualStudio.Designer.Interfaces`(in *\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Per inizializzare la factory del progetto

1. Nel file *SimpleProjectPackage.cs* aggiungere la direttiva `using` seguente.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivare `SimpleProjectPackage` la classe da `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrare la factory del progetto. Aggiungere la riga seguente al `SimpleProjectPackage.Initialize` metodo , subito dopo `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementare la proprietà astratta `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. In *SimpleProjectFactory.cs* aggiungere la direttiva `using` seguente dopo le direttive `using` esistenti.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivare `SimpleProjectFactory` la classe da `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Aggiungere il metodo fittizio seguente alla `SimpleProjectFactory` classe . Questo metodo verrà implementato in una sezione successiva.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Aggiungere il campo e il costruttore seguenti alla `SimpleProjectFactory` classe . Questo riferimento viene memorizzato nella cache in un campo privato in modo che `SimpleProjectPackage` possa essere usato nell'impostazione di un sito del provider di servizi.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Ricompilare la soluzione e verificarne la compilazione senza errori.

## <a name="test-the-project-factory-implementation"></a>Testare l'implementazione della factory del progetto
 Verificare se viene chiamato il costruttore per l'implementazione della factory del progetto.

### <a name="to-test-the-project-factory-implementation"></a>Per testare l'implementazione della factory del progetto

1. Nel file *SimpleProjectFactory.cs* impostare un punto di interruzione nella riga seguente nel `SimpleProjectFactory` costruttore .

    ```csharp
    this.package = package;
    ```

2. Premere **F5 per** avviare un'istanza sperimentale di Visual Studio.

3. Nell'istanza sperimentale iniziare a creare un nuovo progetto. Nella finestra **di dialogo Project** nuovo progetto selezionare il tipo di progetto **SimpleProject** e quindi fare clic su **OK.** L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

4. Cancellare il punto di interruzione e arrestare il debug. Poiché non è ancora stato creato un nodo di progetto, il codice di creazione del progetto genera comunque eccezioni.

## <a name="extend-the-projectnode-class"></a>Estendere la classe ProjectNode
 È ora possibile `SimpleProjectNode` implementare la classe , che deriva dalla `ProjectNode` classe . La `ProjectNode` classe base gestisce le attività di creazione del progetto seguenti:

- Copia il file del modello di progetto *SimpleProject.myproj* nella nuova cartella del progetto. La copia viene rinominata in base al nome immesso nella finestra **di dialogo Project** nuova copia. Il `ProjectGuid` valore della proprietà viene sostituito da un nuovo GUID.

- Attraversa i MSBuild del file del modello di progetto *SimpleProject.myproj* e cerca `Compile` gli elementi . Per ogni `Compile` file di destinazione, copia il file nella nuova cartella del progetto.

  La classe `SimpleProjectNode` derivata gestisce queste attività:

- Abilita le icone per i nodi di progetto e file **Esplora soluzioni** da creare o selezionare.

- Consente di impostare sostituzioni aggiuntive dei parametri del modello di progetto.

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

   Questa `SimpleProjectNode` implementazione della classe ha questi metodi sottoposti a override:

- `ProjectGuid`, che restituisce il GUID della factory del progetto.

- `ProjectType`, che restituisce il nome localizzato del tipo di progetto.

- `AddFileFromTemplate`, che copia i file selezionati dalla cartella del modello al progetto di destinazione. Questo metodo viene implementato ulteriormente in una sezione successiva.

  Il `SimpleProjectNode` costruttore, come il `SimpleProjectFactory` costruttore , memorizza nella cache un riferimento in un campo privato per un uso `SimpleProjectPackage` successivo.

  Per connettere la classe alla classe , è necessario creare un'istanza di un nuovo nel metodo e memorizzarla nella cache in un campo privato per `SimpleProjectFactory` `SimpleProjectNode` un uso `SimpleProjectNode` `SimpleProjectFactory.CreateProject` successivo.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Per connettere la classe factory del progetto e la classe node

1. Nel file *SimpleProjectFactory.cs* aggiungere la direttiva `using` seguente:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Sostituire il `SimpleProjectFactory.CreateProject` metodo usando il codice seguente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Ricompilare la soluzione e verificarne la compilazione senza errori.

## <a name="test-the-projectnode-class"></a>Testare la classe ProjectNode
 Testare la factory del progetto per verificare se crea una gerarchia di progetto.

### <a name="to-test-the-projectnode-class"></a>Per testare la classe ProjectNode

1. Premere **F5** per avviare il debug. Nell'istanza sperimentale creare un nuovo SimpleProject.

2. Visual Studio chiamare la factory del progetto per creare un progetto.

3. Chiudere l'istanza sperimentale di Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Aggiungere un'icona del nodo del progetto personalizzato
 L'icona del nodo del progetto nella sezione precedente è un'icona predefinita. È possibile modificarlo in un'icona personalizzata.

### <a name="to-add-a-custom-project-node-icon"></a>Per aggiungere un'icona del nodo del progetto personalizzato

1. Nella cartella **Risorse** aggiungere un file bitmap denominato *SimpleProjectNode.bmp*.

2. Nelle finestre **Proprietà** ridurre la bitmap a 16 di 16 pixel. Rendere distintiva la bitmap.

    ![Comando Progetto semplice](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Nella finestra **Proprietà** modificare l'azione **Di compilazione** della bitmap in **Risorsa incorporata.**

4. In *SimpleProjectNode.cs* aggiungere le `using` direttive seguenti:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aggiungere il campo statico e il costruttore seguenti alla `SimpleProjectNode` classe .

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Aggiungere la proprietà seguente all'inizio della `SimpleProjectNode` classe .

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

   Durante la costruzione statica, recupera la bitmap del nodo del progetto dalle risorse del manifesto dell'assembly e la memorizza nella cache in un `SimpleProjectNode` campo privato per un uso successivo. Si noti la sintassi del <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> percorso dell'immagine. Per visualizzare i nomi delle risorse manifesto incorporate in un assembly, usare il <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metodo . Quando questo metodo viene applicato `SimpleProject` all'assembly, i risultati devono essere i seguenti:

- *SimpleProject.Resources.resources*

- *VisualStudio. Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio. Project. DontShowAgainDialog.resources*

- *Microsoft.VisualStudio. Project. SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la costruzione dell'istanza, la classe di base caricaResources.imagelis.bmp, in cui sono incorporate `ProjectNode` bitmap 16 ** x 16 di uso comune da *Resources\imagelis.bmp*. Questo elenco di bitmap viene reso disponibile per `SimpleProjectNode` come `ImageHandler.ImageList` . `SimpleProjectNode` aggiunge la bitmap del nodo del progetto all'elenco. L'offset della bitmap del nodo del progetto nell'elenco di immagini viene memorizzato nella cache per un uso successivo come valore della proprietà `ImageIndex` pubblica. Visual Studio usa questa proprietà per determinare quale bitmap visualizzare come icona del nodo del progetto.

## <a name="test-the-custom-project-node-icon"></a>Testare l'icona del nodo del progetto personalizzato
 Testare la factory del progetto per verificare se crea una gerarchia di progetto con l'icona del nodo del progetto personalizzato.

### <a name="to-test-the-custom-project-node-icon"></a>Per testare l'icona del nodo del progetto personalizzato

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. Nel progetto appena creato si noti cheSimpleProjectNode.bmp *come* icona del nodo del progetto.

     ![Progetto semplice, nuovo nodo di progetto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Aprire *Program.cs* nell'editor di codice. Verrà visualizzato codice sorgente simile al codice seguente.

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

     Si noti che i parametri $nameSpace$ e $className$ non hanno nuovi valori. Nella sezione successiva si apprenderà come implementare la sostituzione dei parametri di modello.

## <a name="substitute-template-parameters"></a>Sostituire i parametri del modello
 In una sezione precedente è stato registrato il modello di progetto con Visual Studio usando `ProvideProjectFactory` l'attributo . La registrazione del percorso di una cartella modello in questo modo consente di abilitare la sostituzione dei parametri di modello di base eseguendo l'override ed espandendo la `ProjectNode.AddFileFromTemplate` classe . Per altre informazioni, vedere [New project generation: Under the hood, part two](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Aggiungere ora il codice di sostituzione alla `AddFileFromTemplate` classe .

### <a name="to-substitute-template-parameters"></a>Per sostituire i parametri del modello

1. Nel file *SimpleProjectNode.cs* aggiungere la direttiva `using` seguente.

   ```csharp
   using System.IO;
   ```

2. Sostituire il `AddFileFromTemplate` metodo usando il codice seguente.

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

3. Impostare un punto di interruzione nel metodo subito dopo l'istruzione `className` di assegnazione.

   Le istruzioni di assegnazione determinano valori ragionevoli per uno spazio dei nomi e un nuovo nome di classe. Le due `ProjectNode.FileTemplateProcessor.AddReplace` chiamate al metodo sostituiscono i valori dei parametri di modello corrispondenti usando questi nuovi valori.

## <a name="test-the-template-parameter-substitution"></a>Testare la sostituzione dei parametri di modello
 È ora possibile testare la sostituzione dei parametri di modello.

### <a name="to-test-the-template-parameter-substitution"></a>Per testare la sostituzione dei parametri di modello

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. L'esecuzione si interrompe in corrispondenza del punto di interruzione nel `AddFileFromTemplate` metodo .

3. Esaminare i valori per i `nameSpace` parametri `className` e .

   - `nameSpace`viene assegnato il valore dell'elemento nel file del modello di progetto \<RootNamespace> *\Templates\Projects\SimpleProject\SimpleProject.myproj.* In questo caso il valore è `MyRootNamespace`.

   - `className` viene assegnato il valore del nome del file di origine della classe, senza l'estensione del nome file. In questo caso, il primo file da copiare nella cartella di destinazione è *AssemblyInfo.cs*; Pertanto, il valore di className è `AssemblyInfo` .

4. Rimuovere il punto di interruzione e premere **F5** per continuare l'esecuzione.

    Visual Studio completare la creazione di un progetto.

5. Aprire *Program.cs* nell'editor di codice. Verrà visualizzato codice sorgente simile al codice seguente.

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

    Si noti che lo spazio dei nomi è `MyRootNamespace` ora e il nome della classe è ora `Program` .

6. Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX!!!" nella finestra della console.

    ![Comando Progetto semplice](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Congratulazioni! È stato implementato un sistema di progetto gestito di base.
