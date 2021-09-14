---
title: 'Procedura dettagliata: Estensione Esplora server per la visualizzazione Web part | Microsoft Docs'
titleSuffix: ''
description: In questa procedura dettagliata, estendere Esplora server in modo che visualizzi la raccolta di web part in ogni sito SharePoint connesso.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7654b6b4f73ea3245cb4d21480eb4db4ceabc648
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628211"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Procedura dettagliata: Estendere Esplora server per visualizzare web part
  In Visual Studio è possibile usare  il nodo Connessioni SharePoint di **Esplora server** per visualizzare i componenti nei SharePoint siti. Tuttavia, **Esplora server** non visualizza alcuni componenti per impostazione predefinita. In questa procedura dettagliata si **estenderà** il Esplora server in modo che visualizzi la raccolta di web part in ogni sito SharePoint connesso.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- La creazione Visual Studio un'estensione che estende **Esplora server** nei modi seguenti:

  - L'estensione aggiunge **un nodo Raccolta web** part in ogni SharePoint del sito in **Esplora server**. Questo nuovo nodo contiene nodi figlio che rappresentano ogni web part nella raccolta di web part nel sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di web part. Questo nuovo tipo di nodo è la base per i nodi figlio nel nuovo **nodo Raccolta web** part. Il nuovo tipo di nodo Web part visualizza informazioni **nella finestra Proprietà** relative alla web part che rappresenta. Il tipo di nodo include anche una voce di menu di scelta rapida personalizzata che è possibile usare come punto di partenza per l'esecuzione di altre attività correlate alla web part.

- Creare due comandi SharePoint personalizzati che l'assembly di estensione chiama. SharePoint comandi sono metodi che possono essere chiamati dagli assembly di estensione per usare le API nel modello a oggetti del server per SharePoint. In questa procedura dettagliata vengono creati comandi che recuperano informazioni sulla web part dal sito SharePoint locale nel computer di sviluppo. Per altre informazioni, vedere [Chiamare i modelli SharePoint a oggetti.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Compilazione di un pacchetto vsix (Visual Studio Extension) per distribuire l'estensione.

- Debug e test dell'estensione.

