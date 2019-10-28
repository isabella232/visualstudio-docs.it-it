---
title: 'Esplora server: estensione del nodo connessioni di SharePoint'
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
ms.openlocfilehash: 4a40c20b92dc221dfab566240d27912b2b7e58be
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984995"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procedura dettagliata: chiamata al modello a oggetti del client di SharePoint in un'estensione Esplora server
  In questa procedura dettagliata viene illustrato come chiamare il modello a oggetti del client di SharePoint da un'estensione del nodo **connessioni di SharePoint** in **Esplora server**. Per ulteriori informazioni sull'utilizzo del modello a oggetti del client di SharePoint, vedere la pagina relativa alla [chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che estende il nodo **connessioni di SharePoint** di **Esplora server** nei modi seguenti:

  - L'estensione aggiunge un nodo della **raccolta di Web part** in ogni nodo del sito di SharePoint in **Esplora server**. Questo nuovo nodo contiene i nodi figlio che rappresentano ogni Web part nella raccolta web part sul sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza della web part. Questo nuovo tipo di nodo è la base per i nodi figlio nel nuovo nodo della **raccolta di Web part** . Il nuovo tipo di nodo Web part Visualizza le informazioni nella finestra **Proprietà** relativa alla web part rappresentata dal nodo.

- Creazione di un pacchetto di estensione di Visual Studio (VSIX) per distribuire l'estensione.

- Debug e test dell'estensione.

> [!NOTE]
> L'estensione creata in questa procedura dettagliata è simile all'estensione creata in [procedura dettagliata: estendi Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). In questa procedura dettagliata viene utilizzato il modello a oggetti del server SharePoint, ma in questa procedura dettagliata vengono eseguite le stesse attività utilizzando il modello a oggetti del client.

## <a name="prerequisites"></a>Prerequisites
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Utilizzo del modello a oggetti del client di SharePoint. Per ulteriori informazioni, vedere [Managed Client Object Model](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Web part in SharePoint. Per ulteriori informazioni, vedere [Web part Overview](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione **Esplora server** .

- Progetto di libreria di classi che implementa l'estensione **Esplora server** .

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#**  o **Visual Basic** , quindi scegliere **Extensibility**.

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

     Le estensioni degli strumenti di SharePoint richiedono funzionalità in questa versione del .NET Framework.

5. Scegliere il modello di **progetto VSIX** .

6. Nella casella **nome** digitare **WebPartNode**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNode** al **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#**  o **Visual Basic** , quindi scegliere **Windows**.

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **libreria di classi**.

5. Nella casella **nome** immettere **WebPartNodeExtension**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **WebPartNodeExtension** alla soluzione e apre il file di codice Class1 predefinito.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere il codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto ed è necessario aggiornare lo spazio dei nomi predefinito.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto **WebPartNodeExtension** aggiungere due file di codice denominati SiteNodeExtension e WebPartNodeTypeProvider.

2. Aprire il menu di scelta rapida per il progetto WebPartNodeExtension, quindi scegliere **Aggiungi riferimento**.

3. Nella finestra di dialogo **Gestione riferimenti-WebPartNodeExtension** , scegliere il nodo **Framework** , quindi selezionare le caselle di controllo per gli assembly System. ComponentModel. Composition e System. Windows. Forms.

4. Scegliere il nodo **estensioni** , selezionare la casella di controllo per ognuno degli assembly seguenti, quindi scegliere il pulsante **OK** :

    - Microsoft. SharePoint. client

    - Microsoft. SharePoint. client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. Aprire il menu di scelta rapida per il progetto **WebPartNodeExtension** , quindi scegliere **Proprietà**.

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nella casella **spazio dei nomi predefinito** (C#) o nella casella **spazio dei nomi radice** (Visual Basic) immettere **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creare icone per i nuovi nodi
 Creare due icone per l'estensione **Esplora server** : un'icona per il nuovo nodo **raccolta web part** e un'altra icona per ogni nodo Web part figlio sotto il nodo **raccolta web part** . Più avanti in questa procedura dettagliata verrà scritto il codice che associa queste icone ai nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare icone per i nodi

1. In **Progettazione progetti** per il progetto WebPartNodeExtension scegliere la scheda **risorse** .

2. Scegliere il collegamento il **progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**

     Visual Studio crea un file di risorse e lo apre nella finestra di progettazione.

3. Nella parte superiore della finestra di progettazione scegliere la freccia del comando di menu **Aggiungi risorsa** , quindi scegliere **Aggiungi nuova icona**.

4. Immettere **WebPartsNode** per il nuovo nome dell'icona, quindi scegliere il pulsante **Aggiungi** .

     La nuova icona verrà aperta nell' **editor di immagini**.

5. Modificare la versione di 16x16 dell'icona in modo che disponga di una progettazione che è possibile riconoscere facilmente.

6. Aprire il menu di scelta rapida per la versione 32x32 dell'icona, quindi scegliere **Elimina tipo di immagine**.

7. Ripetere i passaggi da 3 a 7 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **WebPart**.

8. In **Esplora soluzioni**, nella cartella **risorse** del progetto **WebPartNodeExtension** , scegliere *WebPartsNode. ico*.

9. Nella finestra **Proprietà** aprire l'elenco **azione di compilazione** , quindi scegliere **risorsa incorporata**.

10. Ripetere gli ultimi due passaggi per *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo della raccolta web part alla Esplora server
 Creare una classe che aggiunga il nuovo nodo della **raccolta di Web part** a ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>. Implementare questa interfaccia quando si desidera estendere il comportamento di un nodo esistente in **Esplora server**, ad esempio l'aggiunta di un nuovo nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo della raccolta web part a Esplora server

1. Incollare il codice seguente nel file di codice **SiteNodeExtension** per il progetto **WebPartNodeExtension** .

    > [!NOTE]
    > Una volta aggiunto questo codice, il progetto avrà alcuni errori di compilazione. Questi errori si verificano quando si aggiunge codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una Web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web part. Visual Studio usa questo nuovo tipo di nodo per visualizzare i nodi figlio nel nodo **raccolta web part** . Ognuno di questi nodi figlio rappresenta una singola Web part nel sito di SharePoint.

 Per definire il nuovo tipo di nodo, la classe implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>. Implementare questa interfaccia quando si desidera definire un nuovo tipo di nodo in **Esplora server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo Web part

1. Incollare il codice seguente nel file di codice **WebPartNodeTypeProvider** per il progetto **WebPartNodeExtension** .

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il nodo della **raccolta web part** è ora presente nel progetto. Compilare il progetto **WebPartNodeExtension** per assicurarsi che venga compilato senza errori.

#### <a name="to-build-the-project"></a>Per compilare il progetto

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **WebPartNodeExtension** , quindi scegliere **Compila**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest incluso nel progetto. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto **WebPartNode** , aprire il file **source. Extension. vsixmanifest** nell'editor manifesto.

     Il file source. Extension. vsixmanifest è la base per il file Extension. vsixmanifest che tutti i pacchetti VSIX richiedono. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nella casella **nome prodotto** , immettere **nodo Raccolta Web part per Esplora server**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **aggiungere un nodo della raccolta web part personalizzato al nodo connessioni di SharePoint in Esplora server**.

5. Nella scheda **Asset** dell'Editor scegliere il pulsante **nuovo** .

6. Nella finestra di dialogo **Aggiungi nuovo asset** selezionare **Microsoft. VisualStudio. MefComponent**nell'elenco **tipo** .

    > [!NOTE]
    > Questo valore corrisponde all'elemento `MefComponent` nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** scegliere **WebPartNodeExtension**, quindi scegliere il pulsante **OK** .

9. Sulla barra dei **menu scegliere compila** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

10. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contenga ora il file WebPartNode. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 A questo punto si è pronti per testare il nuovo nodo della **raccolta web part** in **Esplora server**. Per prima cosa, iniziare a eseguire il debug del progetto di estensione in un'istanza sperimentale di Visual Studio. Usare quindi il nuovo nodo **Web part** nell'istanza sperimentale di Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione **WebPartNode** .

2. Nel progetto WebPartNodeExtension aprire il file di codice **SiteNodeExtension** e quindi aggiungere un punto di interruzione alla prima riga di codice nei metodi `NodeChildrenRequested` e `CreateWebPartNodes`.

3. Premere il tasto **F5** per avviare il debug.

     Visual Studio installa l'estensione nell'estensione del nodo della raccolta di parti%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web per il Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **visualizza** > **Esplora server**.

2. Verificare che il sito di SharePoint che si desidera utilizzare per il test venga visualizzato sotto il nodo **connessioni di SharePoint** in **Esplora server**. Se non è elencato, attenersi alla procedura seguente:

    1. Aprire il menu di scelta rapida per le **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.

    2. Nella finestra di dialogo **Aggiungi connessione SharePoint** immettere l'URL del sito di SharePoint a cui si desidera connettersi, quindi scegliere il pulsante **OK** .

         Per specificare il sito di SharePoint nel computer di sviluppo, digitare **http://localhost** .

3. Espandere il nodo connessione sito (che consente di visualizzare l'URL del sito), quindi espandere un nodo del sito figlio, ad esempio il **sito del team**.

4. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel metodo `NodeChildrenRequested`, quindi premere il tasto **F5** per continuare a eseguire il debug del progetto.

5. Nell'istanza sperimentale di Visual Studio espandere il nodo **raccolta web part** , che viene visualizzato sotto il nodo sito di livello superiore.

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel metodo `CreateWebPartNodes`, quindi premere il tasto **F5** per continuare a eseguire il debug del progetto.

7. Nell'istanza sperimentale di Visual Studio verificare che tutti i Web part nel sito connesso siano visualizzati nel nodo **raccolta Web Part** **Esplora server**.

8. Aprire il menu di scelta rapida per una Web part, quindi scegliere **Proprietà**.

9. Nella finestra **Proprietà** verificare che vengano visualizzati i dettagli relativi alla web part.

10. In **Esplora server**aprire il menu di scelta rapida per la stessa Web part, quindi scegliere **Visualizza messaggio**.

     Nella finestra di messaggio visualizzata scegliere il pulsante **OK** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Al termine del test dell'estensione, disinstallarla da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere **nodo raccolta web part per Esplora server**, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** .

4. Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

     Viene inoltre disinstallato l'elemento del progetto.

5. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione WebPartNode).

## <a name="see-also"></a>Vedere anche
- [Chiamare nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di &#40;un altro editor di immagini immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
