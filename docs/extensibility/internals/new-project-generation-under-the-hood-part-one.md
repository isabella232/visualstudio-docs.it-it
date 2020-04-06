---
title: 'Nuova generazione di progetti: sotto il cofano, prima parte Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707059"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generazione di un nuovo progetto: dietro le quinte, parte 1
Hai mai pensato a come creare il tuo tipo di progetto? Chissà cosa succede realmente quando crei un nuovo progetto? Diamo una sbirciatina sotto il cofano e vediamo cosa sta realmente succedendo.

 Esistono diverse attività che Visual Studio coordina per l'utente:There are several tasks that Visual Studio coordinates for you:

- Visualizza una struttura ad albero di tutti i tipi di progetto disponibili.

- Visualizza un elenco di modelli di applicazione per ogni tipo di progetto e consente di sceglierne uno.

- Raccoglie informazioni sul progetto per l'applicazione, ad esempio il nome e il percorso del progetto.

- Passa queste informazioni alla factory del progetto.

- Genera elementi di progetto e cartelle nella soluzione corrente.

## <a name="the-new-project-dialog-box"></a>Finestra di dialogo Nuovo progetto
 Tutto inizia quando si seleziona un tipo di progetto per un nuovo progetto. Per iniziare, scegliere **Nuovo progetto** dal menu **File.** Viene visualizzata la finestra di dialogo **Nuovo progetto,** simile alla seguente:

 ![Finestra di dialogo Nuovo progetto](../../extensibility/internals/media/newproject.gif "NewProject")

 Di seguito si spiegherà meglio questo concetto. Nella struttura **Tipi progetto** sono elencati i vari tipi di progetto che è possibile creare. Quando si seleziona un tipo di progetto, ad **esempio Windows Visual C,** verrà visualizzato un elenco di modelli di applicazione per iniziare. **I modelli installati** di Visual Studio vengono installati da Visual Studio e sono disponibili per qualsiasi utente del computer. I nuovi modelli creati o raccolti possono essere aggiunti a **Modelli personali** e sono disponibili solo per l'utente.

 Quando si seleziona un modello come **Applicazione Windows**, nella finestra di dialogo viene visualizzata una descrizione del tipo di applicazione. in questo caso, **un progetto per la creazione di un'applicazione con un'interfaccia utente**di Windows .

 Nella parte inferiore della finestra di dialogo **Nuovo progetto** verranno visualizzati diversi controlli che raccolgono ulteriori informazioni. I controlli visualizzati dipendono dal tipo di progetto, ma in genere includono una casella di testo **Nome** progetto, una casella di testo **Percorso** e il pulsante **Sfoglia** correlato e una casella di testo **Nome soluzione** e la casella di controllo Crea directory **per soluzione** correlata.

## <a name="populating-the-new-project-dialog-box"></a>Popolamento della finestra di dialogo Nuovo progetto
 Da dove viene ottenuta la finestra di dialogo **Nuovo progetto?** Ci sono due meccanismi al lavoro qui, uno dei quali deprecato. La finestra di dialogo **Nuovo progetto** combina e visualizza le informazioni ottenute da entrambi i meccanismi.

 Il metodo precedente (deprecato) utilizza le voci del Registro di sistema e i file VSDIR. Questo meccanismo viene eseguito all'apertura di Visual Studio.This mechanism runs when Visual Studio opened. Il metodo più recente utilizza i file .vstemplate. Questo meccanismo viene eseguito quando Visual Studio viene inizializzato, ad esempio eseguendo

```
devenv /setup
```

 o

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipi di progetto
 La posizione e i nomi dei nodi radice dei tipi di **progetto,** ad esempio **Visual C,** e **altri linguaggi**, sono determinati dalle voci del Registro di sistema. L'organizzazione dei nodi figlio, ad esempio **Database** e **Smart Device**, rispecchia la gerarchia delle cartelle che contengono i file .vstemplate corrispondenti. Esaminiamo prima i nodi radice.

