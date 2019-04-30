---
title: Creazione di un sistema di progetto di base, parte 1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8304719a4b15b5f23957c99244796999d7b3f55c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439391"
---
# <a name="creating-a-basic-project-system-part-1"></a>Creazione di un sistema di progetto di base, parte 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare file di codice sorgente e altre risorse. I progetti vengono visualizzati come figli di soluzioni nel **Esplora soluzioni**. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente e creare riferimenti a servizi Web, database e altre risorse.  
  
 I progetti sono definiti nel file di progetto, ad esempio un file con estensione csproj per un progetto Visual c#. È possibile creare un proprio tipo di progetto che ha il proprio estensione nome file di progetto. Per altre informazioni sui tipi di progetto, vedere [tipi di progetto](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Se è necessario estendere Visual Studio con un tipo di progetto personalizzati, è consigliabile sfruttare il [sistema di progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem) che offre numerosi vantaggi rispetto alla creazione di un sistema di progetto da zero:  
> 
> - Processo di onboarding più semplice.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  Sfruttando CPS riduce i costi di onboarding a pochi clic prima che si è pronti per personalizzarlo in base alle esigenze.  
>   - Maggiore facilità di manutenzione.  Sfruttando CPS, è sufficiente mantenere i propri scenari.  Noi la gestione di manutenzione di tutta l'infrastruttura di sistema di progetto.  
> 
>   Se è necessario destinate alle versioni di Visual Studio precedenti a Visual Studio 2013, non sarà in grado di sfruttare CPS in un'estensione di Visual Studio.  Se è questo il caso, questa procedura dettagliata è ideale per iniziare.  
  
 Questa procedura dettagliata illustra come creare un tipo di progetto che ha il .myproj di estensione nome file progetto. Questa procedura dettagliata Usa il sistema di progetto Visual c# esistente.  
  
> [!NOTE]
> Per un esempio end-to-end di un sistema di progetto linguaggio completo, vedere Approfondimenti esempio IronPython nel [esempi di VSSDK](../misc/vssdk-samples.md).  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
- Creare un tipo di progetto di base.  
  
- Creare un modello di progetto di base.  
  
- Registrare il modello di progetto con Visual Studio.  
  
- Creare un'istanza del progetto, aprire il **nuovo progetto** nella finestra di dialogo e quindi usando il modello.  
  
- Creare una factory di progetto per il sistema di progetto.  
  
- Creare un nodo del progetto per il sistema di progetto.  
  
- Aggiungere icone personalizzate per il sistema di progetto.  
  
