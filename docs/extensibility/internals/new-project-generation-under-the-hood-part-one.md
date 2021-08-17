---
title: 'Nuova Project generazione: Under the Hood, Part One | Microsoft Docs'
description: Esaminare in dettaglio cosa accade nell'ambiente Visual Studio di sviluppo integrato (IDE) durante la creazione del proprio tipo di progetto (parte 1 di 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 308ed373ecfbecf29702a338ac6a595775c29d2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063200"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generazione nuovo progetto: Dietro le quinte, prima parte
Si è mai pensato a come creare un tipo di progetto personalizzato? Cosa accade effettivamente quando si crea un nuovo progetto? Diamo un'occhiata sotto il cofano e vediamo cosa sta realmente succedendo.

 Esistono diverse attività che Visual Studio coordinate:

- Visualizza un albero di tutti i tipi di progetto disponibili.

- Visualizza un elenco di modelli di applicazione per ogni tipo di progetto e consente di selezionarne uno.

- Raccoglie informazioni sul progetto per l'applicazione, ad esempio il nome e il percorso del progetto.

- Passa queste informazioni alla factory del progetto.

- Genera elementi di progetto e cartelle nella soluzione corrente.

## <a name="the-new-project-dialog-box"></a>Finestra di dialogo Nuovo Project
 Tutto inizia quando si seleziona un tipo di progetto per un nuovo progetto. Per iniziare, scegliere **Nuovo Project** dal menu **File.** Verrà **visualizzata la Project** di dialogo Nuovo Project con un aspetto simile al seguente:

 ![Screenshot della finestra di dialogo Nuovo progetto.](../../extensibility/internals/media/newproject.gif)

 Di seguito si spiegherà meglio questo concetto. **L Project albero dei tipi** di progetto elenca i vari tipi di progetto che è possibile creare. Quando si seleziona un tipo di progetto come **Visual C# Windows**, verrà visualizzato un elenco di modelli di applicazione per iniziare. **Visual Studio i modelli** installati vengono installati da Visual Studio e sono disponibili per qualsiasi utente del computer. I nuovi modelli creati o raccolti possono essere aggiunti a **Modelli** personali e sono disponibili solo per l'utente.

 Quando si seleziona un modello come **Windows App,** nella finestra di dialogo viene visualizzata una descrizione del tipo di applicazione. In questo caso, **un progetto per la creazione di un'applicazione con un'Windows utente.**

 Nella parte inferiore della **finestra di dialogo Project** vengono visualizzati diversi controlli che raccolgono altre informazioni. I controlli visualizzati dipendono dal tipo di progetto,  ma in  genere includono una  casella di  testo Nome progetto, una casella di testo Percorso e il pulsante Sfoglia correlato, una casella di testo Nome soluzione e la casella di controllo Crea **directory** per soluzione correlata.

## <a name="populating-the-new-project-dialog-box"></a>Popolamento della finestra di dialogo Project nuova finestra di dialogo
 Da dove viene **visualizzata la Project** nuova finestra di dialogo? Esistono due meccanismi in fase di funzionamento, uno dei quali è deprecato. La **finestra di dialogo** Project combina e visualizza le informazioni ottenute da entrambi i meccanismi.

 Il metodo precedente (deprecato) usa le voci del Registro di sistema e i file vsdir. Questo meccanismo viene eseguito all'Visual Studio aperto. Il metodo più recente usa i file con estensione vstemplate. Questo meccanismo viene eseguito quando Visual Studio viene inizializzato, ad esempio eseguendo

```
devenv /setup
```

 oppure

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipi di progetto
 La posizione e i nomi dei Project **radice** dei tipi, ad esempio **Visual C#** e **Altri** linguaggi, sono determinati dalle voci del Registro di sistema. L'organizzazione dei nodi figlio, ad esempio **Database** e **Smart Device,** rispecchia la gerarchia delle cartelle che contengono i file con estensione vstemplate corrispondenti. Si esaminino prima i nodi radice.