#### <a name="project-type-root-nodes"></a>Nodi radice del tipo di progettoProject Type Root Nodes
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato, attraversa le sottochiavi della chiave del Registro di sistema di sistema HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft Microsoft VisualStudio 14.0, NewProjectTemplates, TemplateDirs per compilare e denominare i nodi radice della struttura ad albero dei tipi di **progetto.** Queste informazioni vengono memorizzate nella cache per un utilizzo successivo. Osservare la chiave\\TemplateDirs -FAE04EC1-301F-11D3-BF4B-00C04F79EFBC /1.\\ Ogni voce è un GUID VSPackage.Each entry is a VSPackage GUID. Il nome della sottochiave (/1) viene ignorato, ma la sua presenza indica che si tratta di un nodo radice di tipi di **progetto.** Un nodo radice può a sua volta avere diverse sottochiavi che ne controllano l'aspetto nella struttura ad albero dei tipi di **progetto.** Diamo un'occhiata ad alcuni di loro.

##### <a name="default"></a>Valore predefinito.
 Si tratta dell'ID risorsa della stringa localizzata che denomina il nodo radice. La risorsa di stringa si trova nella DLL satellite selezionata dal GUID VSPackage.

 Nell'esempio, il GUID VSPackage è

 -FAE04EC1-301F-11D3-BF4B-00C04F79EFBC

 e l'ID risorsa (valore predefinito) del nodo radice (/1) è #2345

 Se si cerca il GUID nella chiave Packages vicina ed esaminare la sottochiave SatelliteDll, è possibile trovare il percorso dell'assembly che contiene la risorsa stringa:

 \<Percorso di installazione di Visual Studio>

 Per verificarlo, aprire Esplora file e trascinare csprojui.dll nella directory di Visual Studio.. Nella tabella delle stringhe viene illustrato che #2345 di risorsa è riportata la didascalia **di Visual C.**

##### <a name="sortpriority"></a>SortPriority (Priorità ordinamento)
 Ciò determina la posizione del nodo radice nella struttura ad albero Tipi di **progetto.**

 SortPriority REG_DWORD 0x00000014 (20)

 Minore è il numero della priorità, maggiore è la posizione nell'albero.

##### <a name="developeractivity"></a>DeveloperActivity
 Se questa sottochiave è presente, la posizione del nodo radice è controllata dalla finestra di dialogo Impostazioni sviluppatore. Ad esempio,

 DeveloperActivity REG_SZ VC #

 indica che Visual Cè sarà un nodo radice [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] se Visual Studio è impostato per lo sviluppo. In caso contrario, sarà un nodo figlio di **Other Languages**.

##### <a name="folder"></a>Cartella
 Se questa sottochiave è presente, il nodo radice diventa un nodo figlio della cartella specificata. Sotto la chiave viene visualizzato un elenco di cartelle possibili

 HKEY_LOCAL_MACHINE SOFTWARE , Microsoft Microsoft Visual Studio 11.0 , NewProjectTemplates , PseudoFolders

 Ad esempio, la voce Progetti di Database dispone di una chiave Cartella che corrisponde alla voce Altri tipi di progetto in PseudoFolders. Pertanto, nella struttura ad albero Tipi di **progetto,** **Progetti** di database sarà un nodo figlio di **altri tipi di progetto**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nodi figlio di tipo progetto e file con estensione vstdirProject Type Child Nodes and .vstdir Files
 La posizione dei nodi figlio nella struttura tipi di **progetto** segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per i modelli di computer **(modelli di Visual Studio installati**), il percorso tipico è**My templates**\\. Le gerarchie di cartelle da queste due posizioni vengono unite per creare la struttura **Tipi di progetto.**

 Per Visual Studio con le impostazioni di sviluppo di C, l'albero dei tipi di progetto è simile al seguente:For Visual Studio with C' developer settings, **the Project types** tree looks something like this:

 ![Tipi di progetto](../../extensibility/internals/media/projecttypes.png "Tipi di progettoProjectTypes")

 La cartella ProjectTemplates corrispondente è simile alla seguente:

 ![Modelli di progetto](../../extensibility/internals/media/projecttemplates.png "Modelli di progetto")

 Quando si apre la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra di dialogo **Nuovo progetto,** attraversa la cartella ProjectTemplates e ne ricrea la struttura nella struttura **Tipi di progetto** con alcune modifiche:

- Il nodo radice nella struttura ad albero Tipi di **progetto** è determinato dal modello di applicazione.

- Il nome del nodo può essere localizzato e può contenere caratteri speciali.

- L'ordinamento può essere modificato.

