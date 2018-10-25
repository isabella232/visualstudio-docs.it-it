---
title: Eseguire unit test su estensioni UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1e3a8cdd6d8551a4ea399a2ef387d383acca136c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873669"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Eseguire unit test su estensioni UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per mantenere la stabilità del codice in caso di modifiche successive, è consigliabile scrivere unit test ed eseguirli come parte di un normale processo di compilazione. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md). Per configurare i test per le estensioni di modellazione di Visual Studio sono necessarie alcune informazioni. Riepilogo:  
  
- [Impostazione di uno Unit Test per le estensioni VSIX](#Host)  
  
   Eseguire test con l'adattatore host dell'IDE di VS. Aggiungere `[HostType("VS IDE")]`come prefisso a ogni metodo di test. L'adattatore host avvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durante l'esecuzione dei test.  
  
- [L'accesso a DTE e ModelStore](#DTE)  
  
   Sarà in genere necessario aprire un modello e i relativi diagrammi e infine accedere a `IModelStore` durante l'inizializzazione del test.  
  
- [Apertura di un diagramma del modello](#Opening)  
  
   È possibile eseguire il casting di `EnvDTE.ProjectItem` in e da `IDiagramContext`.  
  
- [Esecuzione di modifiche nel Thread dell'interfaccia utente](#UiThread)  
  
   I test che modificano l'archivio modelli devono essere eseguiti nel thread dell'interfaccia utente. A tale scopo, è possibile usare `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` .  
  
- [Testing di comandi, movimenti e altri componenti MEF](#MEF)  
  
   Per testare i componenti MEF, è necessario connettere in modo esplicito le relative proprietà importate a valori.  
  
  Questi concetti sono approfonditi nelle sezioni seguenti.  
  
  Per un esempio di estensione UML sottoposta a unit test, vedere la raccolta di esempi di codice disponibile nella pagina [Immissione rapida in UML tramite testo](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).  
  
## <a name="requirements"></a>Requisiti  
 Vedere [Requisiti](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="Host"></a> Impostazione di uno Unit Test per le estensioni VSIX  
 I metodi disponibili nelle estensioni di modellazione possono essere in genere usati con un diagramma già aperto. I metodi usano importazioni MEF, quali **IDiagramContext** e **ILinkedUndoContext**. L'ambiente di testing deve configurare questo contesto prima dell'esecuzione dei test.  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Per configurare un unit test da eseguire in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1.  Creare il progetto di estensione UML e il progetto di unit test.  
  
    1.  **Un progetto di estensione UML.** Per creare il progetto si usano in genere i comandi, i movimenti o i modelli di progetto di convalida. Ad esempio, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
    2.  **Un progetto di unit test.** Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).  
  
2.  Creare una soluzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che include un progetto di modellazione UML. Questa soluzione sarà usata come stato iniziale dei test. Dovrebbe essere separata dalla soluzione in cui si scrivono l'estensione UML e i relativi unit test. Per altre informazioni, vedere [diagrammi e progetti di modellazione UML creare](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
3.  **Nel progetto di estensione UML**modificare il file con estensione csproj come testo e assicurarsi che le righe seguenti mostrino `true`:  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     Per modificare il file con estensione csproj come testo, scegliere **Scarica progetto** dal menu di scelta rapida del progetto in Esplora soluzioni. Scegliere quindi **Modifica… csproj**. Dopo la modifica del testo, scegliere **Ricarica progetto**.  
  
4.  Nel progetto di estensione UML aggiungere la riga seguente a **Properties\AssemblyInfo.cs**. Ciò permette agli unit test di accedere ai metodi da testare:  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5.  **Nel progetto di unit test**aggiungere i riferimenti ad assembly seguenti:  
  
    -   *Il progetto di estensione UML*  
  
    -   **EnvDTE. dll**  
  
    -   **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    -   **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    -   **UnitTestFramework**  
  
    -   **VisualStudio**  
  
    -   **Microsoft.VSSDK.TestHostFramework.dll**  
  
6.  Aggiungere l'attributo `[HostType("VS IDE")]` come prefisso a ogni metodo di test, inclusi i metodi di inizializzazione.  
  
     Ciò consente di assicurare che il test sarà eseguito in un'istanza sperimentale di Visual Studio.  
  
##  <a name="DTE"></a> L'accesso a DTE e ModelStore  
 Scrivere un metodo per aprire un progetto di modellazione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È in genere consigliabile aprire una soluzione solo una volta in ogni esecuzione di test. Per eseguire il metodo solo una volta, aggiungere l'attributo `[AssemblyInitialize]` come prefisso per il metodo. È anche necessario specificare l'attributo [HostType("VS IDE")] in ogni metodo di test.  Ad esempio:  
  
```csharp  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
  
namespace UnitTests  
{  
  [TestClass]  
  public static class TestSetup  
  {  
  
    // Location of a VS Solution that defines an initial state for your tests:  
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";  
    // Name of a modeling project within the test solution:  
    private const string testModelingProjectName = "MyTestModel";  
  
    // Make Solution and IModelStore available to test methods:  
    public static Solution ModelSolution = null;  
    public static IModelingProject ModelingProject = null;  
    public static IModelStore ModelStore = null;  
  
    // This method will be performed once to initialize tests for this assembly:  
    [AssemblyInitialize]   
    [HostType("VS IDE")]  
    public static void OpenTestModelingProject(TestContext testContext)  
    {  
      // To make sure that we always start the tests in the same state,  
      // copy the test solution from a read-only directory:  
      // TODO: copy test solution folder.  
  
      // Open a solution that is the initial state for your tests:  
      ModelSolution = VsIdeTestHostContext.Dte.Solution;  
      ModelSolution.Open(testSolutionFilePath);  
  
      // Find the ModelingProject and IModelStore:  
      foreach (Project project in ModelSolution.Projects)  
      {  
        // http://msdn.microsoft.com/library/ee791691.aspx  
        ModelingProject = project as IModelingProject;  
        if (ModelingProject != null)  
        {  
          // This is a modeling project.  
          ModelStore = ModelingProject.Store;  
          break;  
        }  
        // else this is another kind of project.  
      }  
  
      Assert.IsNotNull(ModelSolution, "VS solution not found");  
      Assert.IsNotNull(ModelStore, "Modeling store not found");  
    }  
    [AssemblyCleanup]  
    public static void RemoveTestSolution ()  
    {  
      // TODO: Remove copied test solution directory.  
    }  
  }  
}  
  
```  
  
 Se un'istanza di <xref:EnvDTE.Project?displayProperty=fullName> rappresenta un progetto di modellazione, sarà possibile eseguirne il casting in e da <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>.  
  
##  <a name="Opening"></a> Apertura di un diagramma del modello  
 Per ogni test o classe di test è in genere consigliabile usare un diagramma aperto. L'esempio seguente usa l'attributo `[ClassInitialize]` , che esegue questo metodo prima degli altri metodi nella classe di test. Anche in questo caso è necessario specificare l'attributo [HostType("VS IDE")] in ogni metodo di test:  
  
```csharp  
//   
private IDiagram diagram;  
// This class contains unit tests:  
[TestClass]  
public class MyTestClass  
{  
  // Map filenames to open diagram files:  
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();  
  
  // This method will be called once for this test class:  
  [ClassInitialize]  
  [HostType("VS IDE")]  
  public static void TestClassInitialize(TestContext testContext)  
  {  
    // Open all the diagrams in the model:  
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)  
    {  
      // Get the filename of the principal file (not the .layout subsidiary):  
      string fileName = item.FileNames[0];  
      // If this is a model diagram file, it can be cast to IDiagramContext:  
      IDiagramContext modelingItem = item as IDiagramContext;  
      if (modelingItem != null)  
      {  
        IDiagram diagram = modelingItem.CurrentDiagram;  
        if (diagram == null)  
        {  
          // Diagram is closed. Open it:  
          item.Open().Activate();  
          diagram = modelingItem.CurrentDiagram;  
        }  
        diagrams[fileName] = diagram;  
      }  
      // else item is not a model diagram.  
    }  
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");  
  }  
// Insert test methods here ...  
}  
  
```  
  
##  <a name="UiThread"></a> Eseguire le modifiche al modello nel Thread dell'interfaccia utente  
 Se i test o i metodi sottoposti a test apportano modifiche all'archivio modelli, sarà necessario eseguirli nel thread dell'interfaccia utente. In caso contrario, è possibile che sia visualizzata una `AccessViolationException`. Racchiudere il codice del metodo di test in una chiamata a Invoke:  
  
```  
using System.Windows.Forms;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
 ...  
    [TestMethod]  
    [HostType("VS IDE")]  
    public void MyTest1()  
    {  
      // Store operations must run in the UI thread:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        SetupTestState(TestSetup.ModelStore, diagram);  
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);  
      });  
    }  
```  
  
##  <a name="MEF"></a> Testing di comandi, movimenti e altri componenti MEF  
 I componenti MEF usano dichiarazioni di proprietà che includono l'attributo `[Import]` e i cui valori sono configurati dai rispettivi host. In genere queste proprietà includono IDiagramContext, SVsServiceProvider e ILinkedUndoContext. Quando si testa un metodo che usa una di queste proprietà, occorre configurarne i valori prima di eseguire il metodo sottoposto a test. Ad esempio, se è stata scritta un'estensione di comando analoga al codice seguente:  
  
```  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class MyCommand : ICommandExtension  
  {  
    [Import] IDiagramContext context { get; set; }  
    [Import]   
Microsoft.VisualStudio.Shell.SVsServiceProvider  
serviceProvider {get;set;}  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      DoCommand();  
    }  
    private void DoCommand()  
    {  
      IDiagram diagram = context.CurrentDiagram;  
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))  
      { ... }}}  
  
```  
  
 Sarà possibile impostare le proprietà importate come indicato di seguito:  
  
```  
  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ComponentModelHost;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
...  
    [TestMethod]   
    [HostType("VS IDE")]  
    public void Test1()  
    {  
      // Create an instance of the class under test:  
      MyCommand myCommand = new MyCommand();  
      // Get the components service:  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
        .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Set the imported properties of the instance under test:  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);  
      // Call method(s) under test:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        myCommand.DoCommand();  
      });  
...}  
```  
  
 Per testare un metodo che accetta una proprietà importata come parametro, sarà quindi possibile importare la proprietà nella classe di test e applicare `SatisfyImportsOnce` all'istanza di test. Ad esempio:  
  
```  
  
using System.ComponentModel.Composition;  
...  
  [TestClass]  
  public class MyTestClass  
  {  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called before each test method:  
    [TestInitialize, HostType("VS IDE")]   
    public void TestInitializer()  
    {  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
            .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(this);  
    }  
    [TestMethod, HostType("VS IDE")]  
    public void Test2()  
    {   
     UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
      // Pass context items to class under test:  
      Class1 item1 = new Class1(this.linkedUndoContext);  
      item1.Method1(); // Can use linkedUndoContext  
     });  
   }  
}  
  
```  
  
 In questo esempio i due attributi di ogni metodo di test sono combinati in una riga per semplificare.  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>Accesso dai test a variabili e metodi privati  
 A volte si vuole testare un metodo privato o verificare lo stato di un campo privato, prima e dopo l'esecuzione di un metodo sottoposto a test. Questa operazione presenta difficoltà, poiché i test si trovano in un assembly diverso rispetto alle classi sottoposte a test. È possibile prendere in considerazione diverse strategie, inclusa la seguente:  
  
 Eseguire test usando solo elementi pubblici e interni  
 Scrivere test in modo che usino solo classi e membri pubblici o interni. Questo è l'approccio migliore. I test continueranno a funzionare anche se si effettua il refactoring dell'implementazione interna dell'assembly sottoposto a test. L'applicazione degli stessi test prima e dopo le modifiche consente di assicurarsi che le modifiche non abbiano alterato il comportamento dell'assembly.  
  
 Per ottenere questo risultato, potrebbe essere necessario ristrutturare il codice. Potrebbe essere ad esempio necessario separare alcuni metodi in un'altra classe.  
  
 Valutando con attenzione questo approccio, si potrà spesso notare che consente di ottenere codice più semplice da leggere e modificare e meno soggetto a errori in caso di modifiche necessarie.  
  
 Sarà possibile permettere all'assembly di test di accedere a elementi interni tramite l'aggiunta di un attributo in **Properties\AssemblyInfo.cs** nel progetto da testare:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Definire un'interfaccia di test  
 Definire un'interfaccia che include i membri pubblici di una classe da testare e le proprietà e i metodi aggiuntivi per i membri privati che i test devono essere in grado di usare. Aggiungere questa interfaccia al progetto da testare. Ad esempio:  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 Aggiungere metodi alla classe da testare, per implementare in modo esplicito i metodi della funzione di accesso. Mantenere questi metodi separati dalla classe principale, scrivendoli in una definizione di classe parziale in un file distinto. Ad esempio:  
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 Permettere all'assembly di test di usare le interfacce di test tramite l'aggiunta di questo attributo all'assembly sottoposto a test:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Nei metodi di unit test, usare l'interfaccia di test. Ad esempio:  
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 Definire le funzioni di accesso tramite la reflection  
 Questo è l'approccio meno consigliabile. Nelle versioni precedenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è disponibile un'utilità che consente di creare automaticamente un metodo di funzione di accesso per ogni metodo privato. Anche se apparentemente efficace, questo approccio tende ad avere come risultato unit test ad accoppiamento avanzato alla struttura interna dell'applicazione sottoposta a test. Questo comporta lavoro aggiuntivo in caso di modifiche ai requisiti o all'architettura, poiché occorre modificare i test insieme all'implementazione. Eventuali supposizioni errate presenti nella progettazione dell'implementazione saranno inoltre incluse nei test, che quindi non rileveranno errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Composizione di uno unit test](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Immissione rapida con testo in UML](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)



