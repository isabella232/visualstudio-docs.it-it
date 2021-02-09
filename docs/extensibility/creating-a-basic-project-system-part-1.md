---
title: Creazione di un sistema di progetto di base, parte 1 | Microsoft Docs
description: Informazioni su come creare un tipo di progetto denominato Extension. PROG. In Visual Studio i progetti sono contenitori usati per organizzare i file del codice sorgente e altri asset.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b21ef736e69c962db389a7bb1a3eb284ebdd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887367"
---
# <a name="create-a-basic-project-system-part-1"></a>Creazione di un sistema di progetto di base, parte 1
In Visual Studio i progetti sono i contenitori usati dagli sviluppatori per organizzare i file del codice sorgente e altri asset. I progetti vengono visualizzati come elementi figlio di soluzioni nel **Esplora soluzioni**. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente e creare riferimenti a servizi Web, database e altre risorse.

 I progetti vengono definiti nei file di progetto, ad esempio un file con *estensione csproj* per un progetto Visual C#. È possibile creare un tipo di progetto personalizzato con estensione del nome di file del progetto. Per ulteriori informazioni sui tipi di progetto, vedere [tipi di progetto](../extensibility/internals/project-types.md).

> [!NOTE]
> Se è necessario estendere Visual Studio con un tipo di progetto personalizzato, è consigliabile sfruttare il sistema di [progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsps), che presenta diversi vantaggi rispetto alla compilazione di un sistema di progetto da zero:
>
> - Onboarding più semplice.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  L'uso di VSPS consente di ridurre i costi di onboarding in pochi clic prima di essere pronti per personalizzarli in base alle esigenze.
> - Manutenzione semplificata.  Sfruttando VSPS, è sufficiente gestire i propri scenari.  Viene gestita la conservazione di tutta l'infrastruttura del sistema del progetto.
>
>   Se è necessario destinare le versioni di Visual Studio precedenti a Visual Studio 2013, non sarà possibile sfruttare VSPS in un'estensione di Visual Studio.  In tal caso, questa procedura dettagliata è una posizione ideale per iniziare.

 Questa procedura dettagliata illustra come creare un tipo di progetto con estensione del nome file di progetto *. PROG*. Questa procedura dettagliata prende in prestito dal sistema del progetto Visual C# esistente.