#### <a name="project-type-root-nodes"></a>Project Tipi di nodi radice
 Quando viene inizializzata, attraversa le sottochiavi della chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs per compilare e assegnare un nome ai nodi radice dell'albero Project [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **tipi di** dati. Queste informazioni vengono memorizzate nella cache per un uso successivo. Esaminare la chiave TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1. Ogni voce è un GUID VSPackage. Il nome della sottochiave (/1) viene ignorato, ma la relativa presenza indica che si tratta di un nodo radice Project **tipi.** Un nodo radice può a sua volta avere diverse sottochiavi che ne controllano l'aspetto **nell'Project albero dei tipi di** dati. Di seguito sono riportati alcuni di essi.

##### <a name="default"></a>Valore predefinito.
 Si tratta dell'ID risorsa della stringa localizzata che indica il nome del nodo radice. La risorsa stringa si trova nella DLL satellite selezionata dal GUID del pacchetto VSPackage.

 Nell'esempio il GUID di VSPackage è

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 e l'ID risorsa (valore predefinito) del nodo radice (/1) è #2345

 Se si cerca il GUID nella chiave Packages vicina ed si esamina la sottochiave SatelliteDll, è possibile trovare il percorso dell'assembly che contiene la risorsa stringa:

 \<Visual Studio installation path>\VC#\VCSPackages\1033\csprojui.dll

 Per verificarlo, aprire il Esplora file e trascinare csprojui.dll nella directory Visual Studio.. La tabella delle stringhe mostra che la #2345 ha la didascalia **Visual C#**.

##### <a name="sortpriority"></a>SortPriority
 Ciò determina la posizione del nodo radice nell'albero **Project tipi di** dati.

 SortPriority REG_DWORD 0x00000014 (20)

 Minore è il numero della priorità, maggiore sarà la posizione nell'albero.

##### <a name="developeractivity"></a>DeveloperActivity
 Se questa sottochiave è presente, la posizione del nodo radice viene controllata dalla finestra di dialogo Impostazioni sviluppatore. Ad esempio,

 DeveloperActivity REG_SZ VC #

 indica che Visual C# sarà un nodo radice se Visual Studio è impostato per lo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] sviluppo. In caso contrario, sarà un nodo figlio di **Altri linguaggi**.

