---
title: 'Esplora server: Estensione del nodo SharePoint connessioni di rete'
titleSuffix: ''
description: In questa procedura dettagliata viene illustrato come chiamare il modello SharePoint a oggetti client da un'estensione per il nodo connessioni SharePoint in Esplora server.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: cf618a3fa237035ead1540a64bc772d325954ff4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156110"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procedura dettagliata: Chiamata al modello SharePoint a oggetti client in un'Esplora server predefinita
  Questa procedura dettagliata illustra come chiamare il SharePoint a oggetti client da un'estensione per **il nodo** connessioni SharePoint in **Esplora server**. Per altre informazioni su come usare il modello SharePoint a oggetti client, vedere Chiamare i [modelli SharePoint a oggetti.](../sharepoint/calling-into-the-sharepoint-object-models.md)

 In questa procedura dettagliata vengono descritte le attività seguenti:

- La creazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di un'estensione **che estende SharePoint nodo Connessioni** di **Esplora server** nei modi seguenti:

  - L'estensione aggiunge **un nodo Raccolta web** part in ogni SharePoint del sito in **Esplora server**. Questo nuovo nodo contiene nodi figlio che rappresentano ogni web part nella raccolta di web part nel sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di web part. Questo nuovo tipo di nodo è la base per i nodi figlio nel nuovo **nodo Raccolta web** part. Il nuovo tipo di nodo Web part visualizza informazioni **nella finestra Proprietà** relative alla web part che il nodo rappresenta.

- Compilazione di un pacchetto vsix (Visual Studio Extension) per distribuire l'estensione.

- Debug e test dell'estensione.

> [!NOTE]
> L'estensione creata in questa procedura dettagliata è simile all'estensione creata in Procedura [dettagliata:](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)Estendere Esplora server per visualizzare le web part . Questa procedura dettagliata usa il SharePoint a oggetti del server, ma questa procedura dettagliata consente di eseguire le stesse attività usando il modello a oggetti client.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- SDK Visual Studio. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Utilizzo del SharePoint a oggetti client. Per altre informazioni, vedere [Modello a oggetti del client gestito.](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14))

- Web part in SharePoint. Per altre informazioni, vedere [panoramica Web part.](/previous-versions/office/ms432401(v=office.14))

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire **l'Esplora server** predefinita.

- Progetto di libreria di classi che implementa **l'Esplora server** predefinita.

  Iniziare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

3. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere **Estendibilità**.

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

     SharePoint estensioni dello strumento richiedono funzionalità in questa versione del .NET Framework.

5. Scegliere il **modello di Project VSIX.**

6. Nella casella **Nome** digitare **WebPartNode** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto WebPartNode** **a Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi **scegliere Windows**.

3. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **Libreria di classi.**

5. Nella casella **Nome** immettere **WebPartNodeExtension** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto WebPartNodeExtension** alla soluzione e apre il file di codice Class1 predefinito.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere file di codice e riferimenti all'assembly al progetto ed è necessario aggiornare lo spazio dei nomi predefinito.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto **WebPartNodeExtension** aggiungere due file di codice denominati SiteNodeExtension e WebPartNodeTypeProvider.

2. Aprire il menu di scelta rapida per il progetto WebPartNodeExtension e quindi scegliere **Aggiungi riferimento.**

3. Nella finestra di dialogo Gestione riferimenti **- WebPartNodeExtension** scegliere il nodo **Framework** e quindi selezionare le caselle di controllo per System.ComponentModel.Composition e System. Windows. Assembly di form.

4. Scegliere il **nodo** Estensioni, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere **il pulsante OK:**

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client.Runtime

    - Microsoft.VisualStudio. SharePoint

