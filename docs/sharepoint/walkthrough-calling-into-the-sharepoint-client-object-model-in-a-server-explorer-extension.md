---
title: 'Esplora server: Estensione del nodo Connessioni di SharePoint'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf3d39a8a06a59ed337c0d847bb92875f0f68558
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824156"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procedura dettagliata: La chiamata nel modello a oggetti client SharePoint in un'estensione di Esplora Server
  Questa procedura dettagliata illustra come chiamare il modello a oggetti client SharePoint da un'estensione per il **connessioni di SharePoint** nodo **Esplora Server**. Per altre informazioni su come usare il modello a oggetti client SharePoint, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensione che consente di estendere il **connessioni di SharePoint** nodo del **Esplora Server** nei modi seguenti:

  - L'estensione aggiunge un **raccolta Web Part** nodo in ogni nodo nel sito di SharePoint **Esplora Server**. Il nuovo nodo contiene i nodi figlio che rappresentano ogni Web Part nella raccolta di Web Part sul sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di Web Part. Questo nuovo tipo di nodo è la base per i nodi figlio sotto la nuova **raccolta Web Part** nodo. Il nuovo tipo di nodo di Web Part Visualizza le informazioni nel **proprietà** finestra sulla Web Part che rappresenta il nodo.

- Creazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'estensione.

- Il debug e l'estensione per il testing.