##### <a name="folder"></a>Cartella
 Se questa sottochiave è presente, il nodo radice diventa un nodo figlio della cartella specificata. Sotto la chiave viene visualizzato un elenco di cartelle possibili

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Ad esempio, la voce Progetti di database ha una chiave cartella che corrisponde alla voce Altri Project tipi in PseudoCartelle. Nell'albero **dei Project,** progetti di **database** sarà quindi un nodo figlio di **Altri Project tipi**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Project Digitare nodi figlio e file con estensione vstdir
 La posizione dei nodi figlio **nell'albero Project** tipi di dati segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per i modelli di computer (**Visual Studio** modelli installati ), il percorso tipico è \Programmi\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ e per i modelli utente (**Modelli** personali ), il percorso tipico è \Documenti\Visual Studio 14.0\Templates\ProjectTemplates \\ . Le gerarchie di cartelle di queste due posizioni vengono unite per creare **l'Project di tipi.**

 Per Visual Studio con le impostazioni per sviluppatori **C#, l'albero Project tipi** di dati è simile al seguente:

 ![Screenshot dell'albero Project cartelle dei tipi di Visual Studio con le impostazioni per sviluppatori C#.](../../extensibility/internals/media/projecttypes.png)

 La cartella ProjectTemplates corrispondente è simile alla seguente:

 ![Screenshot dell'albero Project della cartella Templates in Visual Studio con le impostazioni per sviluppatori C#.](../../extensibility/internals/media/projecttemplates.png)

 Quando si **apre la finestra di** dialogo Nuovo Project, attraversa la cartella ProjectTemplates e ne ricrea la struttura nell'albero Project tipi di dati [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con alcune modifiche: 

- Il nodo radice **nell'albero Project tipi** di dati è determinato dal modello di applicazione.

- Il nome del nodo può essere localizzato e può contenere caratteri speciali.

- L'ordinamento può essere modificato.

##### <a name="finding-the-root-node-for-a-project-type"></a>Ricerca del nodo radice per un tipo Project radice
 Quando Visual Studio attraversa le cartelle ProjectTemplates, apre tutti .zip file ed estrae tutti i file con estensione vstemplate. Un file con estensione vstemplate usa XML per descrivere un modello di applicazione. Per altre informazioni, vedere [New Project Generation: Under the Hood, Part Two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Il \<ProjectType> tag determina il tipo di progetto per l'applicazione. Ad esempio, il file \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un file EmptyProject.vstemplate con questo tag:

```
<ProjectType>CSharp</ProjectType>
```

 Il tag e non la sottocartella nella cartella ProjectTemplates determinano il nodo radice di \<ProjectType> un'applicazione **nell'albero Project tipi di** dati. Nell'esempio, le applicazioni Windows CE verrebbero visualizzate sotto il nodo radice **di Visual C#** e anche se si spostasse la cartella WindowsCE nella cartella VisualBasic, le applicazioni Windows CE verrebbero comunque visualizzate sotto il nodo radice **Visual C#.**

##### <a name="localizing-the-node-name"></a>Localizzazione del nome del nodo
 Quando Visual Studio attraversa le cartelle ProjectTemplates, esamina tutti i file con estensione vstdir trovati. Un file con estensione vstdir è un file XML che controlla l'aspetto del tipo di progetto nella finestra di **dialogo Nuovo** Project. Nel file con estensione vstdir usare il tag per assegnare un nome \<LocalizedName> al nodo Project tipi **di** dati.

 Ad esempio, il file \CSharp\Database\TemplateIndex.vstdir contiene questo tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Ciò determina la DLL satellite e l'ID risorsa della stringa localizzata che nomino il nodo radice, in questo caso **Database**. Il nome localizzato può contenere caratteri speciali che non sono disponibili per i nomi di cartella, ad esempio **.NET.**

 Se non è presente alcun tag, il tipo \<LocalizedName> di progetto viene denominato dalla cartella **stessa, SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Ricerca dell'ordinamento per un tipo Project dati
 Per determinare l'ordinamento del tipo di progetto, i file con estensione vstdir usano il \<SortOrder> tag .

 Ad esempio, il file \CSharp\Windows\Windows.vstdir contiene questo tag:

```
<SortOrder>5</SortOrder>
```

 Il file \CSharp\Database\TemplateIndex.vstdir ha un tag con un valore più grande:

```
<SortOrder>5000</SortOrder>
```

 Minore è il numero nel tag, maggiore sarà la posizione nell'albero, quindi il nodo Windows verrà visualizzato più in alto rispetto al nodo Database nell'albero \<SortOrder> Project tipi **di** dati.  

 Se non viene specificato alcun tag per un tipo di progetto, viene visualizzato in ordine alfabetico dopo \<SortOrder> tutti i tipi di progetto che contengono \<SortOrder> specifiche.

 Si noti che non sono presenti file con estensione vstdir nelle Documenti (**Modelli** personali ). I nomi dei tipi di progetto dell'applicazione utente non sono localizzati e vengono visualizzati in ordine alfabetico.

#### <a name="a-quick-review"></a>Una revisione rapida
 Modificare la finestra di **dialogo Nuovo Project** e creare un nuovo modello di progetto utente.

1. Aggiungere una sottocartella MyProjectNode alla cartella \Programmi\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.

2. Creare un file MyProject.vstdir nella cartella MyProjectNode usando qualsiasi editor di testo.

3. Aggiungere queste righe al file con estensione vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Salvare e chiudere il file con estensione vstdir.

5. Creare un file MyProject.vstemplate nella cartella MyProjectNode usando qualsiasi editor di testo.

6. Aggiungere queste righe al file con estensione vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Salvare il file con estensione vstemplate e chiudere l'editor.

8. Inviare il file con estensione vstemplate a una nuova cartella MyProjectNode\MyProject.zip compressa.

9. Nella finestra Visual Studio comando digitare:

    ```
    devenv /installvstemplates
    ```

   Aprire Visual Studio.

10. Aprire la **finestra di Project** nuovo progetto ed espandere il nodo del progetto Visual **C#.**

    ![Screenshot dell'Project di cartelle dei tipi di progetto nella finestra di dialogo Nuovo Project con MyProjectNode evidenziato nel nodo del progetto Visual C# espanso.](../../extensibility/internals/media/myprojectnode.png)

    **MyProjectNode viene** visualizzato come nodo figlio di Visual C# sotto il nodo Windows progetto.

## <a name="see-also"></a>Vedi anche
- [Generazione nuovo progetto: Dietro le quinte, seconda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