5. Aprire il menu di scelta rapida **per il progetto WebPartNodeExtension** e quindi scegliere **Proprietà.**

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nella casella **Spazio dei** nomi  predefinito (C#) o Spazio dei nomi radice (Visual Basic) immettere **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creare icone per i nuovi nodi
 Creare due icone per **l'Esplora server** web part: un'icona per il nuovo nodo Raccolta **web part** e un'altra icona per ogni nodo web part figlio nel nodo Raccolta **web** part. Più avanti in questa procedura dettagliata si scriverà il codice che associa queste icone ai nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare icone per i nodi

1. Nella finestra **Project per** il progetto WebPartNodeExtension scegliere la **scheda** Risorse.

2. Scegliere il collegamento **Questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**

     Visual Studio crea un file di risorse e lo apre nella finestra di progettazione.

3. Nella parte superiore della finestra di progettazione scegliere la freccia nel comando di menu **Aggiungi** risorsa e quindi scegliere **Aggiungi nuova icona**.

4. Immettere **WebPartsNode** come nome della nuova icona e quindi scegliere **il pulsante** Aggiungi.

     La nuova icona si apre **nell'editor di immagini.**

5. Modificare la versione 16x16 dell'icona in modo che abbia una progettazione facilmente riconoscibile.

6. Aprire il menu di scelta rapida per la versione 32x32 dell'icona e quindi scegliere **Elimina tipo di immagine.**

7. Ripetere i passaggi da 3 a 7 per aggiungere una seconda icona alle risorse del progetto e assegnare a questa icona il nome **WebPart**.

8. In **Esplora soluzioni**, nella **cartella Risorse** per il progetto **WebPartNodeExtension** scegliere *WebPartsNode.ico.*

9. Nella finestra **Proprietà** aprire l'elenco **Azione di** compilazione e quindi scegliere **Risorsa incorporata.**

10. Ripetere gli ultimi due passaggi per *WebPart.ico.*

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo della raccolta di web part Esplora server
 Creare una classe che aggiunge il nuovo **nodo Raccolta web part** a ogni SharePoint del sito. Per aggiungere il nuovo nodo, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio aggiungendo un nuovo nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo della raccolta di web part Esplora server

1. Incollare il codice seguente nel file di codice **SiteNodeExtension** per **il progetto WebPartNodeExtension.**

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione. Questi errori verranno visualizzati quando si aggiungerà codice nei passaggi successivi.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una web part. Visual Studio usa questo nuovo tipo di nodo per visualizzare i nodi figlio nel **nodo Raccolta web** part. Ognuno di questi nodi figlio rappresenta una singola web part nel SharePoint sito.

 Per definire il nuovo tipo di nodo, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di nodo in **Esplora server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo web part

1. Incollare il codice seguente nel file **di codice WebPartNodeTypeProvider** per **il progetto WebPartNodeExtension.**

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il **nodo Raccolta web part** si trova ora nel progetto. Compilare **il progetto WebPartNodeExtension** per assicurarsi che venga compilato senza errori.

#### <a name="to-build-the-project"></a>Per compilare il progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto WebPartNodeExtension** e quindi scegliere **Compila.**

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare prima di tutto il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. In **Esplora soluzioni**, nel **progetto WebPartNode** aprire il file **source.extension.vsixmanifest** nell'editor manifesto.

     Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere **Web Part Gallery Node (Nodo raccolta** web part) per Esplora server .

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere Aggiunge un nodo Raccolta **web part personalizzato** al nodo Connessioni SharePoint in Esplora server .

5. Nella **scheda Asset dell'editor** scegliere il **pulsante** Nuovo.

6. **Nell'elenco Tipo** della finestra di dialogo Aggiungi nuovo **asset** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

7. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

8. **Nell'Project,** scegliere **WebPartNodeExtension** e quindi scegliere **il pulsante OK.**

9. Nella barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che la  >  soluzione venga compilata senza errori.

10. Assicurarsi che la cartella dell'output di compilazione per il progetto WebPartNode contenga ora il file WebPartNode.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 A questo punto è possibile testare il nuovo **nodo Raccolta web part** in **Esplora server**. Per prima cosa, iniziare a eseguire il debug del progetto di estensione in un'istanza sperimentale di Visual Studio. Usare quindi il nuovo **nodo Web part** nell'istanza sperimentale di Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la **soluzione WebPartNode.**

2. Nel progetto WebPartNodeExtension aprire il file di codice **SiteNodeExtension** e quindi aggiungere un punto di interruzione alle prime righe di codice nei `NodeChildrenRequested` metodi e `CreateWebPartNodes` .

3. Premere **F5 per** avviare il debug.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery Node Extension per Esplora server\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento di progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere  >  **Visualizza Esplora server**.

2. Verificare che il SharePoint da usare per il test  sia visualizzato nel nodo Connessioni SharePoint in **Esplora server**. Se non è elencato, seguire questa procedura:

    1. Aprire il menu di scelta **rapida SharePoint connessioni** e quindi scegliere Aggiungi **connessione.**

    2. Nella finestra **di dialogo Aggiungi** SharePoint connessione immettere l'URL per il sito di SharePoint a cui connettersi e quindi scegliere il pulsante **OK.**

         Per specificare il SharePoint nel computer di sviluppo, digitare **http://localhost** .

3. Espandere il nodo della connessione del sito (che visualizza l'URL del sito) e quindi espandere un nodo del sito figlio, ad esempio **Sito del team.**

4. Verificare che il codice nell'altra istanza di Visual Studio si arresti in corrispondenza del punto di interruzione impostato in precedenza nel metodo e quindi premere F5 per continuare a eseguire il `NodeChildrenRequested` debug del progetto. 

5. Nell'istanza sperimentale di Visual Studio espandere il nodo **Raccolta web part** visualizzato sotto il nodo del sito di livello superiore.

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti in corrispondenza del punto di interruzione impostato in precedenza nel metodo e quindi premere F5 per continuare a eseguire il `CreateWebPartNodes` debug del progetto. 

7. Nell'istanza sperimentale di Visual Studio verificare che tutti i Web part nel sito connesso siano visualizzati sotto il nodo Raccolta **web part** **in Esplora server**.

8. Aprire il menu di scelta rapida per una web part e quindi scegliere **Proprietà.**

9. Nella finestra **Proprietà** verificare che vengano visualizzati i dettagli sulla web part.

10. In **Esplora server** aprire il menu di scelta rapida per la stessa web part e quindi scegliere **Visualizza messaggio.**

     Nella finestra di messaggio visualizzata scegliere il **pulsante OK.**

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Dopo aver completato il test dell'estensione, disinstallarla da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **Strumenti**  >  **Estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Nodo raccolta web part per Esplora server** e quindi scegliere il pulsante **Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere il **pulsante** Sì.

4. Scegliere il **pulsante Riavvia** ora per completare la disinstallazione.

     Viene disinstallato anche l'elemento di progetto.

5. Chiudere entrambe le istanze Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione WebPartNode).

## <a name="see-also"></a>Vedi anche
- [Chiamare nei modelli SharePoint oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di un'altra immagine &#40;editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)