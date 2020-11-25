---
title: 'Procedura dettagliata: estensione Esplora server per visualizzare Web part | Microsoft Docs'
titleSuffix: ''
description: In questa procedura dettagliata, estendere Esplora server in modo da visualizzare la raccolta web part in ogni sito di SharePoint connesso.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55950d8498b436d38d2145c2692556330718883e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970221"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Procedura dettagliata: estendere Esplora server per visualizzare le web part
  In Visual Studio è possibile usare il nodo **connessioni di SharePoint** di **Esplora server** per visualizzare i componenti nei siti di SharePoint. Tuttavia, per impostazione predefinita, **Esplora server** non visualizza alcuni componenti. In questa procedura dettagliata si estenderà **Esplora server** in modo da visualizzare la raccolta web part in ogni sito di SharePoint connesso.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che estende **Esplora server** nei modi seguenti:

  - L'estensione aggiunge un nodo della **raccolta di Web part** in ogni nodo del sito di SharePoint in **Esplora server**. Questo nuovo nodo contiene i nodi figlio che rappresentano ogni Web part nella raccolta web part sul sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza della web part. Questo nuovo tipo di nodo è la base per i nodi figlio nel nuovo nodo della **raccolta di Web part** . Il nuovo tipo di nodo Web part Visualizza informazioni nella finestra **Proprietà** relativa alla web part rappresentata. Il tipo di nodo include inoltre una voce di menu di scelta rapida personalizzata che è possibile utilizzare come punto di partenza per eseguire altre attività correlate alla web part.

- Creare due comandi di SharePoint personalizzati chiamati dall'assembly di estensione. I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensione per utilizzare le API nel modello a oggetti del server per SharePoint. In questa procedura dettagliata vengono creati i comandi che consentono di recuperare le informazioni sulla Web part dal sito di SharePoint locale nel computer di sviluppo. Per ulteriori informazioni, vedere [la pagina relativa alla chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Creazione di un pacchetto di estensione di Visual Studio (VSIX) per distribuire l'estensione.

- Debug e test dell'estensione.

