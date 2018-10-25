---
title: Soluzione (. File sln) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f01657d1053f2172f421bf6e265aa836f930c438
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864933"
---
# <a name="solution-sln-file"></a>File della soluzione (con estensione sln)
Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione gestisce le informazioni sullo stato per i progetti in file con estensione sln (basata su testo, condiviso) e i file con estensione suo (opzioni soluzione binari specifici dell'utente). Per altre informazioni sui file con estensione suo, vedere [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se il pacchetto VSPackage viene caricato in seguito a cui viene fatto riferimento nel file con estensione sln, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> per leggere il file con estensione sln.  
  
 Il file con estensione sln contiene informazioni basate su testo che nell'ambiente viene usato per individuare e caricare i parametri nome / valore per i dati persistenti e il progetto fa riferimento a pacchetti VSPackage. Quando un utente apre una soluzione, l'ambiente consente di scorrere le `preSolution`, `Project`, e `postSolution` informazioni nel file con estensione sln per caricare la soluzione, progetti all'interno della soluzione e qualsiasi informazione persistente collegata alla soluzione.  
  
 File di ogni progetto contiene informazioni aggiuntive di lettura da parte dell'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati di gerarchia è controllata dal progetto. i dati non è in genere archiviati nel file con estensione sln, sebbene sia possibile scrivere le informazioni sul progetto nel file con estensione sln intenzionalmente se si sceglie di eseguire questa operazione. Per altre informazioni relative alla persistenza, vedere [progetto persistenza](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Contenuto del File di soluzione  
 Il file con estensione sln è costituito da diverse sezioni come illustrato nel codice seguente.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Per caricare una soluzione, l'ambiente esegue la sequenza di attività seguente.  
  
1. L'ambiente legge la sezione globale del file con estensione sln ed elabora tutte le sezioni contrassegnate `preSolution`. In questo caso, è presente un'istruzione di questo tipo:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Quando legge l'ambiente di `GlobalSection('name')` tag, esegue il mapping il nome a un pacchetto VSPackage usando il Registro di sistema. Il nome della chiave deve esistere nel Registro di sistema [HKLM\\< directory radice del Registro di ID applicazione\>\SolutionPersistence\AggregateGUIDs]. Valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del pacchetto VSPackage che ha scritto le voci.  
  
2. L'ambiente viene caricato il pacchetto VSPackage, le chiamate `QueryInterface` nel pacchetto VSPackage per la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia e le chiamate di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metodo con i dati nella sezione in modo che il pacchetto VSPackage può archiviare i dati. L'ambiente di questo processo viene ripetuto per ogni `preSolution` sezione.  
  
3. L'ambiente esegue l'iterazione attraverso i blocchi di persistenza del progetto. In questo caso, è presente un unico progetto.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Questa informativa contiene il GUID univoco del progetto e il GUID del tipo di progetto. Queste informazioni vengono utilizzate dall'ambiente per trovare i file di progetto che appartengono alla soluzione e il pacchetto VSPackage necessarie per ogni progetto. Il progetto GUID viene passato a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> per caricare il pacchetto VSPackage specifico correlato al progetto, quindi il progetto viene caricato dal pacchetto VSPackage. In questo caso, il pacchetto VSPackage che viene caricato per questo progetto è Visual Basic.  
  
    Ogni progetto può rendere persistente un ID istanza univoco del progetto in modo che sia accessibile in base alle esigenze da altri progetti nella soluzione. In teoria, se la soluzione e i progetti sono al controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso per la soluzione. Quando il caricamento della soluzione prima di tutto, i file di progetto non possono essere sul computer dell'utente. Facendo in modo che il file di progetto archiviato nel server rispetto al file della soluzione, è relativamente semplice per il file di progetto per trovare e copiare al computer dell'utente. Viene quindi copiata e carica il resto dei file necessari per il progetto.  
  
4. Basato sulle informazioni contenute nella sezione del file con estensione sln di progetto, l'ambiente viene caricato ogni file di progetto. Il progetto stesso è quindi responsabile per la compilazione della gerarchia del progetto e il caricamento di tutti i progetti annidati.  
  
5. Dopo che vengono elaborate tutte le sezioni del file con estensione sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica dall'utente.  
  
   Se non viene caricato, qualsiasi pacchetto VSPackage che implementa un progetto nella soluzione il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> viene chiamato il metodo e ogni altro progetto nella soluzione viene data la possibilità di ignorare le modifiche eventualmente apportate durante il caricamento. Se si verificano errori di analisi, viene mantenute quante più informazioni possibili con i file della soluzione e l'ambiente Visualizza una finestra di dialogo che avvisa l'utente che la soluzione sia danneggiata.  
  
   Quando la soluzione viene salvata o chiuso, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> metodo viene chiamato e passato alla gerarchia per vedere se sono state apportate modifiche alla soluzione che devono essere immesse nel file con estensione sln. Un valore null, passato alla `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica che sono permanente informazioni per la soluzione. Se il valore non null, le informazioni persistenti sono per un progetto specifico, determinato dal puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.  
  
   Se sono presenti informazioni da salvare, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia viene chiamata con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> (metodo). Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> viene quindi chiamato dall'ambiente per recuperare le coppie nome / valore da `IPropertyBag` interfaccia e scrivere le informazioni nel file con estensione sln.  
  
   `SaveSolutionProps` e `WriteSolutionProps` gli oggetti vengono denominati in modo ricorsivo da parte dell'ambiente per recuperare informazioni da salvare dal `IPropertyBag` interfaccia fino a quando tutte le modifiche sono stati immessi nel file con estensione sln. In questo modo, è possibile garantire che le informazioni vengono rese persistenti con la soluzione e il tempo disponibile successivo che la soluzione è aperta.  
  
   Ogni VSPackage caricato viene enumerata per verificare se dispone di alcuna azione per salvare file con estensione sln. È solo in fase di caricamento che vengono eseguite query sulle chiavi del Registro di sistema. L'ambiente conosce tutti i pacchetti caricati in quanto sono in memoria al momento che la soluzione viene salvata.  
  
   Solo i file con estensione sln contiene voci le `preSolution` e `postSolution` sezioni. Sono presenti sezioni simile nel file con estensione suo poiché la soluzione necessita di queste informazioni per caricare correttamente. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio note private, che non devono essere condivisi o inserito nel controllo del codice sorgente.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluzioni](../../extensibility/internals/solutions.md)