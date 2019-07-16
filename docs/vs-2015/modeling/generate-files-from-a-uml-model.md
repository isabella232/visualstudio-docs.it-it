---
title: Generare file da un modello UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d58a8b98cb27527f3d4c464119fb5543f88e8ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182831"
---
# <a name="generate-files-from-a-uml-model"></a>Generare file da un modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Da un modello UML, è possibile generare codice programma, schemi, documenti, risorse e altri tipi di elementi. Un metodo pratico per la generazione di file di testo da un modello UML consiste nell'utilizzare [modelli di testo](../modeling/code-generation-and-t4-text-templates.md). Questi consentono di incorporare il codice programma nel testo da generare.  
  
 Esistono tre scenari principali:  
  
- [Generazione di file da un comando di menu](#Command) o movimenti. L'utente definisce un comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] disponibile nei modelli UML.  
  
- [Generazione di file da un'applicazione](#Application). L'utente scrive un'applicazione in grado di leggere i modelli UML e di generare i file.  
  
- [Generazione in fase di progettazione](#Design). L'utente usa un modello per definire alcune delle funzionalità dell'applicazione e per generare codice, risorse e altro all'interno della soluzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  In questo argomento termina con una discussione sulle [come usare la generazione di testo](#What). Per altre informazioni, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="Command"></a> Generazione di file da un comando di menu  
 È possibile usare i modelli di testo pre-elaborati in un comando di menu UML. Nel codice del modello di testo o in una classe parziale separata, è possibile leggere il modello visualizzato dal diagramma.  
  
 Per altre informazioni su queste funzionalità, leggere gli argomenti seguenti:  
  
- [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [Esplorare il modello UML](../modeling/navigate-the-uml-model.md)  
  
  L'approccio mostrato nell'esempio seguente è adatto per la generazione di testo da un singolo modello, quando si avvia l'operazione da uno dei diagrammi del modello. Per elaborare un modello in un contesto separato, è consigliabile usare [Modelbus di Visual Studio](../modeling/integrate-uml-models-with-other-models-and-tools.md) per accedere al modello e i relativi elementi.  
  
### <a name="example"></a>Esempio  
 Per eseguire questo esempio, creare un progetto con estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Il nome del progetto che viene usato in questo esempio è `VdmGenerator`. Nel **vsixmanifest** del file, fare clic su **Aggiungi contenuto** e impostare il campo di tipo **componente MEF** e il percorso di origine che fa riferimento il progetto corrente. Per altre informazioni su come configurare questo tipo di progetto, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Aggiungere al progetto un file C# contenente il codice seguente. Questa classe definisce un comando di menu che verrà visualizzato in un diagramma classi UML.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 Il file seguente è il modello di testo. Genera una riga di testo per ogni classe UML nel modello e una riga per ogni attributo in ciascuna classe. Il codice per la lettura del modello è incorporato nel testo, delimitato da `<# ... #>`.  
  
 Per creare questo file, fare clic sul progetto in Esplora soluzioni, scegliere **Add**, quindi fare clic su **nuovo elemento**. Selezionare **modello di testo pre-elaborato**. Il nome di file per questo esempio deve essere **VdmGen.tt**. Il **Custom Tool** proprietà del file deve essere **TextTemplatingFilePreprocessor**. Per altre informazioni sui modelli di testo pre-elaborato, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 Il modello di testo genera una classe parziale C# che diventa parte del progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In un file separato, aggiungere un'altra dichiarazione parziale della stessa classe. Questo codice fornisce il modello con accesso all'archivio modelli UML:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 Per testare il progetto, premere **F5**. Viene avviata una nuova istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In questa istanza, aprire o creare un modello UML contenente un diagramma classi. Aggiungere alcune classi al diagramma e alcuni attributi a ogni classe. Pulsante destro del mouse nel diagramma e quindi scegliere il comando di esempio `Generate VDM`. Il comando crea il file `C:\Generated.txt`. Esaminare il file. I contenuti dovrebbero somigliare al testo seguente, ma con le proprie classi e attributi:  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
## <a name="Application"></a> Generazione di file da un'applicazione  
 È possibile generare file da un'applicazione che legge un modello UML. A tale scopo, è metodo più flessibile e affidabile di accedere al modello e i relativi elementi [Modelbus di Visual Studio](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 È anche possibile usare l'API di base per caricare il modello e passarlo ai modelli di testo usando le stesse tecniche della sezione precedente. Per altre informazioni sul caricamento di un modello, vedere [leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="Design"></a> Generazione di file in fase di progettazione  
 Se il progetto ha un metodo standard di interpretazione di UML come codice, è possibile creare modelli di testo che consentono di generare il codice all'interno del progetto da un modello UML. In genere si ha una soluzione che contiene il progetto del modello UML e uno o più progetti per il codice dell'applicazione. Ogni progetto di codice può contenere diversi modelli che generano il codice del programma, le risorse e i file di configurazione in base al contenuto del modello. Lo sviluppatore può eseguire tutti i modelli facendo il **Trasforma tutti i modelli** sulla barra degli strumenti Esplora soluzioni. Il codice del programma viene generato in genere sotto forma di classi parziali per semplificare l'integrazione manuale delle parti scritte.  
  
 Un progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] di questo tipo può essere distribuito sotto forma di modello, in modo che ogni membro di un team possa creare allo stesso modo progetti che generano codice da un modello. In genere, il modello fa parte di un pacchetto di estensioni che include vincoli di convalida relativi al modello per garantire che le precondizioni per il codice di generazione vengano soddisfatte.  
  
### <a name="outline-procedure-for-generating-files"></a>Procedura relativa alla struttura per la generazione di file  
  
- Per aggiungere un modello a un progetto, selezionare **modello di testo** nella finestra di dialogo Aggiungi nuovo File. È possibile aggiungere un modello alla maggior parte dei tipi di progetto, ma non ai progetti di modellazione.  
  
- La proprietà Custom Tools del file modello deve essere **TextTemplatingFileGenerator**, e l'estensione del nome file deve essere. tt.  
  
- Il modello deve avere almeno una direttiva di output:  
  
     `<#@ output extension=".cs" #>`  
  
     Impostare il campo delle estensioni in base al linguaggio del progetto.  
  
- Per consentire al codice di generazione nel modello di accedere al modello, scrivere le direttive `<#@ assembly #>` per gli assembly necessari per leggere un modello UML. Usare `ModelingProject.LoadReadOnly()` per aprire il modello. Per altre informazioni, vedere [leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md).  
  
- Il modello viene eseguito quando viene salvato e quando fa clic su **Trasforma tutti i modelli** sulla barra degli strumenti Esplora soluzioni.  
  
- Per altre informazioni su questo tipo di modello, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
- In un progetto standard sono presenti più modelli che generano file diversi dallo stesso modello. La prima parte di tutti i modelli sarà uguale. Per ridurre questa duplicazione, spostare le parti comuni in un file di testo separato, quindi richiamarle usando la direttiva `<#@include file="common.txt"#>` in ogni modello.  
  
- È anche possibile definire un processore di direttive specializzato che consente di fornire i parametri al processo di generazione del testo. Per altre informazioni, vedere [personalizzazione di trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Esempio  
 Questo esempio genera una classe C# per ogni classe UML nel modello di origine.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Per configurare una soluzione di Visual Studio per questo esempio  
  
1. Creare un diagramma classi UML in un progetto di modellazione in una nuova soluzione.  
  
   1. Nel **Architecture** menu, fare clic su **nuovo diagramma**.  
  
   2. Selezionare **diagramma classi UML**.  
  
   3. Seguire le istruzioni per creare una nuova soluzione e un progetto di modellazione.  
  
   4. Aggiungere alcune classi al diagramma trascinando lo strumento Classe UML dalla casella degli strumenti.  
  
   5. Salvare il file.  
  
2. Creare un progetto C# o Visual Basic nella stessa soluzione.  
  
   - In Esplora soluzioni fare doppio clic la soluzione, scegliere **Add**, quindi fare clic su **nuovo progetto**. Sotto **modelli installati**, fare clic su **Visual Basic** oppure **Visual c#** e quindi selezionare un tipo di progetto, ad esempio **applicazione Console**.  
  
3. Aggiungere un file di testo normale al progetto C# o Visual Basic. Il file conterrà codice condiviso se si vogliono scrivere più modelli di testo.  
  
   - In Esplora soluzioni fare clic sul progetto, scegliere **Add**, quindi fare clic su **nuovo elemento**. Selezionare **File di testo**.  
  
     Inserire il testo visualizzato nella sezione seguente.  
  
4. Aggiungere un file del modello di testo al progetto C# o Visual Basic.  
  
   - In Esplora soluzioni fare clic sul progetto, scegliere **Add**, quindi fare clic su **nuovo elemento**. Selezionare **modello di testo**.  
  
     Inserire il codice seguente nel file del modello di testo.  
  
5. Salvare il file del modello di testo.  
  
6. Esaminare il codice nel file secondario. Deve contenere una classe per ogni classe UML nel modello.  
  
   1. In un progetto di Visual Basic, fare clic su **Mostra tutti i file** sulla barra degli strumenti Esplora soluzioni.  
  
   2. Espandere il nodo del file del modello in Esplora soluzioni.  
  
#### <a name="content-of-the-shared-text-file"></a>Contenuto del file di testo condiviso  
 In questo esempio il file è denominato SharedTemplateCode.txt e si trova nella stessa cartella dei modelli di testo.  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>Contenuto del file del modello di testo  
 Il testo seguente viene inserito nel **tt** file. Questo esempio genera classi in un file C# dalle classi UML nel modello. Tuttavia, è possibile generare file di qualsiasi tipo. Il linguaggio del file generato non è correlato a quello con cui viene scritto il codice del modello di testo.  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
## <a name="What"></a> Come usare la generazione di testo  
 La reale potenza della modellazione viene raggiunta quando si usano i modelli per la progettazione a livello di requisiti o di architettura. È possibile usare i modelli di testo per eseguire alcune attività di trasformazione di concetti di alto livello in codice. In molti casi non si ottiene una corrispondenza univoca tra gli elementi nei modelli UML e nelle classi o in altre parti del codice del programma.  
  
 Inoltre, la trasformazione dipende dal dominio del problema specifico. Non esiste un mapping universale tra modelli e codice.  
  
 Ecco alcuni esempi di generazione del codice dai modelli:  
  
- **Linee di prodotti**. Fabrikam, Inc. crea e installa sistemi di gestione dei bagagli negli aeroporti. La maggior parte del software delle varie installazioni è simile, mentre la configurazione del software dipende dal macchinario di gestione dei bagagli installato e dalla modalità di interconnessione dei componenti mediante i nastri trasportatori. All'inizio di un contratto, gli analisti di Fabrikam discutono dei requisiti con il management dell'aeroporto e acquisiscono il piano dell'hardware usando un diagramma di attività UML. Da questo modello il team di sviluppo genera i file di configurazione, il codice del programma, i piani e i documenti dell'utente. Il lavoro viene completato con aggiunte e modifiche manuali al codice. Con l'aumentare dell'esperienza, il team è in grado di estendere l'ambito del materiale generato.  
  
- **I modelli**. Gli sviluppatori in Contoso, Ltd costruiscono spesso siti Web e progettano lo schema di navigazione usando i diagrammi classi UML. Ogni pagina Web viene rappresentata da una classe e le associazioni rappresentano i collegamenti di navigazione. Gli sviluppatori generano gran parte del codice di un sito Web dal modello. Ogni pagina Web corrisponde a diverse classi e voci del file di risorse.  Questo metodo offre il vantaggio di poter costruire ogni pagina in modo conforme a un unico motivo, rendendolo quindi più affidabile e flessibile rispetto al codice scritto a mano. Il motivo si trova nei modelli di generazione, mentre il modello viene usato per acquisire gli aspetti variabili.  
  
- **Gli schemi**. Humongous Insurance ha migliaia di sistemi in tutto il mondo. Questi sistemi usano database, linguaggi e interfacce diversi. Il team di architettura centrale pubblica internamente modelli per i concetti e i processi aziendali. Da questi modelli i team locali generano parte dei propri schemi di database e di scambio, le dichiarazioni nel codice del programma e così via. La presentazione grafica dei modelli consente ai team di discutere le proposte. I team creano più diagrammi che mostrano i subset del modello che si applicano a diverse aree aziendali. Usano anche i colori per evidenziare le aree soggette a modifiche.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Tecniche importanti per la generazione di elementi  
 Negli esempi precedenti i modelli sono stati usati per diversi scopi aziendali e l'interpretazione degli elementi di modellazione, come le classi e le attività, varia da un'applicazione all'altra. Le tecniche seguenti sono utili quando si generano gli elementi dai modelli.  
  
- **I profili**. Anche in un'unica area aziendale, l'interpretazione di un tipo di elemento può variare. Ad esempio, in un diagramma sito Web alcune classi possono rappresentare le pagine Web, mentre altre i blocchi di contenuto. Per semplificare la registrazione di queste differenze per gli utenti, definire gli stereotipi. Gli stereotipi consentono anche di collegare altre proprietà da applicare agli elementi dello stesso tipo. Gli stereotipi vengono forniti all'interno dei profili. Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     Nel codice del modello è facile accedere agli stereotipi definiti in un oggetto. Ad esempio:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
- **Modelli vincolati**. Non tutti i modelli che è possibile creare sono validi per qualsiasi scopo. Ad esempio, nei modelli per la gestione dei bagagli negli aeroporti di Fabrikam non sarebbe appropriato avere un banco dell'accettazione senza un nastro trasportatore in uscita. È possibile definire le funzioni di convalida che consentono agli utenti di rispettare questi vincoli. Per altre informazioni, vedere [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
- **Mantenere le modifiche manuali**. Solo alcuni file della soluzione possono essere generati da un modello. Nella maggior parte dei casi è necessario aggiungere o modificare il contenuto generato manualmente. Tuttavia, è importante che queste modifiche manuali vengano mantenute quando la trasformazione del modello viene eseguita di nuovo.  
  
     Se i modelli generano codice [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] linguaggi, in modo che gli sviluppatori possono aggiungere i metodi e codice devono generare le classi parziali. Inoltre, è utile generare ogni classe sotto forma di coppia: una classe di base astratta che contiene i metodi e una classe a eredità che contiene solo il costruttore. In questo modo, gli sviluppatori possono eseguire l'override dei metodi. Per l'override dell'inizializzazione è necessario usare un metodo separato invece dei costruttori.  
  
     Se un modello genera XML e altri tipi di output, può risultare più difficile mantenere separato il contenuto manuale da quello generato. Un metodo consiste nel creare un'attività nel processo di compilazione che combini i due file. Un altro metodo è pensato per gli sviluppatori e consente di modificare una copia locale del modello di generazione.  
  
- **Spostare il codice in un assembly separato**. Non si consiglia di scrivere grandi quantità di codice nei modelli. È preferibile mantenere il contenuto generato separato dal calcolo. I modelli di testo non sono supportati correttamente per la modifica del codice.  
  
     Al contrario, se è necessario eseguire calcoli sostanziali per generare il testo, compilare queste funzioni in un assembly separato e chiamarne i metodi dal modello.