> [!NOTE]
> Per una versione alternativa di questa procedura dettagliata che usa il modello a oggetti del client per SharePoint anziché il relativo modello a oggetti del server, vedere [procedura dettagliata: chiamare il modello a oggetti del client di SharePoint in un'estensione Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Utilizzo del modello a oggetti del server per SharePoint. Per ulteriori informazioni, vedere [utilizzo del modello a oggetti di SharePoint Foundation Server-Side](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Web part nelle soluzioni di SharePoint. Per ulteriori informazioni, vedere [Web part Overview](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.

- Progetto di libreria di classi che implementa l'estensione. Il progetto deve avere come destinazione il .NET Framework 4,5.

- Progetto di libreria di classi che definisce i comandi personalizzati di SharePoint. Questo progetto deve avere come destinazione the.NET Framework 3,5.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella finestra di dialogo  **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

5. Scegliere il modello di **progetto VSIX** , denominare il progetto **WebPartNode**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNode** a **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual C#** o il nodo **Visual Basic** , quindi il nodo scegliere **Windows** .

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **libreria di classi**, denominare il progetto **WebPartNodeExtension**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNodeExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella finestra di dialogo  **nuovo progetto** espandere il nodo **Visual C#** o il nodo **Visual Basic** , quindi scegliere il nodo **Windows** .

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 3,5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **libreria di classi**, denominare il progetto **WebPartCommands**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere il codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti ad assembly e configurare le impostazioni del progetto.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Per configurare il progetto WebPartNodeExtension

1. Nel progetto WebPartNodeExtension aggiungere quattro file di codice con i nomi seguenti:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Aprire il menu di scelta rapida per il progetto **WebPartNodeExtension** , quindi scegliere **Aggiungi riferimento**.

3. Nella finestra di dialogo **Gestione riferimenti-WebPartNodeExtension** scegliere la scheda **Framework** , quindi selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Scegliere la scheda **estensioni** , selezionare la casella di controllo per l'assembly Microsoft. VisualStudio. SharePoint, quindi scegliere il pulsante **OK** .

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto **WebPartNodeExtension** , quindi scegliere **proprietà**.

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nella casella **spazio dei nomi predefinito** (C#) o nella casella **spazio dei nomi radice** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) immettere **ServerExplorer. SharePointConnections. WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Per configurare il progetto WebPartCommands

1. Nel progetto WebPartCommands aggiungere un file di codice denominato WebPartCommands.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto **WebPartCommands** , scegliere **Aggiungi**, quindi **elemento esistente**.

3. Nella finestra di dialogo **Aggiungi elemento esistente** individuare la cartella che contiene i file di codice per il progetto WebPartNodeExtension, quindi scegliere i file di codice WebPartNodeInfo e WebPartCommandIds.

4. Scegliere la freccia accanto al pulsante **Aggiungi** , quindi scegliere **Aggiungi come collegamento** nel menu visualizzato.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge i file di codice al progetto WebPartCommands come collegamenti. Di conseguenza, i file di codice si trovano nel progetto WebPartNodeExtension, ma anche il codice nei file viene compilato nel progetto WebPartCommands.

5. Aprire di nuovo il menu di scelta rapida per il progetto **WebPartCommands** e scegliere **Aggiungi riferimento**.

6. Nella finestra di dialogo **Gestione riferimenti-WebPartCommands** scegliere la scheda **estensioni** , selezionare la casella di controllo per ognuno degli assembly seguenti, quindi scegliere il pulsante **OK** :

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

7. In **Esplora soluzioni** aprire di nuovo il menu di scelta rapida per il progetto **WebPartCommands** , quindi scegliere **proprietà**.

     Si apre la finestra **Creazione progetti**.

8. Scegliere la scheda **Applicazione**.

9. Nella casella **spazio dei nomi predefinito** (C#) o nella casella **spazio dei nomi radice** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) immettere **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creare icone per i nuovi nodi
 Creare due icone per l'estensione **Esplora server** : un'icona per il nuovo nodo **raccolta web part** e un'altra icona per ogni nodo Web part figlio sotto il nodo **raccolta web part** . Più avanti in questa procedura dettagliata verrà scritto il codice che associa queste icone ai nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare icone per i nodi

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **WebPartNodeExtension** , quindi scegliere **proprietà**.

2. Si apre la finestra **Creazione progetti**.

3. Scegliere la scheda **risorse** , quindi scegliere il **progetto non contiene un file di risorse predefinito. Fare clic qui per creare un** collegamento.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare un file di risorse e di aprirlo nella finestra di progettazione.

4. Nella parte superiore della finestra di progettazione scegliere la freccia accanto al comando di menu **Aggiungi risorsa** , quindi scegliere **Aggiungi nuova icona** nel menu visualizzato.

5. Nella finestra di dialogo **Aggiungi nuova risorsa** assegnare un nome alla nuova icona **WebPartsNode**, quindi scegliere il pulsante **Aggiungi** .

     La nuova icona verrà aperta nell' **editor di immagini**.

6. Modificare la versione di 16x16 dell'icona in modo che disponga di una progettazione che è possibile riconoscere facilmente.

7. Aprire il menu di scelta rapida per la versione 32x32 dell'icona, quindi scegliere **Elimina tipo di immagine**.

8. Ripetere i passaggi da 5 a 8 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **WebPart**.

9. In **Esplora soluzioni**, nella cartella **risorse** del progetto **WebPartNodeExtension** , aprire il menu di scelta rapida per **WebPartsNode. ico**.

10. Nella finestra **Proprietà** scegliere la freccia accanto a azione di **compilazione**, quindi scegliere **risorsa incorporata** nel menu visualizzato.

11. Ripetere gli ultimi due passaggi per **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo della raccolta web part alla Esplora server
 Creare una classe che aggiunga il nuovo nodo della **raccolta di Web part** a ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Implementare questa interfaccia quando si desidera estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio l'aggiunta di un nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo della raccolta web part a Esplora server

1. Nel progetto WebPartNodeExtension aprire il file di codice SiteNodeExtension e quindi incollare il codice seguente al suo interno.

    > [!NOTE]
    > Dopo l'aggiunta di questo codice, il progetto avrà alcuni errori di compilazione, ma non sarà più necessario quando si aggiunge il codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una Web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web part. Visual Studio usa questo nuovo tipo di nodo per visualizzare i nodi figlio nel nodo **raccolta web part** . Ogni nodo figlio rappresenta una singola Web part nel sito di SharePoint.

 Per definire il nuovo tipo di nodo, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Implementare questa interfaccia quando si desidera definire un nuovo tipo di nodo in **Esplora server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo Web part

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartNodeTypeProvder e quindi incollare il codice seguente al suo interno.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definire la classe di dati web part
 Definire una classe che contiene i dati relativi a una singola Web part nel sito di SharePoint. Più avanti in questa procedura dettagliata verrà creato un comando di SharePoint personalizzato che recupera i dati relativi a ogni Web part nel sito e quindi assegna i dati alle istanze di questa classe.

#### <a name="to-define-the-web-part-data-class"></a>Per definire la classe di dati web part

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartNodeInfo e quindi incollare il codice seguente al suo interno.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definire gli ID per i comandi di SharePoint
 Definire diverse stringhe che identificano i comandi personalizzati di SharePoint. Questi comandi vengono implementati più avanti in questa procedura dettagliata.

#### <a name="to-define-the-command-ids"></a>Per definire gli ID dei comandi

1. Nel progetto WebPartNodeExtension aprire il file di codice WebPartCommandIds e quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi personalizzati di SharePoint
 Creare comandi personalizzati che effettuano chiamate nel modello a oggetti del server per SharePoint per recuperare i dati relativi all'Web part nel sito di SharePoint. Ogni comando è un metodo a cui è <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applicato.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint

1. Nel progetto WebPartCommands aprire il file di codice WebPartCommands e quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il nodo della **raccolta web part** e i comandi di SharePoint sono ora inclusi nei progetti. Compilare la soluzione per assicurarsi che entrambi i progetti vengano compilati senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

    > [!WARNING]
    > A questo punto, il progetto WebPartNode potrebbe avere un errore di compilazione perché il file manifesto VSIX non ha un valore per Author. Questo errore si verifica quando si aggiunge un valore nei passaggi successivi.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest nel progetto VSIX. Quindi, creare il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto WebPartNode, aprire il file **source. Extension. vsixmanifest** nell'editor manifesto.

     Il file source. Extension. vsixmanifest è la base per il file Extension. vsixmanifest che tutti i pacchetti VSIX richiedono. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Nella casella **nome prodotto** , immettere **nodo Raccolta Web part per Esplora server**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **aggiungere un nodo della raccolta web part personalizzato al nodo connessioni di SharePoint in Esplora server. Questa estensione usa un comando di SharePoint personalizzato per chiamare il modello a oggetti del server.**

5. Scegliere la scheda **Asset** dell'editor, quindi scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nell'elenco  **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** scegliere **WebPartNodeExtension** , quindi scegliere il pulsante **OK** .

9. Nell'editor del manifesto scegliere di nuovo il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

10. Nella casella **tipo** immettere **SharePoint. Commands. v4**.

    > [!NOTE]
    > Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per altre informazioni, vedere [elemento asset (schema VSX)](/previous-versions/dd393737(v=vs.110)).

11. Nell'elenco **origine** scegliere il progetto nell'elemento dell'elenco **soluzione corrente** .

12. Nell'elenco **progetto** scegliere **WebPartCommands**, quindi scegliere il pulsante **OK** .

13. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

14. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contenga ora il file WebPartNode. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 A questo punto si è pronti per testare il nuovo nodo della **raccolta web part** in **Esplora server**. Innanzitutto, avviare il debug dell'estensione in un'istanza sperimentale di Visual Studio. Usare quindi il nuovo nodo **Web part** nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative, quindi aprire la soluzione WebPartNode.

2. Nel progetto WebPartNodeExtension aprire il file di codice SiteNodeExtension, quindi aggiungere un punto di interruzione alla prima riga di codice nei `NodeChildrenRequested` `CreateWebPartNodes` metodi e.

3. Premere il tasto **F5** per avviare il debug.

     Visual Studio installa l'estensione nell'estensione del nodo della raccolta di parti%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web per il Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliere **Visualizza** Esplora server dalla barra dei menu  >  **Server Explorer**.

2. Se il sito di SharePoint che si desidera utilizzare per il test non viene visualizzato nel nodo connessioni di **SharePoint** in **Esplora server**, attenersi alla procedura seguente:

    1. In **Esplora server** aprire il menu di scelta rapida per le **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.

    2. Nella finestra di dialogo **Aggiungi connessione SharePoint** immettere l'URL del sito di SharePoint a cui si desidera connettersi, quindi scegliere il pulsante **OK** .

         Per specificare il sito di SharePoint nel computer di sviluppo, immettere **http://localhost** .

3. Espandere il nodo connessione sito (che consente di visualizzare l'URL del sito), quindi espandere un nodo del sito figlio, ad esempio il **sito del team**.

4. Verificare che il codice nell'altra istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] si interrompa nel punto di interruzione impostato in precedenza nel `NodeChildrenRequested` metodo, quindi premere **F5** per continuare a eseguire il debug del progetto.

5. Nell'istanza sperimentale di Visual Studio verificare che nel nodo sito di livello superiore venga visualizzato un nuovo nodo denominato **raccolta web part** , quindi espandere il nodo **raccolta web part** .

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `CreateWebPartNodes` metodo, quindi premere il tasto **F5** per continuare a eseguire il debug del progetto.

7. Nell'istanza sperimentale di Visual Studio verificare che tutti i Web part nel sito connesso siano visualizzati nel nodo **raccolta Web Part** **Esplora server**.

8. In **Esplora server** aprire il menu di scelta rapida per una delle web part, quindi scegliere **Proprietà**.

9. Nell'istanza di di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cui si sta eseguendo il debug, verificare che i dettagli relativi alla web part siano visualizzati nella finestra **Proprietà** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Al termine del test dell'estensione, disinstallare l'estensione da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , nella barra dei menu scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere estensione del **nodo raccolta web part per Esplora server**, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione, quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

4. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione WebPartNode).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: chiamare il modello a oggetti del client di SharePoint in un'estensione Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di un'altra immagine &#40;editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)