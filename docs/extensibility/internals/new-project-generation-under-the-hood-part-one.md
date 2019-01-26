---
title: 'Nuova generazione del progetto: Dietro le quinte, parte 1 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd41bb8fd0e35ee13815b11941950d9031f824a0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041789"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nuova generazione del progetto: Dietro le quinte, parte 1
Mai pensato di come creare un proprio tipo di progetto? Chiedersi cosa succede effettivamente quando si crea un nuovo progetto? Verrà esaminato un peek dietro le quinte e vedere cosa sta effettivamente succedendo.  
  
 Sono disponibili diverse attività che coordina la Visual Studio per l'utente:  
  
-   Visualizza un albero di tutti i tipi di progetto disponibili.  
  
-   Visualizza un elenco di modelli di applicazione per ogni tipo di progetto e consente di selezionare uno.  
  
-   Raccoglie le informazioni sul progetto per l'applicazione, ad esempio nome del progetto e il percorso.  
  
-   Queste informazioni passa la factory del progetto.  
  
-   Genera gli elementi del progetto e le cartelle nella soluzione corrente.  
  
## <a name="the-new-project-dialog-box"></a>La finestra di dialogo Nuovo progetto  
 Tutto ha inizio quando si seleziona un tipo di progetto per un nuovo progetto. Iniziamo facendo **nuovo progetto** nel **File** menu. Il **nuovo progetto** viene visualizzata la finestra di dialogo, dall'aspetto professionale simile al seguente:  
  
 ![Finestra di dialogo Nuovo progetto](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Diamo uno sguardo. Il **tipi di progetto** albero sono elencati i vari tipi di progetto è possibile creare. Quando si seleziona un tipo di progetto, ad esempio **Visual C# Windows**, verrà visualizzato un elenco dei modelli di applicazione per iniziare a usare. **Modelli Visual Studio installati** vengono installati da Visual Studio e sono disponibili a tutti gli utenti del computer in uso. Nuovi modelli di creazione o la raccolta possono essere aggiunto a **modelli personali** e sono accessibili solo all'utente.  
  
 Quando si seleziona un modello simile **dell'applicazione Windows**, nella finestra di dialogo, in questo caso, viene visualizzata una descrizione del tipo di applicazione **un progetto per la creazione di un'applicazione con un'interfaccia utente di Windows**.  
  
 In fondo il **nuovo progetto** finestra di dialogo, si noterà diversi controlli che consentono di raccogliere ulteriori informazioni. I controlli visualizzati variano a seconda del tipo di progetto, ma generalmente includono un progetto **Name** casella di testo, un **posizione** casella di testo ed elementi correlati **Sfoglia** pulsante e una **Nome della soluzione** casella di testo ed elementi correlati **Crea directory per soluzione** casella di controllo.  
  
## <a name="populating-the-new-project-dialog-box"></a>Popolare la finestra di dialogo Nuovo progetto  
 In cui viene il **nuovo progetto** ottenere le relative informazioni dalla finestra di dialogo? Esistono due meccanismi a lavoro in questo caso, uno di essi è deprecato. Il **nuovo progetto** nella finestra di dialogo combina e visualizza le informazioni ottenute da entrambi i meccanismi.  
  
 Il metodo meno recente (obsoleto) usa le voci del Registro di sistema e file VSDIR. Questo meccanismo viene eseguito all'apertura di Visual Studio. Il metodo più recente utilizza i file con estensione vstemplate. Questo meccanismo viene eseguito quando viene inizializzato Visual Studio, ad esempio, tramite l'esecuzione  
  
```  
devenv /setup  
```  
  
 oppure  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Tipi di progetto  
 La posizione e i nomi del **tipi di progetto** radice, ad esempio, i nodi **Visual c#** e **altri linguaggi**, viene determinato dalle voci di registro di sistema. L'organizzazione dei nodi figlio, ad esempio **Database** e **Smart Device**, rispecchia la gerarchia delle cartelle che contengono i file con estensione vstemplate corrispondenti. Esaminiamo i nodi radice prima di tutto.  
  
#### <a name="project-type-root-nodes"></a>Nodi radice di tipo di progetto  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato, attraversa le sottochiavi della chiave del Registro di sistema del sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs per creare e denominare i nodi radice del **tipidiprogetto** struttura ad albero. Queste informazioni sono memorizzato nella cache per un uso successivo. Esaminare il TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC il} \\ /1 chiave. Ogni voce è un GUID di VSPackage. Il nome della sottochiave (/ 1) viene ignorato, ma la sua presenza indica che si tratta di un **tipi di progetto** nodo radice. Un nodo radice potrebbe essere a sua volta sottochiavi diverse che consentono di controllare l'aspetto nella **tipi di progetto** struttura ad albero. Esaminiamo alcune di esse.  
  
##### <a name="default"></a>(Predefinito)  
 Questo è l'ID risorsa della stringa localizzata che corrisponde al nome del nodo radice. La risorsa di stringa si trova nella DLL selezionato dal GUID VSPackage satellite.  
  
 Nell'esempio, il GUID di VSPackage è  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 e l'ID di risorsa (valore predefinito) del nodo radice (/ 1) è 2345 #  
  
 Se si esamina la sottochiave SatelliteDll cercare il GUID della chiave di pacchetti nelle vicinanze, è possibile trovare il percorso dell'assembly che contiene la risorsa di stringa:  
  
 \<Percorso di installazione di Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Per verificarlo, aprire Esplora File e trascinare csprojui.dll nella directory di Visual Studio... Tabella di stringhe viene illustrato che risorse 2345 # contiene la didascalia **Visual c#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Questa impostazione determina la posizione del nodo radice nel **tipi di progetto** struttura ad albero.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Più basso il numero di priorità, maggiore sarà la posizione nell'albero.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Se questa sottochiave è presente, la posizione del nodo radice è controllata dalla finestra di dialogo Impostazioni modalità sviluppatore. Ad esempio,  
  
 REG_SZ DeveloperActivity VC #  
  
 indica che Visual c# è un nodo radice se Visual Studio è impostato per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] lo sviluppo. In caso contrario, sarà un nodo figlio del **altri linguaggi**.  
  
##### <a name="folder"></a>Cartella  
 Se questa sottochiave è presente, il nodo radice diventa quindi un nodo figlio della cartella specificata. Viene visualizzato un elenco di possibili cartelle sotto la chiave  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Ad esempio, la voce di progetti di Database ha una chiave di cartella che corrisponde alla voce di altri tipi di progetto nel PseudoFolders. In questo caso, nella **tipi di progetto** albero **progetti di Database** sarà un nodo figlio del **altri tipi di progetto**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>I nodi figlio di tipo di progetto e i file. vstdir  
 La posizione dei nodi figlio di **tipi di progetto** albero segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per i modelli di computer (**Modelli Visual Studio installati**), il percorso tipico è \Programmi\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ e per i modelli utente (**modelli personali**), il percorso tipico è Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Le gerarchie di cartelle da questi due percorsi vengono unite per creare il **tipi di progetto** struttura ad albero.  
  
 Per Visual Studio con c# impostazioni modalità sviluppatore, il **tipi di progetto** albero simile al seguente:  
  
 ![Tipi di progetto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Nella cartella ProjectTemplates corrispondente è simile alla seguente:  
  
 ![Modelli di progetto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Quando la **nuovo progetto** verrà visualizzata la finestra di dialogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attraversa la cartella ProjectTemplates e ricrea la struttura di **tipi di progetto** albero con alcune modifiche:  
  
-   Il nodo radice nella **tipi di progetto** albero è determinata dal modello di applicazione.  
  
-   Il nome del nodo può essere localizzato e può contenere caratteri speciali.  
  
-   L'ordinamento può essere modificato.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Ricerca del nodo radice per un tipo di progetto  
 Quando Visual Studio attraversa le cartelle ProjectTemplates, apre tutti i file con estensione zip ed estrae i file con estensione vstemplate. Un file con estensione vstemplate Usa XML per descrivere un modello di applicazione. Per altre informazioni, vedere [nuova generazione progetto: Dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Il \<ProjectType > tag determina il tipo di progetto per l'applicazione. Ad esempio, il file \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un file EmptyProject.vstemplate con questo tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Il \<ProjectType > tag e non la sottocartella nella cartella ProjectTemplates, determina il nodo radice di un'applicazione nel **tipi di progetto** struttura ad albero. Nell'esempio, le applicazioni di Windows CE queste appariranno sotto la **Visual c#** nodo radice, e anche se si intende spostare la cartella WindowsCE nella cartella VisualBasic, le applicazioni di Windows CE comunque queste appariranno sotto la  **Visual c#** nodo radice.  
  
##### <a name="localizing-the-node-name"></a>Localizzare il nome del nodo  
 Quando Visual Studio attraversa le cartelle ProjectTemplates, esamina tutti i file. vstdir rilevati. Un file. vstdir è un file XML che controlla l'aspetto del tipo di progetto nel **nuovo progetto** nella finestra di dialogo. Nel file. vstdir, usare il \<LocalizedName > tag al nome il **tipi di progetto** nodo.  
  
 Ad esempio, il file \CSharp\Database\TemplateIndex.vstdir contiene questo tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 L'ID di risorsa e DLL satellite della stringa localizzata che corrisponde al nome del nodo radice, in questo caso, determinando **Database**. Il nome localizzato può contenere caratteri speciali che non sono disponibili per i nomi delle cartelle, ad esempio **.NET**.  
  
 Se nessun \<LocalizedName > tag è presente, il tipo di progetto viene denominato dalla cartella stessa, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Ricerca l'ordinamento per un tipo di progetto  
 Per determinare l'ordinamento del tipo di progetto, usano i file. vstdir il \<SortOrder > tag.  
  
 Ad esempio, il file \CSharp\Windows\Windows.vstdir contiene questo tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Il file \CSharp\Database\TemplateIndex.vstdir ha un tag con un valore maggiore:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Più basso il numero nel \<SortOrder > tag, maggiore sarà la posizione nell'albero in modo che il **Windows** nodo viene visualizzato supera il **Database** nodo il **tipi di progetto**  struttura ad albero.  
  
 Se nessun \<SortOrder > tag viene specificato per un tipo di progetto, viene visualizzato in ordine alfabetico seguenti eventuali tipi di progetto contenenti \<SortOrder > specifiche.  
  
 Si noti che non sono presenti file. vstdir nella cartella documenti (**modelli personali**) le cartelle. Nomi di tipi di progetto dell'applicazione utente non sono localizzati e vengono visualizzati in ordine alfabetico.  
  
#### <a name="a-quick-review"></a>Una rapida panoramica  
 È possibile modificare il **nuovo progetto** dialogo casella e creare un nuovo modello di progetto utente.  
  
1. Aggiungere una sottocartella del nodo progetto personalizzato nella cartella 14.0\Common7\IDE\ProjectTemplates\CSharp \Programmi\Microsoft Visual Studio.  
  
2. Creare un file MyProject.vstdir nella cartella nodo progetto personalizzato usando qualsiasi editor di testo.  
  
3. Aggiungere le righe seguenti al file. vstdir:  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Salvare e chiudere il file. vstdir.  
  
5. Creare un file MyProject.vstemplate nella cartella nodo progetto personalizzato usando qualsiasi editor di testo.  
  
6. Nel file con estensione vstemplate, aggiungere le righe seguenti:  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. Salvare file the.vstemplate e chiudere l'editor.  
  
8. Inviare il file con estensione vstemplate in una nuova cartella MyProjectNode\MyProject.zip compressa.  
  
9. Nella finestra di comando di Visual Studio, digitare:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Aprire Visual Studio.  
  
10. Aprire il **nuovo progetto** finestra di dialogo casella ed espandere le **Visual c#** nodo del progetto.  
  
    ![Nodo progetto personalizzato](../../extensibility/internals/media/myprojectnode.png "nodo progetto personalizzato")  
  
    **Nodo progetto personalizzato** visualizzato come nodo figlio di Visual c# appena sotto il nodo di Windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Nuova generazione del progetto: Dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)