> [!NOTE]
> Per altri esempi di progetti di estensione, vedere [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Questa procedura dettagliata illustra come eseguire queste attività:

- Creare un tipo di progetto di base.

- Creare un modello di progetto di base.

- Registrare il modello di progetto con Visual Studio.

- Creare un'istanza del progetto aprendo la finestra di dialogo **nuovo progetto** e quindi usando il modello.

- Creare una factory di progetto per il sistema del progetto.

- Creare un nodo di progetto per il sistema del progetto.

- Aggiungere icone personalizzate per il sistema del progetto.

- Implementare la sostituzione del parametro di modello di base.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 È inoltre necessario scaricare il codice sorgente per il [Framework di pacchetto gestito per i progetti](https://github.com/tunnelvisionlabs/MPFProj10). Estrarre il file in un percorso accessibile alla soluzione che si vuole creare.

## <a name="create-a-basic-project-type"></a>Creare un tipo di progetto di base
 Creare un progetto VSIX C# denominato **SimpleProject**. (**File**  >  **Nuovo**  >  **Progetto e** quindi **Visual C#**  >  **Extensibility**  >  **progetto VSIX**). Aggiungere un modello di elemento di progetto di pacchetto di Visual Studio (nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**, quindi passare a **estendibilità**  >  **Visual Studio Package**). Denominare il file *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creazione di un modello di progetto di base
 A questo punto, è possibile modificare questo pacchetto VSPackage di base per implementare il nuovo tipo di progetto *. PROG* . Per creare un progetto basato sul tipo di progetto *. PROG* , è necessario che Visual Studio conosca i file, le risorse e i riferimenti da aggiungere al nuovo progetto. Per fornire queste informazioni, inserire i file di progetto in una cartella del modello di progetto. Quando un utente usa il progetto *. PROG* per creare un progetto, i file vengono copiati nel nuovo progetto.

### <a name="to-create-a-basic-project-template"></a>Per creare un modello di progetto di base

1. Aggiungere tre cartelle al progetto, una sotto l'altra: *Templates\Projects\SimpleProject*. (In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo del progetto **SimpleProject** , scegliere **Aggiungi**, quindi fare clic su **nuova cartella**. Assegnare un nome ai *modelli* di cartella. Nella cartella *templates* aggiungere una cartella denominata *Projects*. Nella cartella *progetti* aggiungere una cartella denominata *SimpleProject*.

2. Nella cartella *Templates\Projects\SimpleProject* aggiungere un file di immagine bitmap da usare come icona denominata *SimpleProject. ico*. Quando si fa clic su **Aggiungi**, viene aperto l'editor di icone.

3. Rendere l'icona distinta. Questa icona verrà visualizzata nella finestra di dialogo **nuovo progetto** più avanti nella procedura dettagliata.

    ![Icona Progetto semplice](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Salvare l'icona e chiudere l'editor di icone.

5. Nella cartella *Templates\Projects\SimpleProject* aggiungere un elemento **classe** denominato *Program.cs*.

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
   > Non si tratta del formato finale del codice *Program.cs* . i parametri di sostituzione verranno gestiti in un passaggio successivo. È possibile che vengano visualizzati errori di compilazione, ma purché il **BuildAction** del file sia **contenuto**, dovrebbe essere possibile compilare ed eseguire il progetto come di consueto.

7. Salvare il file.

8. Copiare il file *AssemblyInfo.cs* dalla cartella *Properties* alla cartella *Projects\SimpleProject* .

9. Nella cartella *Projects\SimpleProject* aggiungere un file XML denominato *SimpleProject. PROG*.

   > [!NOTE]
   > L'estensione del nome file per tutti i progetti di questo tipo è *. PROG*. Se si vuole modificarlo, è necessario modificarlo ovunque sia indicato nella procedura dettagliata.

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

12. Nella finestra **Proprietà** impostare l'azione di **compilazione** *AssemblyInfo.cs*, *Program.cs*, *SimpleProject. ico* e *SimpleProject. PROG* sul **contenuto** e impostare le proprietà **Includi in VSIX** su **true**.

    Questo modello di progetto descrive un progetto di base di Visual C# che include una configurazione di debug e una configurazione di rilascio. Il progetto include due file di origine, *AssemblyInfo.cs* e *Program.cs*, e diversi riferimenti ad assembly. Quando viene creato un progetto dal modello, il valore ProjectGuid viene sostituito automaticamente da un nuovo GUID.

    In **Esplora soluzioni** la cartella **modelli** espansa dovrebbe apparire come segue:

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
 È necessario indicare a Visual Studio la posizione della cartella del modello di progetto. A tale scopo, aggiungere un attributo alla classe VSPackage che implementa la factory del progetto in modo che la posizione del modello venga scritta nel registro di sistema durante la compilazione del pacchetto VSPackage. Iniziare creando una factory di progetto di base identificata da un GUID della factory del progetto. Usare l' <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo per connettere la factory del progetto alla `SimpleProjectPackage` classe.

### <a name="to-create-a-basic-project-factory"></a>Per creare una factory di progetto di base

1. Creare GUID per la factory del progetto (dal menu **strumenti** , fare clic su **Crea GUID**) o usare quello nell'esempio seguente. Aggiungere i GUID alla `SimpleProjectPackage` classe accanto alla sezione con l'oggetto già definito `PackageGuidString` . I GUID devono essere in formato GUID e stringa. Il codice risultante dovrebbe essere simile all'esempio seguente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Aggiungere una classe alla cartella Top *SimpleProject* denominata *SimpleProjectFactory.cs*.

3. Aggiungere le seguenti direttive using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Aggiungere un attributo GUID alla `SimpleProjectFactory` classe. Il valore dell'attributo è il nuovo GUID della factory del progetto.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   A questo punto è possibile registrare il modello di progetto.

### <a name="to-register-the-project-template"></a>Per registrare il modello di progetto

1. In *SimpleProjectPackage.cs* aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo alla `SimpleProjectPackage` classe, come indicato di seguito.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Ricompilare la soluzione e verificare che venga compilata senza errori.

    La ricompilazione registra il modello di progetto.

   I parametri `defaultProjectExtension` e `possibleProjectExtensions` sono impostati sull'estensione del nome del file di progetto (*. PROG*). Il `projectTemplatesDirectory` parametro viene impostato sul percorso relativo della cartella *templates* . Durante la compilazione, questo percorso verrà convertito in una compilazione completa e aggiunto al registro di sistema per registrare il sistema del progetto.

## <a name="test-the-template-registration"></a>Testare la registrazione del modello
 La registrazione dei modelli indica a Visual Studio la posizione della cartella del modello di progetto in modo che Visual Studio possa visualizzare il nome e l'icona del modello nella finestra di dialogo **nuovo progetto** .

### <a name="to-test-the-template-registration"></a>Per testare la registrazione del modello

1. Premere **F5** per avviare il debug di un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, creare un nuovo progetto del tipo di progetto appena creato. Nella finestra di dialogo **nuovo progetto** dovrebbe essere visualizzato **SimpleProject** in **modelli installati**.

   A questo punto è disponibile una factory di progetto che è registrata. Tuttavia, non può ancora creare un progetto. Il pacchetto di progetto e la factory del progetto interagiscono per creare e inizializzare un progetto.

## <a name="add-the-managed-package-framework-code"></a>Aggiungere il codice del Framework del pacchetto gestito
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.

- Importare i file del codice sorgente per il Framework di pacchetto gestito.

    1. Scaricare il progetto SimpleProject (in **Esplora soluzioni**, selezionare il nodo del progetto e scegliere **Scarica progetto** dal menu di scelta rapida e aprire il file di progetto nell'editor XML.

    2. Aggiungere i blocchi seguenti al file di progetto (appena sopra i \<Import> blocchi). Impostare sul `ProjectBasePath` percorso del file *ProjectBase. files* nel codice del Framework del pacchetto gestito appena scaricato. Potrebbe essere necessario aggiungere una barra rovesciata al percorso. In caso contrario, il progetto potrebbe non riuscire a trovare il codice sorgente del Framework del pacchetto gestito.

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

1. Nel file *SimpleProjectPackage.cs* aggiungere la `using` direttiva seguente.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivare la `SimpleProjectPackage` classe da `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registrare la factory del progetto. Aggiungere la riga seguente al `SimpleProjectPackage.Initialize` metodo, subito dopo `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementare la proprietà abstract `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. In *SimpleProjectFactory.cs* aggiungere la direttiva seguente `using` dopo le `using` direttive esistenti.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivare la `SimpleProjectFactory` classe da `ProjectFactory` .

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

8. Aggiungere il campo e il costruttore seguenti alla `SimpleProjectFactory` classe. Questo `SimpleProjectPackage` riferimento viene memorizzato nella cache in un campo privato, in modo che possa essere usato nell'impostazione di un sito del provider di servizi.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Ricompilare la soluzione e verificare che venga compilata senza errori.

## <a name="test-the-project-factory-implementation"></a>Testare l'implementazione della factory di progetto
 Verificare se viene chiamato il costruttore per l'implementazione della factory di progetto.

### <a name="to-test-the-project-factory-implementation"></a>Per testare l'implementazione della factory di progetto

1. Nel file *SimpleProjectFactory.cs* , impostare un punto di interruzione nella riga seguente del `SimpleProjectFactory` costruttore.

    ```csharp
    this.package = package;
    ```

2. Premere **F5** per avviare un'istanza sperimentale di Visual Studio.

3. Nell'istanza sperimentale avviare la creazione di un nuovo progetto. Nella finestra di dialogo **nuovo progetto** selezionare il tipo di progetto **SimpleProject** e quindi fare clic su **OK**. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

4. Cancellare il punto di interruzione e arrestare il debug. Poiché non è stato ancora creato un nodo di progetto, il codice di creazione del progetto genera comunque eccezioni.

## <a name="extend-the-projectnode-class"></a>Estendere la classe ProjectNode
 A questo punto è possibile implementare la `SimpleProjectNode` classe, che deriva dalla `ProjectNode` classe. La `ProjectNode` classe base gestisce le attività di creazione del progetto seguenti:

- Copia il file del modello di progetto, *SimpleProject. PROG*, nella nuova cartella del progetto. La copia viene rinominata in base al nome immesso nella finestra di dialogo **nuovo progetto** . Il `ProjectGuid` valore della proprietà viene sostituito da un nuovo GUID.

- Attraversa gli elementi MSBuild del file del modello di progetto, *SimpleProject. PROG*, e Cerca `Compile` gli elementi. Per ogni `Compile` file di destinazione, copia il file nella nuova cartella del progetto.

  La `SimpleProjectNode` classe derivata gestisce queste attività:

- Consente di creare o selezionare Icone per i nodi di progetto e file in **Esplora soluzioni** .

- Consente di specificare altre sostituzioni di parametro del modello di progetto.

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

   Questa `SimpleProjectNode` implementazione della classe presenta questi metodi sottoposti a override:

- `ProjectGuid`, che restituisce il GUID della factory del progetto.

- `ProjectType`, che restituisce il nome localizzato del tipo di progetto.

- `AddFileFromTemplate`, che copia i file selezionati dalla cartella del modello al progetto di destinazione. Questo metodo viene implementato ulteriormente in una sezione successiva.

  Il `SimpleProjectNode` costruttore, ad esempio il `SimpleProjectFactory` costruttore, memorizza nella cache un `SimpleProjectPackage` riferimento in un campo privato per un uso successivo.

  Per connettere la `SimpleProjectFactory` classe alla `SimpleProjectNode` classe, è necessario creare un'istanza di un nuovo oggetto `SimpleProjectNode` nel `SimpleProjectFactory.CreateProject` metodo e memorizzarlo nella cache in un campo privato per un uso successivo.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Per connettere la classe factory del progetto e la classe Node

1. Nel file *SimpleProjectFactory.cs* aggiungere la `using` direttiva seguente:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Sostituire il `SimpleProjectFactory.CreateProject` Metodo usando il codice seguente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Ricompilare la soluzione e verificare che venga compilata senza errori.

## <a name="test-the-projectnode-class"></a>Testare la classe ProjectNode
 Testare la factory del progetto per verificare se viene creata una gerarchia del progetto.

### <a name="to-test-the-projectnode-class"></a>Per eseguire il test della classe ProjectNode

1. Premere **F5** per avviare il debug. Nell'istanza sperimentale creare un nuovo SimpleProject.

2. Per creare un progetto, è necessario che Visual Studio chiami la factory del progetto.

3. Chiudere l'istanza sperimentale di Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Icona Aggiungi nodo progetto personalizzato
 L'icona del nodo del progetto nella sezione precedente è un'icona predefinita. È possibile modificarlo in un'icona personalizzata.

### <a name="to-add-a-custom-project-node-icon"></a>Per aggiungere un'icona del nodo del progetto personalizzato

1. Nella cartella **risorse** aggiungere un file bitmap denominato *SimpleProjectNode.bmp*.

2. Nelle finestre **Proprietà** ridurre la bitmap a 16 per 16 pixel. Rendere la bitmap distinta.

    ![Comando Progetto semplice](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Nella finestra **Proprietà** modificare l'azione di **compilazione** della bitmap in **risorsa incorporata**.

4. In *SimpleProjectNode.cs* aggiungere le `using` direttive seguenti:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Aggiungere il seguente campo statico e il costruttore alla `SimpleProjectNode` classe.

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

   Durante la costruzione statica, `SimpleProjectNode` Recupera la bitmap del nodo del progetto dalle risorse del manifesto dell'assembly e la memorizza nella cache in un campo privato per un uso successivo. Si noti la sintassi del <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> percorso dell'immagine. Per visualizzare i nomi delle risorse del manifesto incorporate in un assembly, usare il <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metodo. Quando questo metodo viene applicato all' `SimpleProject` assembly, i risultati devono essere i seguenti:

- *SimpleProject. resources. resources*

- *VisualStudio. Project. resources*

- *SimpleProject. VSPackage. resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la costruzione dell'istanza, la `ProjectNode` classe base carica *Resources.imagelis.bmp*, in cui le bitmap sono incorporate comunemente utilizzate 16 x 16 bitmap da *Resources\imagelis.bmp*. Questo elenco bitmap viene reso disponibile a `SimpleProjectNode` come `ImageHandler.ImageList` . `SimpleProjectNode` Accoda la bitmap del nodo del progetto all'elenco. L'offset della mappa di bit del nodo di progetto nell'elenco immagini viene memorizzato nella cache per un uso successivo come valore della `ImageIndex` proprietà Public. Visual Studio usa questa proprietà per determinare quale bitmap visualizzare come icona del nodo del progetto.

## <a name="test-the-custom-project-node-icon"></a>Testare l'icona del nodo del progetto personalizzato
 Testare la factory del progetto per verificare se viene creata una gerarchia del progetto con l'icona del nodo del progetto personalizzato.

### <a name="to-test-the-custom-project-node-icon"></a>Per testare l'icona del nodo del progetto personalizzato

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. Nel progetto appena creato si noti che *SimpleProjectNode.bmp* viene usato come icona del nodo del progetto.

     ![Progetto semplice, nuovo nodo di progetto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Aprire *Program.cs* nell'editor di codice. Si noterà che il codice sorgente è simile al codice seguente.

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

     Si noti che i parametri del modello $nameSpace $ e $className $ non hanno nuovi valori. Si apprenderà come implementare la sostituzione dei parametri di modello nella sezione successiva.

## <a name="substitute-template-parameters"></a>Sostituisci parametri modello
 In una sezione precedente è stato registrato il modello di progetto con Visual Studio usando l' `ProvideProjectFactory` attributo. La registrazione del percorso di una cartella modello in questo modo consente di abilitare la sostituzione dei parametri di modello di base eseguendo l'override e l'espansione della `ProjectNode.AddFileFromTemplate` classe. Per altre informazioni, vedere [creazione di un nuovo progetto: dietro le quinte, parte 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 A questo punto aggiungere il codice di sostituzione alla `AddFileFromTemplate` classe.

### <a name="to-substitute-template-parameters"></a>Per sostituire i parametri del modello

1. Nel file *SimpleProjectNode.cs* aggiungere la `using` direttiva seguente.

   ```csharp
   using System.IO;
   ```

2. Sostituire il `AddFileFromTemplate` Metodo usando il codice seguente.

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

3. Impostare un punto di interruzione nel metodo, subito dopo l' `className` istruzione di assegnazione.

   Le istruzioni di assegnazione determinano valori ragionevoli per uno spazio dei nomi e un nuovo nome di classe. Le due `ProjectNode.FileTemplateProcessor.AddReplace` chiamate al metodo sostituiscono i valori del parametro di modello corrispondenti usando questi nuovi valori.

## <a name="test-the-template-parameter-substitution"></a>Testare la sostituzione del parametro di modello
 A questo punto è possibile testare la sostituzione del parametro di modello.

### <a name="to-test-the-template-parameter-substitution"></a>Per testare la sostituzione del parametro di modello

1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.

2. L'esecuzione si interrompe in corrispondenza del punto di interruzione nel `AddFileFromTemplate` metodo.

3. Esaminare i valori per i `nameSpace` `className` parametri e.

   - `nameSpace` viene dato il valore dell' \<RootNamespace> elemento nel file del modello di progetto *\Templates\Projects\SimpleProject\SimpleProject.MyProj* . In questo caso il valore è `MyRootNamespace`.

   - `className` viene dato il valore del nome del file di origine della classe, senza l'estensione del nome file. In questo caso, il primo file da copiare nella cartella di destinazione è *AssemblyInfo.cs*; il valore di nomeclasse è pertanto `AssemblyInfo` .

4. Rimuovere il punto di interruzione e premere **F5** per continuare l'esecuzione.

    Visual Studio deve terminare la creazione di un progetto.

5. Aprire *Program.cs* nell'editor di codice. Si noterà che il codice sorgente è simile al codice seguente.

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

    Si noti che lo spazio dei nomi è ora `MyRootNamespace` e il nome della classe è Now `Program` .

6. Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX!!!" nella finestra della console.

    ![Comando Progetto semplice](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Congratulazioni! È stato implementato un sistema di progetto gestito di base.