> [!NOTE]
> L'estensione create in questa procedura dettagliata è simile all'estensione che crea in [procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Tale procedura dettagliata Usa il modello a oggetti SharePoint server, ma questa procedura dettagliata esegue le stesse attività usando il modello a oggetti client.

## <a name="prerequisites"></a>Prerequisiti
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:

- Usando il modello a oggetti client SharePoint. Per altre informazioni, vedere [modello a oggetti Client gestito](http://go.microsoft.com/fwlink/?LinkId=177797).

- Web part in SharePoint. Per altre informazioni, vedere [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Un progetto VSIX per creare il pacchetto VSIX per la distribuzione di **Esplora Server** estensione.

- Un progetto di libreria di classi che implementa il **Esplora Server** estensione.

  Avviare la procedura dettagliata mediante la creazione di progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel **nuovo progetto** finestra di dialogo, espandere il **Visual c#** oppure **Visual Basic** nodi e quindi scegliere **estendibilità**.

    > [!NOTE]
    > Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.

     Le estensioni di strumenti di SharePoint richiedono funzionalità in questa versione di .NET Framework.

5. Scegliere il **progetto VSIX** modello.

6. Nel **nome** , digitare **WebPartNode**, quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **WebPartNode** progetto al **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo, espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere **Windows**.

3. Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.

4. Nell'elenco dei modelli di progetto, scegliere **libreria di classi**.

5. Nel **Name** casella, immettere **risorse**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **risorse** progetto alla soluzione e apre il file di codice predefinita Class1.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto e sarà necessario aggiornare lo spazio dei nomi predefinito.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel **risorse** del progetto, aggiungere due file di codice denominati SiteNodeExtension e WebPartNodeTypeProvider.

2. Aprire il menu di scelta rapida risorse per il progetto e quindi scegliere **Aggiungi riferimento**.

3. Nel **gestione riferimenti - risorse** finestra di dialogo scegliere la **Framework** nodo e quindi selezionare le caselle di controllo per il Composition e System assembly.

4. Scegliere il **Extensions** nodo, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere il **OK** pulsante:

    - Microsoft.SharePoint.Client

    - Microsoft.SharePoint.Client.Runtime

    - Microsoft.VisualStudio.SharePoint

5. Aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **proprietà**.

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nel **spazio dei nomi predefinito** finestra (c#) o **spazio dei nomi radice** (Visual Basic), immettere **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creazione di icone per i nuovi nodi
 Creare due icone per il **Esplora Server** estensione: un'icona per il nuovo **raccolta Web Part** nodo e un'altra icona per ogni nodo della Web Part figlio sotto il **raccolta Web Part** nodo. Più avanti in questa procedura dettagliata, si scriverà il codice che associa tali icone con i nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare le icone per i nodi

1. Nel **creazione progetti** risorse per il progetto, scegliere il **risorse** scheda.

2. Scegliere il collegamento **questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**

     Visual Studio crea un file di risorse e lo apre nella finestra di progettazione.

3. Nella parte superiore della finestra di progettazione, scegliere la freccia in sulla **Aggiungi risorsa** dal menu di comando e quindi scegliere **Aggiungi nuova icona**.

4. Immettere **WebPartsNode** per l'icona del nuovo nome e quindi scegliere il **Add** pulsante.

     Viene aperta la nuova icona nel **Editor di immagini**.

5. Modificare la versione di 16x16 dell'icona in modo che includa una progettazione che è possibile riconoscere facilmente.

6. Aprire il menu di scelta rapida per la versione a 32 x 32 dell'icona e quindi scegliere **eliminare tipo di immagine**.

7. Ripetere i passaggi da 3 a 7 per aggiungere una seconda icona Risorse del progetto e denominare questa icona **WebPart**.

8. Nella **Esplora soluzioni**, nella **risorse** cartella per il **risorse** del progetto, scegliere *WebPartNodeExtension*.

9. Nel **delle proprietà** finestra, aprire il **azione di compilazione** elenco e quindi scegliere **risorsa incorporata**.

10. Ripetere gli ultimi due passaggi per la *WebPart*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo di raccolta web part a Esplora Server
 Creare una classe che aggiunge la nuova **raccolta Web Part** nodo per ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera estendere il comportamento di un nodo esistente nel **Esplora Server**, ad esempio l'aggiunta di un nuovo nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo di raccolta web part a Esplora Server

1. Incollare il codice seguente nel **SiteNodeExtension** file di codice per il **risorse** progetto.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto avrà alcuni errori di compilazione. Questi errori scompare quando si aggiunge codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web Part. Visual Studio Usa questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il **raccolta Web Part** nodo. Ognuno di questi nodi figlio rappresenta una singola parte Web nel sito di SharePoint.

 Per definire il nuovo tipo di nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di nodo **Esplora Server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo di web part

1. Incollare il codice seguente nel **WebPartNodeTypeProvider** file di codice per il **risorse** progetto.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il **raccolta Web Part** nodo ora è incluso nel progetto. Compilare il **risorse** progetto per assicurarsi che venga compilata senza errori.

#### <a name="to-build-the-project"></a>Per compilare il progetto

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **compilare**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest incluso nel progetto. Creare quindi il pacchetto VSIX per la compilazione della soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. Nelle **Esplora soluzioni**, nella **WebPartNode** progetto aprire **vsixmanifest** file nell'editor del manifesto.

     Il file vsixmanifest costituisce la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nel **Product Name** casella, immettere **nodo di raccolta Web Part di Esplora Server**.

3. Nel **Author** casella, immettere **Contoso**.

4. Nel **Description** casella, immettere **aggiunge un nodo di raccolta Web Part personalizzato al nodo Connessioni di SharePoint in Esplora Server**.

5. Nel **asset** della scheda dell'editor, scegliere il **New** pulsante.

6. Nel **Aggiungi nuovo Asset** nella finestra di dialogo il **tipo** casella di riepilogo **MEFComponent**.

    > [!NOTE]
    > Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

8. Nel **progetto** scegliere **risorse**, quindi scegliere il **OK** pulsante.

9. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

10. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contiene ora il file WebPartNode.

     Per impostazione predefinita, la cartella di output di compilazione è di... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 Ora si è pronti per testare le nuove **raccolta Web Part** nodo **Esplora Server**. Innanzitutto, avviare il debug del progetto di estensione in un'istanza sperimentale di Visual Studio. Quindi usare le nuove **Web part** nodo nell'istanza sperimentale di Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire il **WebPartNode** soluzione.

2. Nel progetto di risorse, aprire il **SiteNodeExtension** file di codice e quindi aggiungere un punto di interruzione per le prime righe di codice nelle `NodeChildrenRequested` e `CreateWebPartNodes` metodi.

3. Scegliere il **F5** chiave per avviare il debug.

     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery nodo Extension for Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **View** > **Esplora Server**.

2. Verificare che il sito di SharePoint che si desidera usare per il test venga visualizzato sotto il **connessioni di SharePoint** nodo **Esplora Server**. Se non è elencato, seguire questa procedura:

    1. Aprire il menu di scelta rapida **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.

    2. Nel **Aggiungi connessione SharePoint** finestra di dialogo immettere l'URL per il sito di SharePoint a cui si desidera connettersi, quindi scegliere il **OK** pulsante.

         Per specificare il sito di SharePoint nel computer di sviluppo, digitare **http://localhost** .

3. Espandere il nodo di connessione del sito, che visualizza l'URL del sito, e quindi espandere un nodo del sito figlio (ad esempio, **sito del Team**).

4. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nella `NodeChildrenRequested` metodo e quindi scegliere il **F5** un tasto per continuare il debug del progetto.

5. Nell'istanza sperimentale di Visual Studio, espandere la **raccolta Web Part** nodo, visualizzata sotto il nodo di sito di livello superiore.

6. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nella `CreateWebPartNodes` metodo e quindi scegliere il **F5** un tasto per continuare il debug del progetto.

7. Nell'istanza sperimentale di Visual Studio, verificare che tutte le Web part sul sito connesso appaiano sotto le **raccolta Web Part** nodo **Esplora Server**.

8. Aprire il menu di scelta rapida per una Web Part e quindi scegliere **proprietà**.

9. Nel **proprietà** finestra, verificare che siano visualizzati i dettagli sulla Web Part.

10. Nelle **Esplora Server**, aprire il menu di scelta rapida per la stessa di Web Part e quindi scegliere **Visualizza un messaggio**.

     Nella finestra di messaggio che viene visualizzato, scegliere il **OK** pulsante.

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Dopo aver completato l'estensione per il testing, disinstallarlo da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni, scegliere **nodo di raccolta Web Part di Esplora Server**, quindi scegliere il **Disinstalla** pulsante.

3. Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante.

4. Scegliere il **Riavvia ora** pulsante per completare la disinstallazione.

     Inoltre viene disinstallata l'elemento del progetto.

5. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta).

## <a name="see-also"></a>Vedere anche
- [Chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o un'altra immagine &#40;Image Editor for Icons&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
