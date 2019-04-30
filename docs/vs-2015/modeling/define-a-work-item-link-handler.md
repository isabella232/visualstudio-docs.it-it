---
title: Definire un gestore di collegamento elemento di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd50f4c80e5e67f6fb7582dc2bc22963151b42fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433123"
---
# <a name="define-a-work-item-link-handler"></a>Definire un gestore dei collegamenti agli elementi di lavoro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare un progetto Visual Studio Integration Extension che risponde quando l'utente crea o elimina un collegamento tra un elemento del modello UML e un elemento di lavoro. Ad esempio, quando l'utente sceglie di collegare un nuovo elemento di lavoro a un elemento del modello, il codice può inizializzare i campi dell'elemento di lavoro dai valori nel modello.  
  
## <a name="set-up-a-uml-extension-solution"></a>Impostare una soluzione di estensione UML  
 L'impostazione consentirà di sviluppare gestori e di distribuirli ad altri utenti. È necessario impostare due progetti di Visual Studio:  
  
- Un progetto di libreria di classi contenente il codice di un gestore di collegamenti.  
  
- Un progetto VSIX, che funge da contenitore per l'installazione del comando. Se si desidera, è possibile includere altri componenti nello stesso progetto VSIX.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Per impostare la soluzione di Visual Studio  
  
1. Creare un progetto di libreria di classi, aggiungendolo a una soluzione VSIX esistente oppure creando una nuova soluzione.  
  
    1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.  
  
    2. Sotto **modelli installati**, espandere **Visual c#** oppure **Visual Basic**, quindi nella colonna centrale fare clic su **libreria di classi**.  
  
    3. Impostare **Soluzione** per indicare se si desidera creare una nuova soluzione o aggiungere un componente a una soluzione VSIX che è già stata aperta.  
  
    4. Specificare il nome e il percorso del progetto e fare clic su OK.  
  
2. Creare un progetto VSIX salvo il caso in cui la soluzione ne contenga già uno.  
  
    1. In **Esplora soluzioni**scegliere **Aggiungi**dal menu di scelta rapida della soluzione e quindi fare clic su **Nuovo progetto**.  
  
    2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**, quindi selezionare **Extensibility**. Nella colonna centrale scegliere **Progetto VSIX**.  
  
3. Impostare il progetto VSIX come progetto di avvio della soluzione.  
  
    - In Esplora soluzioni scegliere **Imposta come progetto di avvio**dal menu di scelta rapida del progetto VSIX.  
  
4. Nelle **vsixmanifest**, in **contenuto**, aggiungere il progetto di libreria di classi come componente MEF.  
  
    1. Nella scheda **Metadati** impostare un nome per il progetto VSIX.  
  
    2. Nella scheda **Destinazioni di installazione** impostare le versioni di Visual Studio come destinazioni.  
  
    3. Nella scheda **Asset** scegliere **Nuovo**e nella finestra di dialogo impostare le opzioni seguenti:  
  
         **Tipo** = **Componente MEF**  
  
         **Origine** = **Progetto nella soluzione corrente**  
  
         **Progetto** = *Progetto di libreria di classi*  
  
## <a name="defining-the-work-item-link-handler"></a>Definizione di un gestore dei collegamenti agli elementi di lavoro  
 Eseguire tutte le attività seguenti nel progetto di libreria di classi.  
  
### <a name="project-references"></a>Riferimenti al progetto  
 Aggiungere gli [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] assembly seguenti ai riferimento di progetto:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -usato dal codice di esempio  
  
 Se non è possibile trovare uno di questi riferimenti nella **.Net** scheda della finestra di **Aggiungi riferimento** finestra di dialogo utilizzare la scheda Sfoglia per trovarlo in \Programmi\Microsoft Visual Studio [versione] \Common7\IDE\ PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>Importare lo spazio dei nomi dell'elemento di lavoro  
 Nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project **riferimenti**, aggiungere i riferimenti agli assembly seguenti:  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  Nel codice del programma, importare gli spazi dei nomi seguenti:  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Definire il gestore eventi degli elementi di lavoro collegati  
 Aggiungere un file di classe al progetto di libreria di classi e impostarne il contenuto come segue. Modificare i nomi dello spazio dei nomi e della classe secondo le proprie preferenze.  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>Test del gestore di collegamenti  
 Per scopi di test, eseguire il gestore di collegamenti in modalità di debug.  
  