> [!NOTE]
> Per una versione alternativa di questa procedura dettagliata che usa il modello a oggetti client per SharePoint anziché il relativo modello a oggetti server, vedere [Procedura dettagliata:](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)Chiamare il modello a oggetti client di SharePoint in un'estensione Esplora server .

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- SDK Visual Studio. Questa procedura dettagliata usa il **modello Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Utilizzo del modello a oggetti del server per SharePoint. Per altre informazioni, vedere [Using the SharePoint Foundation Server-Side Object Model](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Web part in SharePoint soluzioni. Per altre informazioni, vedere [panoramica Web part.](/previous-versions/office/ms432401(v=office.14))

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.

- Progetto di libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione .NET Framework 4.5.

- Progetto di libreria di classi che definisce i comandi SharePoint personalizzati. Questo progetto deve essere the.NET Framework 3.5.

  Iniziare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

3. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **nodo Extensibility.**

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

5. Scegliere il **modello di Project VSIX,** assegnare al progetto il nome **WebPartNode** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto WebPartNode** **a Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra di **dialogo Project** nuovo nodo espandere il  nodo **Visual C#** o il nodo Visual Basic e quindi scegliere Windows **nodo.**

3. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **Libreria di** classi, assegnare al progetto il nome **WebPartNodeExtension** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto WebPartNodeExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto SharePoint comandi

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra di **dialogo Project** nuovo nodo espandere il  nodo **Visual C#** o il nodo Visual Basic e quindi scegliere il **Windows** nodo.

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 3.5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **Libreria di** classi, assegnare al progetto il nome **WebPartCommands** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto WebPartCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere file di codice e riferimenti ad assembly e configurare le impostazioni del progetto.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Per configurare il progetto WebPartNodeExtension

1. Nel progetto WebPartNodeExtension aggiungere quattro file di codice con i nomi seguenti:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Aprire il menu di scelta rapida **per il progetto WebPartNodeExtension** e quindi scegliere **Aggiungi riferimento.**

3. Nella finestra di dialogo Gestione riferimenti **- WebPartNodeExtension** scegliere la scheda **Framework** e quindi selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Scegliere la **scheda** Estensioni e selezionare la casella di controllo per Microsoft.VisualStudio. SharePoint assembly, quindi scegliere **il pulsante OK.**

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il **nodo del progetto WebPartNodeExtension** e quindi scegliere **Proprietà.**

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nella casella **Spazio dei nomi** predefinito (C#) o Spazio **dei** nomi radice ( ) [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] immettere **ServerExplorer.SharePointConnections.WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Per configurare il progetto webpartcommands

1. Nel progetto WebPartCommands aggiungere un file di codice denominato WebPartCommands.

2. In Esplora soluzioni aprire il menu di scelta rapida per il nodo del progetto **WebPartCommands,** scegliere **Aggiungi** **e** quindi elemento **esistente.**

3. Nella **finestra** di dialogo Aggiungi elemento esistente passare alla cartella che contiene i file di codice per il progetto WebPartNodeExtension e quindi scegliere i file di codice WebPartNodeInfo e WebPartCommandIds.

4. Scegliere la freccia accanto al **pulsante** Aggiungi e quindi scegliere **Aggiungi come** collegamento nel menu visualizzato.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge i file di codice al progetto WebPartCommands come collegamenti. Di conseguenza, i file di codice si trovano nel progetto WebPartNodeExtension, ma anche il codice nei file viene compilato nel progetto WebPartCommands.

5. Aprire di nuovo il menu di scelta rapida per il progetto **WebPartCommands** e scegliere **Aggiungi riferimento.**

6. Nella finestra di dialogo Gestione riferimenti -  **WebPartCommands** scegliere la scheda Estensioni, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere il **pulsante OK:**

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Comandi

7. In **Esplora soluzioni** aprire di nuovo il menu di scelta rapida per il **progetto WebPartCommands** e quindi scegliere **Proprietà.**

     Si apre la finestra **Creazione progetti**.

8. Scegliere la scheda **Applicazione**.

9. Nella casella **Spazio dei nomi** predefinito (C#) o Spazio **dei** nomi radice ( ) [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] immettere **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creare icone per i nuovi nodi
 Creare due icone per **l'Esplora server** web part: un'icona per il nuovo nodo Raccolta **web part** e un'altra icona per ogni nodo web part figlio nel nodo Raccolta **web** part. Più avanti in questa procedura dettagliata si scriverà il codice che associa queste icone ai nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare icone per i nodi

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto WebPartNodeExtension** e quindi scegliere **Proprietà.**

2. Si apre la finestra **Creazione progetti**.

3. Scegliere la **scheda** Risorse e quindi scegliere Il **progetto non contiene un file di risorse predefinito. Fare clic qui per creare un collegamento.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea un file di risorse e lo apre nella finestra di progettazione.

4. Nella parte superiore della finestra di progettazione scegliere la freccia accanto al comando di **menu** Aggiungi risorsa e quindi scegliere **Aggiungi** nuova icona nel menu visualizzato.

5. Nella finestra **di dialogo Aggiungi** nuova risorsa assegnare alla nuova icona il nome **WebPartsNode** e quindi scegliere **il pulsante** Aggiungi.

     La nuova icona viene aperta **nell'editor di immagini**.

6. Modificare la versione 16x16 dell'icona in modo che abbia un design facilmente riconoscibile.

7. Aprire il menu di scelta rapida per la versione 32x32 dell'icona e quindi scegliere **Elimina tipo di immagine**.

8. Ripetere i passaggi da 5 a 8 per aggiungere una seconda icona alle risorse del progetto e assegnare a questa icona il nome **WebPart**.

9. In **Esplora soluzioni**, nella **cartella Resources** per il progetto **WebPartNodeExtension** aprire il menu di scelta rapida **per WebPartsNode.ico.**

10. Nella finestra **Proprietà** scegliere la freccia accanto a **Azione** di compilazione e quindi scegliere **Risorsa** incorporata dal menu visualizzato.

11. Ripetere gli ultimi due passaggi per **WebPart.ico.**

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo Raccolta web part Esplora server
 Creare una classe che aggiunge il nuovo **nodo Raccolta web part** a ogni SharePoint del sito. Per aggiungere il nuovo nodo, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio l'aggiunta di un nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo Raccolta web part Esplora server

1. Nel progetto WebPartNodeExtension aprire il file di codice SiteNodeExtension e incollarlo al suo interno.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto avrà alcuni errori di compilazione, ma non verranno aggiunti quando si aggiunge il codice nei passaggi successivi.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una web part. Visual Studio questo nuovo tipo di nodo per visualizzare i nodi figlio nel **nodo Raccolta web** part. Ogni nodo figlio rappresenta una singola web part nel SharePoint sito.

 Per definire il nuovo tipo di nodo, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di nodo in **Esplora server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo web part

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartNodeTypeProvder e incollarlo al suo interno.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::

## <a name="define-the-web-part-data-class"></a>Definire la classe di dati della web part
 Definire una classe che contiene dati su una singola web part nel SharePoint sito. Più avanti in questa procedura dettagliata verrà creato un comando SharePoint personalizzato che recupera i dati su ogni web part nel sito e quindi assegna i dati alle istanze di questa classe.

#### <a name="to-define-the-web-part-data-class"></a>Per definire la classe di dati della web part

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartNodeInfo e incollarlo al suo interno.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs" id="Snippet3":::

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definire gli ID per i comandi SharePoint comando
 Definire diverse stringhe che identificano i comandi SharePoint personalizzati. Questi comandi verranno implementati più avanti in questa procedura dettagliata.

#### <a name="to-define-the-command-ids"></a>Per definire gli ID dei comandi

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartCommandIds e incollarlo al suo interno.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb" id="Snippet4":::

## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi SharePoint personalizzati
 Creare comandi personalizzati che chiamano nel modello a oggetti del server per SharePoint recuperare i dati sulla Web part nel SharePoint sito. Ogni comando è un metodo a cui è <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applicato l'oggetto .

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi SharePoint comando

1. Nel progetto WebPartCommands aprire il file di codice WebPartCommands e incollarlo al suo interno.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb" id="Snippet6":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il nodo **Raccolta web part** e i comandi SharePoint sono ora presenti nei progetti. Compilare la soluzione per assicurarsi che entrambi i progetti siano compilati senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

    > [!WARNING]
    > A questo punto, il progetto WebPartNode potrebbe avere un errore di compilazione perché il file manifesto VSIX non ha un valore per Author. Questo errore verrà visualizzato quando si aggiunge un valore nei passaggi successivi.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare prima di tutto il pacchetto VSIX modificando il file source.extension.vsixmanifest nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. In **Esplora soluzioni** nel progetto WebPartNode aprire il file **source.extension.vsixmanifest** nell'editor manifesto.

     Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Nome prodotto** immettere Nodo raccolta web part **per Esplora server**.

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere Aggiunge un nodo raccolta web part personalizzato al nodo SharePoint **connessioni in Esplora server. Questa estensione usa un comando SharePoint personalizzato per chiamare nel modello a oggetti del server.**

5. Scegliere la **scheda Asset** dell'editor e quindi scegliere **il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

7. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

8. **Nell'Project** scegliere **WebPartNodeExtension** e quindi fare clic sul **pulsante OK.**

9. Nell'editor del manifesto scegliere di **nuovo il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

10. Nella casella **Tipo** immettere **SharePoint. Commands.v4**.

    > [!NOTE]
    > Questo elemento specifica un'estensione personalizzata da includere nell'Visual Studio personalizzata. Per altre informazioni, vedere [Elemento Asset (schema VSX)](/previous-versions/dd393737(v=vs.110)).

11. **Nell'elenco Origine** scegliere **l'elemento A project in current solution** list (Progetto nella soluzione corrente).

12. **Nell'Project** selezionare **WebPartCommands** e quindi fare clic sul **pulsante OK.**

13. Sulla barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che  >  la soluzione venga compilata senza errori.

14. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contenga ora il file WebPartNode.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 A questo punto è possibile testare il nuovo **nodo Raccolta web part** in **Esplora server**. Avviare prima di tutto il debug dell'estensione in un'istanza sperimentale di Visual Studio. Usare quindi il nuovo nodo **Web part** nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e quindi aprire la soluzione WebPartNode.

2. Nel progetto WebPartNodeExtension aprire il file di codice SiteNodeExtension e quindi aggiungere un punto di interruzione alla prima riga di codice nei `NodeChildrenRequested` metodi `CreateWebPartNodes` e .

3. Premere **F5 per** avviare il debug.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery Node Extension per Esplora server\1.0 e avvia un'istanza sperimentale di Visual Studio. L'elemento di progetto verrà testato in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , sulla barra dei menu scegliere  >  **Visualizza Esplora server**.

2. Seguire questa procedura se il sito SharePoint da usare per i test  non viene visualizzato nel nodo Connessioni SharePoint in **Esplora server**:

    1. In **Esplora server** aprire il menu di scelta rapida per SharePoint **connessioni** e quindi scegliere **Aggiungi connessione**.

    2. Nella finestra **di dialogo Aggiungi** SharePoint connessione immettere l'URL del sito SharePoint a cui si vuole connettersi e quindi scegliere **OK.**

         Per specificare il SharePoint nel computer di sviluppo, immettere **http://localhost** .

3. Espandere il nodo di connessione del sito (che visualizza l'URL del sito) e quindi espandere un nodo del sito figlio, ad esempio **Sito del team**.

4. Verificare che il codice nell'altra istanza di si arresti nel punto di interruzione impostato in precedenza nel metodo e quindi scegliere F5 per continuare a eseguire il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] `NodeChildrenRequested` debug del progetto. 

5. Nell'istanza sperimentale di Visual Studio verificare che venga visualizzato un nuovo nodo denominato **Raccolta** web part nel nodo del sito di primo livello e quindi espandere il **nodo Raccolta web** part.

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti sul punto di interruzione impostato in precedenza nel metodo e quindi scegliere F5 per continuare a eseguire il `CreateWebPartNodes` debug del progetto. 

7. Nell'istanza sperimentale di Visual Studio verificare che tutti i Web part nel sito connesso siano visualizzati nel nodo **Raccolta** web part in **Esplora server**.

8. In **Esplora server** aprire il menu di scelta rapida per una delle Web part e quindi scegliere **Proprietà**.

9. Nell'istanza di di cui si esegue il debug, verificare che i dettagli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sulla web part vengano visualizzati nella **finestra** Proprietà.

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Dopo aver completato il test dell'estensione, disinstallarla da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nell'istanza sperimentale di scegliere Strumenti Estensioni e aggiornamenti sulla [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] barra   >  **dei** menu.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Web Part Gallery Node Extension (Estensione** nodo raccolta web part) per Esplora server e quindi scegliere il pulsante **Disinstalla.**

3. Nella finestra di dialogo visualizzata  scegliere il pulsante Sì per confermare che si vuole disinstallare l'estensione e quindi scegliere il pulsante Riavvia **ora** per completare la disinstallazione.

4. Chiudere entrambe le istanze Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione WebPartNode).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Chiamare il modello SharePoint a oggetti client in un'Esplora server personalizzata](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di un'altra immagine &#40;editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)