##### <a name="finding-the-root-node-for-a-project-type"></a>Individuazione del nodo radice per un tipo di progettoFinding the Root Node for a Project Type
 Quando Visual Studio attraversa le cartelle ProjectTemplates, apre tutti i file con estensione zip ed estrae tutti i file con estensione vstemplate. Un file .vstemplate utilizza XML per descrivere un modello di applicazione. Per ulteriori informazioni, vedere Nuova generazione di [progetto: sotto il cofano, seconda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Il \<tag ProjectType> determina il tipo di progetto per l'applicazione. Ad esempio, il file .zip di WindowsCE 1033 con estensione EmptyProject contiene un file EmptyProject.vstemplate con questo tag:

```
<ProjectType>CSharp</ProjectType>
```

 Il \<tag ProjectType> e non la sottocartella nella cartella ProjectTemplates determina il nodo radice di un'applicazione nella struttura ad albero Tipi di **progetto.** Nell'esempio, le applicazioni Windows CE verrebbero visualizzate sotto il nodo radice di **Visual C,** e anche se si spostasse la cartella WindowsCE nella cartella VisualBasic, le applicazioni Windows CE verrebbero comunque visualizzate sotto il nodo radice di **Visual C.**

##### <a name="localizing-the-node-name"></a>Localizzazione del nome del nodoLocalizing the Node Name
 Quando Visual Studio attraversa le cartelle ProjectTemplates, esamina tutti i file con estensione vstdir trovati. Un file .vstdir è un file XML che controlla l'aspetto del tipo di progetto nella finestra di dialogo **Nuovo progetto.** Nel file vstdir utilizzare \<il tag LocalizedName> per denominare il nodo **Tipi** progetto.

 Ad esempio, il file di , CSharp, Database, TemplateIndex.vstdir, contiene questo tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 In questo modo vengono determinati la DLL satellite e l'ID risorsa della stringa localizzata che denomina il nodo radice, in questo caso **Database**. Il nome localizzato può contenere caratteri speciali non disponibili per i nomi delle cartelle, ad esempio **.NET**.

 Se \<non è presente alcun tag LocalizedName>, il tipo di progetto viene denominato dalla cartella stessa, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Ricerca dell'ordinamento per un tipo di progetto
 Per determinare l'ordinamento del tipo di progetto, \<i file vstdir utilizzano il tag> SortOrder.

 Ad esempio, il file di Windows.vstdir di Windows.vstdir contiene questo tag:

```
<SortOrder>5</SortOrder>
```

 Il file di , CSharp, Database, TemplateIndex.vstdir, dispone di un tag con un valore maggiore:

```
<SortOrder>5000</SortOrder>
```

 Più basso è \<il numero nel SortOrder> tag, maggiore è la posizione nella struttura ad albero, in modo che il nodo **Windows** viene visualizzato superiore al **Database** nodo nella struttura tipi di **progetto.**

 Se \<non viene specificato alcun tag sortOrder> per un tipo di \<progetto, viene visualizzato in ordine alfabetico seguendo tutti i tipi di progetto che contengono le specifiche di SortOrder>.

 Si noti che non sono presenti file con estensione vstdir nelle cartelle Documenti (**Modelli**personali ). I nomi dei tipi di progetto dell'applicazione utente non sono localizzati e vengono visualizzati in ordine alfabetico.

#### <a name="a-quick-review"></a>Una rapida revisione
 È possibile modificare la finestra di dialogo **Nuovo progetto** e creare un nuovo modello di progetto utente.

1. Aggiungere una sottocartella MyProjectNode alla cartella .

2. Creare un file MyProject.vstdir nella cartella MyProjectNode utilizzando qualsiasi editor di testo.

3. Aggiungere queste righe al file .vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Salvare e chiudere il file VS.vstdir.

5. Creare un file MyProject.vstemplate nella cartella MyProjectNode utilizzando qualsiasi editor di testo.

6. Aggiungere queste righe al file .vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Salvare il file .vstemplate e chiudere l'editor.

8. Inviare il file .vstemplate a una nuova cartella MyProjectNode.zip compressa.

9. Nella finestra di comando di Visual Studio digitare:

    ```
    devenv /installvstemplates
    ```

   Aprire Visual Studio.

10. Aprire la finestra di dialogo **Nuovo progetto** ed espandere il nodo del progetto di **Visual C.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** viene visualizzato come nodo figlio di Visual C, appena sotto il nodo Windows.

## <a name="see-also"></a>Vedere anche
- [Generazione di un nuovo progetto: dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