> [!WARNING]
> Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
#### <a name="to-test-the-link-handler"></a>Per testare il gestore di collegamenti  
  
1. Premere **F5**o scegliere **Avvia debug** dal menu **Debug**.  
  
     Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     **Risoluzione dei problemi**: Se un nuovo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non viene avviato, verificare che il progetto VSIX sia impostato come progetto di avvio della soluzione.  
  
2. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]aprire o creare un progetto di modellazione e aprire o creare un diagramma di modellazione.  
  
3. Creare un elemento del modello, ad esempio la classe UML, e impostarne il nome.  
  
4. Fare doppio clic dell'elemento e quindi fare clic su **Crea elemento di lavoro**.  
  
    - Se viene visualizzato il sottomenu **Apri connessione a Team Foundation Server**, sarà necessario chiudere il progetto, connettersi all'istanza appropriata di TFS e riavviare questa procedura.  
  
    - Se il sottomenu visualizza un elenco di tipi di elemento di lavoro, fare clic su uno di essi.  
  
         Viene visualizzato un nuovo modulo degli elementi di lavoro.  
  
5. Verificare che il titolo dell'elemento di lavoro sia lo stesso elemento del modello se è stato usato il codice di esempio nella sezione precedente. Ciò dimostra che `OnWorkItemCreated()` ha funzionato.  
  
6. Completare il modulo, salvare e chiudere l'elemento di lavoro.  
  
7. Verificare che l'elemento di lavoro sia ora visualizzato in rosso. Ciò dimostra `OnWorkItemLinked()` nel codice di esempio.  
  
     **Risoluzione dei problemi**: Se i metodi del gestore non è sono eseguito, verificare che:  
  
    - Progetto libreria di classi è elencato come componente MEF nel **contenuti** nell'elenco **manifest** nel progetto VSIX.  
  
    - L' attributo `Export` corretto sia collegato alla classe del gestore e la classe implementi `ILinkedWorkItemExtension`.  
  
    - I parametri di tutti gli attributi `Import` e `Export` attributi siano validi.  
  
## <a name="about-the-work-item-handler-code"></a>Informazioni sul codice del gestore degli elementi di lavoro  
  
### <a name="listening-for-new-work-items"></a>Attesa di nuovi elementi di lavoro  
 `OnWorkItemCreated` viene chiamato quando l'utente sceglie di creare un nuovo elemento di lavoro da collegare agli elementi del modello. Il codice può inizializzare i campi elemento di lavoro. L'elemento di lavoro viene quindi presentato all'utente, che può aggiornare i campi e salvare l'elemento di lavoro. Il collegamento a un elemento del modello non viene creato fino a quando l'elemento di lavoro non è stato salvato.  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>Attesa della creazione di collegamenti  
 `OnWorkItemLinked` viene chiamato subito dopo la creazione di un collegamento, sia nel caso di collegamento a un nuovo elemento di lavoro che a un elemento esistente. Viene chiamato una volta per ogni elemento di lavoro.  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
> Per far funzionare questo esempio, è necessario aggiungere un riferimento di progetto a `System.Drawing.dll` e importare lo spazio dei nomi `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Tuttavia, queste aggiunte non sono necessarie per altre implementazioni di `OnWorkItemLinked`.  
  
### <a name="listening-for-link-removal"></a>Attesa della rimozione di collegamenti  
 `OnWorkItemRemoved` viene chiamato una volta prima dell'eliminazione di ogni collegamento di elemento di lavoro. Se viene eliminato un elemento del modello, verranno rimossi tutti i relativi collegamenti.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Aggiornamento di un elemento di lavoro  
 Usando gli spazi dei nomi di Team Foundation, è possibile modificare un elemento di lavoro.  
  
 Per usare l'esempio seguente, aggiungere questi assembly .NET ai riferimenti del progetto:  
  
- Microsoft.TeamFoundation.Client.dll  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>Accesso ai collegamenti di riferimento degli elementi di lavoro  
 È possibile accedere ai collegamenti nel modo seguente:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Il formato di `linkString` è il seguente:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 dove:  
  
- L'URI per il server sarà:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   L'alternanza maiuscolo minuscolo è importante in `projectCollection`.  
  
- `RepositoryGuid` può essere ottenuto dalla connessione TFS:  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Per altre informazioni sui riferimenti, vedere [stringhe di riferimento Attach UML di elementi del modello](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md)   
 [Allegare stringhe di riferimento agli elementi del modello UML](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