- Implementare la sostituzione dei parametri di modello di base.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 È inoltre necessario scaricare il codice sorgente per il [Framework di pacchetto gestito per progetti](http://mpfproj12.codeplex.com/). Estrarre il file in una posizione accessibile per la soluzione che si intende creare.  
  
## <a name="creating-a-basic-project-type"></a>Creazione di un tipo di progetto di base  
 Creare un progetto VSIX c# denominato **SimpleProject**. (**File, nuovo, progetto** e quindi **il pacchetto di Visual Studio c#, estendibilità,**). Aggiungere un modello di elemento di progetto di pacchetto di Visual Studio (in Esplora soluzioni fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**, quindi passare alla **estendibilità / pacchetto di Visual Studio**). Denominare il file **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Creazione di un modello di progetto di base  
 A questo punto, è possibile modificare questo VSPackage di base per implementare il nuovo tipo di progetto .myproj. Per creare un progetto che si basa sul tipo di progetto .myproj, deve conoscere quali file, risorse e riferimenti da aggiungere al nuovo progetto di Visual Studio. Per fornire questa informazione, inserire i file di progetto in una cartella di modello di progetto. Quando un utente usa il progetto .myproj per creare un progetto, i file vengono copiati nel nuovo progetto.  
  
#### <a name="to-create-a-basic-project-template"></a>Per creare un modello di progetto di base  
  
1. Aggiungere al progetto, uno dopo le altre tre cartelle: **Templates\Projects\SimpleProject**. (In **Esplora soluzioni**, fare doppio clic sul **SimpleProject** nodo del progetto, scegliere **Add**, quindi fare clic su **nuova cartella**. Denominare la cartella `Templates`. Nel **modelli** cartella, aggiungere una cartella denominata `Projects`. Nel **progetti** cartella, aggiungere una cartella denominata `SimpleProject`.)  
  
2. Nel **Projects\SimpleProject** cartella aggiungere un file di icona denominato `SimpleProject.ico`. Quando fa clic su **Add**, viene aperto l'editor di icona.  
  
3. Verificare l'icona distintivo. Questa icona verrà visualizzata nel **nuovo progetto** finestra di dialogo in un secondo momento nella procedura dettagliata.  
  
    ![Simple Project Icon](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. L'icona di salvare e chiudere l'editor di icona.  
  
5. Nel **Projects\SimpleProject** cartella, aggiungere un **classe** elemento denominato `Program.cs`.  
  
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
   > Non è il formato finale del codice di Program.cs; verranno gestiti con i parametri di sostituzione in un passaggio successivo. È possibile visualizzare errori di compilazione, ma fino a quando il file **BuildAction** viene **contenuto**, dovrebbe essere possibile compilare ed eseguire il progetto come di consueto.  
  
7. Salvare il file.  
  
8. Copiare il file AssemblyInfo.cs dal **delle proprietà** cartella per il **Projects\SimpleProject** cartella.  
  
9. Nel **Projects\SimpleProject** cartella aggiungere un file XML denominato `SimpleProject.myproj`.  
  
   > [!NOTE]
   > L'estensione per tutti i progetti di questo tipo è .myproj. Se si desidera modificarlo, è necessario modificarlo ovunque che viene citata nella procedura dettagliata.  
  
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
  
12. Nel **proprietà** impostare nella finestra di **azione di compilazione** AssemblyInfo.cs, Program.cs, SimpleProject.ico e SimpleProject.myproj a **contenuto**e impostare i  **Includi in VSIX** delle proprietà per **True**.  
  
    Questo modello descrive un progetto Visual c# base con una configurazione di Debug e una configurazione di rilascio. Il progetto include due file di origine, AssemblyInfo.cs e Program.cs e numerosi assembly che i riferimenti. Quando viene creato un progetto dal modello, il valore ProjectGuid verrà automaticamente sostituito da un nuovo GUID.  
  
    Nelle **Esplora soluzioni**, espanso **modelli** cartella apparirà come segue:  
  
    Modelli  
  
    Progetti  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Creazione di una Factory di progetto di base  
 È necessario indicare a Visual Studio il percorso della cartella dei modelli di progetto. A tale scopo, aggiungere un attributo alla classe VSPackage che implementa la factory del progetto in modo che il percorso del modello viene scritto nel Registro di sistema quando viene compilato il pacchetto VSPackage. Iniziare creando una factory di progetto di base che è identificata da un GUID della factory progetto. Usare il <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo a cui connettersi la classe SimpleProjectPackage la factory del progetto.  
  
#### <a name="to-create-a-basic-project-factory"></a>Per creare una factory di progetto di base  
  
1. Aprire SimpleProjectPackageGuids.cs nell'editor del codice.  
  
2. Crea GUID della factory di progetto (nelle **strumenti** menu, fare clic su **Crea GUID**), o usare quello nell'esempio seguente. Aggiungere i GUID per la classe SimpleProjectPackageGuids. Il GUID deve essere in formato GUID sia sotto forma di stringa. Il codice risultante dovrebbe essere simile al seguente.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Aggiungere una classe nella parte superiore **SimpleProject** cartella denominata `SimpleProjectFactory.cs`.  
  
4. Aggiungere quanto segue usando istruzioni:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Aggiungere un attributo Guid alla classe SimpleProjectFactory. Il valore dell'attributo è il nuovo GUID della factory progetto.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   A questo punto è possibile registrare il modello di progetto.  
  
#### <a name="to-register-the-project-template"></a>Per registrare il modello di progetto  
  
1. In SimpleProjectPackage.cs, aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo alla classe SimpleProjectPackage, come indicato di seguito.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Ricompilare la soluzione e verificare che la compilazione senza errori.  
  
    La ricompilazione registra il modello di progetto.  
  
   I parametri `defaultProjectExtension` e `possibleProjectExtensions` configurati per l'estensione del file di progetto (.myproj). Il `projectTemplatesDirectory` parametro è impostato per il percorso relativo della cartella modelli. Durante la compilazione, questo percorso verrà convertito in una build completa e aggiunto al Registro di sistema per registrare il sistema del progetto.  
  
## <a name="testing-the-template-registration"></a>La registrazione di un modello di test  
 Registrazione di un modello indica a Visual Studio il percorso della cartella dei modelli di progetto in modo che Visual Studio può visualizzare il nome del modello e l'icona nel **nuovo progetto** nella finestra di dialogo.  
  
#### <a name="to-test-the-template-registration"></a>Per testare la registrazione di un modello  
  
1. Premere F5 per avviare il debug di un'istanza sperimentale di Visual Studio.  
  
2. Nell'istanza sperimentale, creare un nuovo progetto del tipo di progetto appena creato. Nel **nuovo progetto** della finestra di dialogo dovrebbe **SimpleProject** sotto **modelli installati**.  
  
   Ora si dispone di una factory di progetto che è registrata. Tuttavia, ancora non è possibile creare un progetto. Il pacchetto del progetto e la factory di progetto interagiscono per creare e inizializzare un progetto.  
  
## <a name="add-the-managed-package-framework-code"></a>Aggiungere il codice del Framework di pacchetto gestito  
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.  
  
- Importare i file di codice sorgente per il Framework di pacchetto gestito.  
  
    1. Scaricare il progetto SimpleProject (in **Esplora soluzioni**, selezionare il nodo del progetto e scegliere il menu di scelta rapida **Scarica progetto**.) e aprire il file di progetto nell'editor XML.  
  
    2. Aggiungere i seguenti blocchi del file di progetto (di sopra di \<Import > blocchi). Impostare ProjectBasePath nel percorso del file ProjectBase.files nel codice gestito Framework di pacchetto che appena scaricato. Potrebbe essere necessario aggiungere una barra rovesciata per il nome del percorso. In caso contrario, il progetto potrebbe non riuscire a trovare il codice del Framework di pacchetto gestito.  
  
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
  
        - Microsoft.VisualStudio.Designer.Interfaces (in \<install VSSDK > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Per inizializzare la factory del progetto  
  
1. Aggiungere il codice seguente nel file SimpleProjectPackage.cs `using` istruzione.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Derivare la `SimpleProjectPackage` classe `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Registrare la factory del progetto. Aggiungere la riga seguente per il `SimpleProjectPackage.Initialize` metodo, subito dopo `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Implementa la proprietà astratta `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. In SimpleProjectFactory.cs, aggiungere quanto segue `using` istruzione dopo esistente `using` istruzioni.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Derivare la `SimpleProjectFactory` classe `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Aggiungere il seguente metodo fittizio per il `SimpleProjectFactory` classe. Questo metodo è implementato in una sezione successiva.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Aggiungere il seguente campo e al costruttore il `SimpleProjectFactory` classe. Ciò `SimpleProjectPackage` riferimento viene memorizzato nella cache in un campo privato, in modo che può essere utilizzato nell'impostazione di un sito del provider di servizio.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Ricompilare la soluzione e verificare che la compilazione senza errori.  
  
## <a name="testing-the-project-factory-implementation"></a>L'implementazione di Factory di progetto di test  
 Verificare se viene chiamato il costruttore per l'implementazione di factory di progetto.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Per testare l'implementazione di factory di progetto  
  
1. Nel file SimpleProjectFactory.cs, impostare un punto di interruzione nella riga seguente all'interno di `SimpleProjectFactory` costruttore.  
  
    ```  
    this.package = package;  
    ```  
  
2. Premere F5 per avviare un'istanza sperimentale di Visual Studio.  
  
3. Nell'istanza sperimentale, iniziare a creare un nuovo progetto. Nel **nuovo progetto** finestra di dialogo SimpleProject il tipo di progetto e quindi fare clic su **OK**. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.  
  
4. Rimuovere il punto di interruzione e arrestare il debug. Poiché non è stata creata ancora un nodo del progetto, il codice di creazione del progetto continua a generare eccezioni.  
  
## <a name="extending-the-project-node-class"></a>Estensione della classe di nodo di progetto  
 A questo punto è possibile implementare il `SimpleProjectNode` classe che deriva dal `ProjectNode` classe. Il `ProjectNode` classe di base gestisce le attività seguenti della creazione del progetto:  
  
- Copia il file di modello di progetto, SimpleProject.myproj, nella nuova cartella di progetto. La copia è stata rinominata in base al nome immesso nella **nuovo progetto** nella finestra di dialogo. Il `ProjectGuid` proprietà valore viene sostituito con un nuovo GUID.  
  
- Consente di scorrere gli elementi di MSBuild del file di modello di progetto, SimpleProject.myproj ed esegue una ricerca `Compile` elementi. Per ogni `Compile` file di destinazione, viene copiato nella nuova cartella di progetto.  
  
  Derivata `SimpleProjectNode` classe gestisce queste attività:  
  
- Abilita le icone per i nodi di progetto e file in **Esplora soluzioni** può essere creato o selezionato.  
  
- Abilita sostituzioni di parametro di modello di progetto aggiuntivi specificare.  
  
#### <a name="to-extend-the-project-node-class"></a>Per estendere la classe di nodo di progetto  
  
1. 
  
2. Aggiungere una classe denominata `SimpleProjectNode.cs`.  
  
3. Sostituire il codice esistente con quello seguente.  
  
   ```  
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
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
   Ciò `SimpleProjectNode` implementazione della classe dispone di questi metodi sottoposti a override:  
  
- `ProjectGuid`, che restituisce il GUID della factory progetto.  
  
- `ProjectType`, che restituisce il nome localizzato del tipo di progetto.  
  
- `AddFileFromTemplate`, che copia i file selezionati dalla cartella di modello per il progetto di destinazione. Inoltre, questo metodo viene implementato in una sezione successiva.  
  
  Il `SimpleProjectNode` costruttore, ad esempio il `SimpleProjectFactory` memorizza nella cache di costruttore, un `SimpleProjectPackage` riferimento in un campo privato per un uso successivo.  
  
  Per connettersi il `SimpleProjectFactory` classe per il `SimpleProjectNode` (classe), è necessario creare un'istanza di un nuovo `SimpleProjectNode` nel `SimpleProjectFactory.CreateProject` (metodo) e lo memorizza nella cache in un campo privato per un uso successivo.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Per connettere la classe factory di progetto e la classe del nodo  
  
1. Aggiungere il codice seguente nel file SimpleProjectFactory.cs `using` istruzione:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Sostituire il `SimpleProjectFactory.CreateProject` metodo usando il codice seguente.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Ricompilare la soluzione e verificare che la compilazione senza errori.  
  
## <a name="testing-the-project-node-class"></a>La classe di nodo di progetto di test  
 La factory di progetto per verificare se crea una gerarchia del progetto di test.  
  
#### <a name="to-test-the-project-node-class"></a>Per testare la classe di nodo di progetto  
  
1. Premere F5 per avviare il debug. Nell'istanza sperimentale, creare un nuovo SimpleProject.  
  
2. Visual Studio deve chiamare la factory di progetto per creare un progetto.  
  
3. Chiudere l'istanza sperimentale di Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Aggiunta di un'icona di nodo di progetto personalizzati  
 L'icona del nodo di progetto nella sezione precedente è un'icona predefinita. È possibile modificarlo per un'icona personalizzata.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Per aggiungere un'icona di nodo di progetto personalizzati  
  
1. Nel **risorse** cartella, aggiungere un file di mappa di bit denominato SimpleProjectNode.bmp.  
  
2. Nel **proprietà** windows, ridurre la bitmap da 16x16 pixel. Rendere la bitmap distintivo.  
  
    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. Nel **delle proprietà** finestra Modifica il **azione di compilazione** della bitmap da **risorsa incorporata**.  
  
4. In SimpleProjectNode.cs, aggiungere il codice seguente `using` istruzioni:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Aggiungere il seguente campo statico e un costruttore di `SimpleProjectNode` classe.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Aggiungere la proprietà seguente all'inizio del `SimpleProjectNode` classe.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Sostituire il costruttore di istanza con il codice seguente.  
  
   ```  
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
  
   Durante la costruzione statica, `SimpleProjectNode` recupera la bitmap di nodo di progetto dalle risorse del manifesto dell'assembly e li inserisce in un campo privato per un uso successivo. Si noti che la sintassi del <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> percorso dell'immagine. Per visualizzare i nomi delle risorse di manifesto incorporate in un assembly, usare il <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> (metodo). Quando questo metodo viene applicato a di `SimpleProject` assembly, i risultati dovrebbero essere come segue:  
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources.imagelis.bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Durante la costruzione dell'istanza, il `ProjectNode` classe di base carica Resources.imagelis.bmp, in cui sono incorporate bitmap di 16x16 comunemente utilizzate da Resources\imagelis.bmp. Questo elenco bitmap viene resa disponibile per `SimpleProjectNode` come ImageHandler.ImageList. `SimpleProjectNode` Accoda la bitmap di nodo di progetto all'elenco. L'offset della bitmap di nodo di progetto nell'elenco delle immagini viene memorizzato nella cache per usarlo come valore della popolazione `ImageIndex` proprietà. Visual Studio Usa questa proprietà per determinare quali bitmap da visualizzare come icona di nodo del progetto.  
  
## <a name="testing-the-custom-project-node-icon"></a>L'icona di nodo di progetto personalizzati di test  
 Testare la factory di progetto per verificare se crea una gerarchia del progetto con l'icona di nodo di progetto personalizzato.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Per testare l'icona di nodo di progetto personalizzati  
  
1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.  
  
2. Nel progetto appena creato, si noti che SimpleProjectNode.bmp viene utilizzata come icona di nodo del progetto.  
  
     ![Progetto semplice nuovo progetto di nodo](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Aprire Program.cs nell'editor del codice. Dovrebbe essere il codice sorgente che è simile al codice seguente.  
  
    ```  
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
  
     Si noti che i parametri del modello $nameSpace$ e $ $className$ non è nuovi valori. Si apprenderà come implementare la sostituzione dei parametri di modello nella sezione successiva.  
  
## <a name="substituting-template-parameters"></a>Sostituzione di parametri di modello  
 In una sezione precedente, è registrato il modello di progetto in Visual Studio usando il `ProvideProjectFactory` attributo. Registrare il percorso di una cartella di modello in questo modo consente di abilitare la sostituzione dei parametri di modello di base viene sottoposto a override ed espandendo il `ProjectNode.AddFileFromTemplate` classe. Per altre informazioni, vedere [nuova generazione progetto: Dietro le quinte, parte 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 A questo punto aggiungere il codice di sostituzione per il `AddFileFromTemplate` classe.  
  
#### <a name="to-substitute-template-parameters"></a>Sostituire i parametri di modello  
  
1. Aggiungere il codice seguente nel file SimpleProjectNode.cs `using` istruzione.  
  
   ```  
   using System.IO;  
   ```  
  
2. Sostituire il `AddFileFromTemplate` metodo usando il codice seguente.  
  
   ```  
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
  
3. Impostare un punto di interruzione nel metodo, subito dopo il `className` istruzione di assegnazione.  
  
   Le istruzioni di assegnazione determinano i valori ragionevoli per uno spazio dei nomi e un nuovo nome di classe. I due `ProjectNode.FileTemplateProcessor.AddReplace` chiamate al metodo sostituire i valori di parametro di modello corrispondenti con questi nuovi valori.  
  
## <a name="testing-the-template-parameter-substitution"></a>La sostituzione dei parametri di modello di test  
 È ora possibile testare la sostituzione dei parametri di modello.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Per testare la sostituzione dei parametri di modello  
  
1. Avviare il debug e nell'istanza sperimentale creare un nuovo SimpleProject.  
  
2. Esecuzione si arresta nel punto di interruzione il `AddFileFromTemplate` (metodo).  
  
3. Esaminare i valori per il `nameSpace` e `className` parametri.  
  
   - `nameSpace` viene assegnato il valore di \<RootNamespace > elemento nel file del modello di progetto \Templates\Projects\SimpleProject\SimpleProject.myproj. In questo caso, il valore è "MyRootNamespace".  
  
   - `className` viene assegnato il valore del nome della classe source file, senza l'estensione del nome file. In questo caso, il primo file da copiare nella cartella di destinazione è AssemblyInfo.cs; Pertanto, il valore di className è "AssemblyInfo".  
  
4. Rimuovere il punto di interruzione e premere F5 per continuare l'esecuzione.  
  
    Visual Studio deve completare la creazione di un progetto.  
  
5. Aprire Program.cs nell'editor del codice. Dovrebbe essere il codice sorgente che è simile al codice seguente.  
  
   ```  
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
  
    Si noti che lo spazio dei nomi è ora "MyRootNamespace" e il nome della classe è ora "Program".  
  
6. Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX!!!" nella finestra della console.  
  
    ![Comando progetto semplice](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   La procedura è stata completata. È stato implementato un sistema di progetto gestito.
