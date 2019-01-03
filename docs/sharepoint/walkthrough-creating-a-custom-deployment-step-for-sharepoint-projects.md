---
title: 'Procedura dettagliata: Creazione di un passaggio di distribuzione personalizzato per progetti SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e12f9d8b93b429b0ecdc433eef59809f2ca4c61d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891576"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint
  Quando si distribuisce un progetto SharePoint, Visual Studio esegue una serie di passaggi di distribuzione in un ordine specifico. Visual Studio include numerosi passaggi di distribuzione predefinite, ma è anche possibile creare una propria.  
  
 In questa procedura dettagliata, si creerà un passaggio di distribuzione personalizzato per aggiornare soluzioni in un server che esegue SharePoint. Visual Studio include fasi di distribuzione predefinite per numerose attività, tale ritrazione o aggiunta di soluzioni, ma non include un passaggio di distribuzione per l'aggiornamento delle soluzioni. Per impostazione predefinita, quando si distribuisce una soluzione di SharePoint, Visual Studio prima di tutto si ritrae la soluzione (se è già distribuita) e quindi ridistribuisce l'intera soluzione. Per altre informazioni sui passaggi di distribuzione predefinite, vedere [distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che esegue due attività principali:  
  
    -   L'estensione di definire un passaggio di distribuzione personalizzato per aggiornare soluzioni SharePoint.  
  
    -   L'estensione crea un'estensione di progetto che definisce una nuova configurazione di distribuzione, ovvero una serie di passaggi di distribuzione che vengono eseguite per un determinato progetto. La nuova configurazione di distribuzione include il passaggio di distribuzione personalizzato e alcuni passaggi di distribuzione predefinite.  
  
-   Creare due comandi di SharePoint personalizzati che chiama l'assembly dell'estensione. I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensione per usare le API nel modello a oggetti server per SharePoint. Per altre informazioni, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Creazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire entrambi gli assiemi.  
  
-   Il nuovo passaggio di distribuzione di test.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
- Edizioni supportate di Windows, SharePoint e Visual Studio.
  
- Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:  
  
- Usando il modello a oggetti server per SharePoint. Per altre informazioni, vedere [usando il modello a oggetti lato Server SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- Soluzioni di SharePoint. Per altre informazioni, vedere [panoramica delle soluzioni](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
- Aggiornamento delle soluzioni di SharePoint. Per altre informazioni, vedere [l'aggiornamento di una soluzione](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.  
  
- Un progetto libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione .NET Framework 4.5.  
  
- Un progetto libreria di classi che definisce i comandi di SharePoint personalizzati. Questo progetto deve avere come destinazione .NET Framework 3.5.  
  
  Avviare la procedura dettagliata mediante la creazione di progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
5.  Scegliere il **progetto VSIX** modello, nome del progetto **UpgradeDeploymentStep**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **UpgradeDeploymentStep** progetto al **Esplora soluzioni**.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual c#** oppure **Visual Basic** nodi e quindi scegliere il **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **DeploymentStepExtension**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **DeploymentStepExtension** progetto alla soluzione e apre il file di codice predefinita Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Per creare il progetto di comando di SharePoint  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere **Visual c#** o **Visual Basic**, quindi scegliere il **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
     Visual Studio aggiunge il **SharePointCommands** progetto alla soluzione e apre il file di codice predefinita Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere codice per creare la fase di distribuzione personalizzato, è necessario aggiungere i file di codice e i riferimenti ad assembly, ed è necessario configurare i progetti.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Per configurare il progetto DeploymentStepExtension
  
1.  Nel **DeploymentStepExtension** del progetto, aggiungere due file di codice che includono i nomi seguenti:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Aprire il menu di scelta rapida del progetto DeploymentStepExtension e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **Framework** scheda, selezionare la casella di controllo per l'assembly Composition.  
  
4.  Nel **Extensions** scheda, selezionare la casella di controllo per l'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointCommands
  
1.  Nel **SharePointCommands** del progetto, aggiungere un file di codice denominato comandi.  
  
2.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida nel **SharePointCommands** nodo del progetto e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **estensioni** scheda, selezionare le caselle di controllo per gli assembly seguenti e quindi fare clic su Scegli le **OK** pulsante  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Definire la fase di distribuzione personalizzato
 Creare una classe che definisce il passaggio di distribuzione dell'aggiornamento. Per definire la fase di distribuzione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia. Implementare questa interfaccia ogni volta che si vuole definire un passaggio di distribuzione personalizzato.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Per definire la fase di distribuzione personalizzato  
  
1.  Nel **DeploymentStepExtension** del progetto, aprire il file di codice UpgradeStep e quindi incollare il codice seguente al suo interno.  
  
    > [!NOTE]  
    >  Dopo che si aggiunge questo codice, il progetto avrà alcuni errori di compilazione, ma scompariranno quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Creare una configurazione di distribuzione che include il passaggio di distribuzione personalizzato
 Creare un'estensione di progetto per la nuova configurazione di distribuzione, che include diversi passaggi di distribuzione predefinite e il nuovo passaggio di distribuzione dell'aggiornamento. Tramite la creazione di questa estensione, aiutare gli sviluppatori di SharePoint da usare il passaggio di distribuzione di aggiornamento nei progetti di SharePoint.  
  
 Per creare la configurazione della distribuzione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Implementare questa interfaccia ogni volta che si vuole creare un'estensione di progetto SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Per creare la configurazione della distribuzione  
  
1.  Nel **DeploymentStepExtension** del progetto, aprire il file di codice DeploymentConfigurationExtension e quindi incollare il codice seguente al suo interno.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi di SharePoint personalizzati
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti del server per SharePoint. Un unico comando determina se è già stata distribuita una soluzione; il comando consente di aggiornare una soluzione.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint  
  
1.  Nel **SharePointCommands** del progetto, aprire il file di codice i comandi e quindi incollare il codice seguente al suo interno.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto della procedura dettagliata, tutto il codice per il passaggio di distribuzione personalizzato e i comandi di SharePoint si trovano nei progetti. Compilarli per assicurarsi che si esegue la compilazione senza errori.  
  
#### <a name="to-build-the-projects"></a>Per compilare i progetti  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **DeploymentStepExtension** del progetto e quindi scegliere **compilare**.  
  
2.  Aprire il menu di scelta rapida per il **SharePointCommands** del progetto e quindi scegliere **compilazione**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest nel progetto VSIX. Creare quindi il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  Nella **Esplora soluzioni**, sotto il **UpgradeDeploymentStep** del progetto, aprire il menu di scelta rapida per il **vsixmanifest** file e quindi scegliere  **Apri**.  
  
     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest costituisce la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** casella, immettere **aggiornare il passaggio di distribuzione per progetti SharePoint**.  
  
3.  Nel **Author** casella, immettere **Contoso**.  
  
4.  Nel **Description** casella, immettere **offre una procedura di distribuzione di aggiornamento personalizzato che può essere usata in progetti SharePoint**.  
  
5.  Nel **asset** della scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** casella di riepilogo **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **DeploymentStepExtension**, quindi scegliere il **OK** pulsante.  
  
9. Nell'editor del manifesto, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
10. Nel **tipo** elenco, immettere **v4**.  
  
    > [!NOTE]  
    >  Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per altre informazioni, vedere [Asset Element (Schema di VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
12. Nel **progetto** scegliere **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
13. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
14. Assicurarsi che la cartella di output di compilazione per il progetto UpgradeDeploymentStep contiene ora il file UpgradeDeploymentStep.  
  
     Per impostazione predefinita, la cartella di output di compilazione è di... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Preparare il passaggio di distribuzione dell'aggiornamento di test
 Per testare il passaggio di distribuzione dell'aggiornamento, è necessario innanzitutto distribuire una soluzione di esempio per il sito di SharePoint. Avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio. Creare quindi una definizione di elenco e un'istanza di elenco da usare per testare la fase di distribuzione e quindi distribuirli nel sito di SharePoint. Successivamente, modificare la definizione e l'istanza di elenco e ridistribuirli per illustrare il modo in cui il processo di distribuzione predefinito sovrascrive le soluzioni nel sito di SharePoint.  
  
 Più avanti in questa procedura dettagliata si modificherà la definizione e l'istanza di elenco e quindi verrà eseguito l'aggiornamento li nel sito di SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione UpgradeDeploymentStep.  
  
2.  Nel progetto DeploymentStepExtension, aprire il file di codice UpgradeStep e quindi aggiungere un punto di interruzione per la prima riga del codice nel `CanExecute` e `Execute` metodi.  
  
3.  Avviare il debug scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.  
  
4.  Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade passaggio di distribuzione per SharePoint Projects\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà il passaggio di distribuzione di aggiornamento in questa istanza di Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Per creare un progetto SharePoint con una definizione di elenco e un'istanza di elenco  
  
1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.  
  
2. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** nodo o la **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3. Nella parte superiore della finestra di dialogo, verificare che **.NET Framework 3.5** visualizzato nell'elenco delle versioni di .NET Framework.  
  
    Per i progetti [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] necessaria questa versione di .NET Framework.  
  
4. Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**, denominare il progetto **EmployeesListDefinition**, quindi scegliere il **OK** pulsante.  
  
5. Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug.  
  
6. Sotto **qual è il livello di attendibilità per questa soluzione di SharePoint**, scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
   > [!NOTE]  
   >  Il passaggio di distribuzione di aggiornamento non supporta soluzioni create mediante sandbox.  
  
7. Scegliere il **fine** pulsante.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea il progetto EmployeesListDefinition.  
  
8. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition, scegliere **Add**, quindi scegliere **nuovo elemento**.  
  
9. Nel **Aggiungi nuovo elemento - EmployeesListDefinition** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
10. Scegliere il **elenco** modello di elemento, denominare l'elemento **elenco dipendenti**, quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata la personalizzazione guidata SharePoint  
  
11. Nel **scegliere le impostazioni dell'elenco** pagina, verificare le impostazioni seguenti e quindi scegliere il **fine** pulsante:  
  
    1. **Elenco di dipendenti** viene visualizzato nei **quale nome si desidera visualizzare per l'elenco?** casella.  
  
    2. Il **creare un elenco personalizzabile basato su:** viene scelto il pulsante di opzione.  
  
    3. **Predefinito (vuoto)** viene scelto nel **creare un elenco personalizzabile basato su:** elenco.  
  
       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea l'elemento dell'elenco di dipendenti con una colonna del titolo e una singola istanza vuota e verrà visualizzata la finestra di progettazione di elenco.  
  
12. Nella finestra di progettazione di elenco nel **colonne** scheda, scegliere il **digitare un nome di colonna nuovo o esistente** riga e quindi aggiungere le colonne seguenti nel **nome visualizzato colonna** elenco:  
  
    1.  Nome  
  
    2.  Company  
  
    3.  Telefono ufficio  
  
    4.  Messaggio di posta elettronica  
  
13. Salvare tutti i file e quindi chiudere la finestra di progettazione di elenco.  
  
14. In **Esplora soluzioni**, espandere il **elenco dipendenti** nodo, quindi espandere il **istanza elenco dipendenti** nodo figlio.  
  
15. Nel *Elements* file, sostituire il valore predefinito in questo file XML con il codice XML seguente. Questo codice XML viene modificato il nome dell'elenco **dipendenti** e aggiunge le informazioni per un dipendente che ha chiamato Jim Hance.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Salvare e chiudere il *Elements* file.  
  
17. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition e quindi scegliere **aperto** oppure **proprietà**.  
  
     Verrà visualizzata la finestra di progettazione le proprietà.  
  
18. Nel **SharePoint** scheda, deseleziona le **ritrazione automatica dopo il debug** casella di controllo e quindi salvare le proprietà.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Per distribuire la definizione e l'istanza di elenco  
  
1.  Nelle **Esplora soluzioni**, scegliere il **EmployeesListDefinition** nodo del progetto.  
  
2.  Nel **delle proprietà** finestra, assicurarsi che il **configurazione distribuzione attiva** viene impostata su **predefinito**.  
  
3.  Scegliere il **F5** chiave alternativa, sulla barra dei menu, scegliere **Debug** > **Avvia debug**.  
  
4.  Verificare che il progetto venga compilato correttamente, che consente di aprire il web browser al sito di SharePoint, che il **sono elencati** include il nuovo elemento nella barra Avvio veloce **Employees** elenco e che il  **I dipendenti** elenco include la voce per Jim Hance.  
  
5.  Chiudere il Web browser.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Per modificare la definizione e l'istanza di elenco e ridistribuirle  
  
1.  Nel progetto EmployeesListDefinition, aprire il *Elements. XML* file di un elemento figlio del **Employee List Instance** elemento del progetto.  
  
2.  Rimuovere il `Data` elemento e i relativi figli per rimuovere la voce per Jim Hance dall'elenco.  
  
     Al termine, il file deve contenere il codice XML seguente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Salvare e chiudere il *Elements* file.  
  
4.  Aprire il menu di scelta rapida per il **elenco di dipendenti** dell'elemento di progetto e quindi scegliere **Open** oppure **proprietà**.  
  
5.  Nella finestra di progettazione elenco, scegliere il **viste** scheda.  
  
6.  Nel **colonne selezionate** scegliere **allegati**e quindi scegliere il < chiave per spostare tale colonna per il **colonne disponibili** elenco.  
  
7.  Ripetere il passaggio precedente per spostare il **telefono dell'ufficio** colonna dalle **colonne selezionate** elenco per il **colonne disponibili** elenco.  
  
     Questa azione rimuove questi campi dalla visualizzazione predefinita della **dipendenti** elenco nel sito di SharePoint.  
  
8.  Avviare il debug scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.  
  
9. Verificare che il **conflitti di distribuzione** verrà visualizzata la finestra di dialogo.  
  
     Questa finestra di dialogo viene visualizzata quando si tenta di distribuire una soluzione (l'istanza di elenco) in un sito di SharePoint a cui tale soluzione è già stata distribuita. Questa finestra di dialogo non verrà visualizzato quando si esegue il passaggio di distribuzione dell'aggiornamento più avanti in questa procedura dettagliata.  
  
10. Nel **conflitti di distribuzione** finestra di dialogo scegliere la **Risolvi automaticamente** pulsante di opzione.  
  
     Visual Studio consente di eliminare l'istanza di elenco nel sito di SharePoint, distribuisce l'elemento dell'elenco nel progetto e quindi apre il sito di SharePoint.  
  
11. Nel **sono elencati** sezione della barra di avvio veloce scegliere il **dipendenti** elencare e verificare i dettagli seguenti:  
  
    -   Il **allegati** e **Phone Home** colonne non vengono visualizzati in questa visualizzazione dell'elenco.  
  
    -   L'elenco è vuoto. Quando è stato usato il **predefinite** configurazione della distribuzione per ridistribuire la soluzione, il **dipendenti** elenco è stato sostituito con il nuovo elenco vuoto nel progetto.  
  
## <a name="test-the-deployment-step"></a>Il passaggio di distribuzione di test
 A questo punto si è pronti testare il passaggio di distribuzione dell'aggiornamento. In primo luogo, aggiungere un elemento per l'istanza di elenco in SharePoint. Modificare la definizione di elenco e un'istanza di elenco, l'aggiornamento nel sito di SharePoint e verificare che il passaggio di distribuzione di aggiornamento non sovrascriva il nuovo elemento.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Per aggiungere manualmente un elemento all'elenco  
  
1.  Nella barra multifunzione nel sito di SharePoint, sotto il **strumenti elenco** scheda, scegliere il **elementi** scheda.  
  
2.  Nel **New** gruppo, scegliere **nuovo elemento**.  
  
     In alternativa, è possibile scegliere il **Aggiungi nuovo elemento** collegamento nell'elenco di elementi di se stesso.  
  
3.  Nel **dipendenti - nuovo elemento** finestra, nelle **titolo** immettere **responsabile strutture**.  
  
4.  Nel **First Name** casella, immettere **Andy**.  
  
5.  Nel **società** , digitare **Contoso**.  
  
6.  Scegliere il **salvare** pulsante, verificare che il nuovo elemento viene visualizzato nell'elenco e quindi chiudere il browser web.  
  
     Più avanti in questa procedura dettagliata, si userà questo elemento per verificare che il passaggio di distribuzione di aggiornamento non sovrascrive il contenuto di questo elenco.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Per testare il passaggio di distribuzione di aggiornamento  
  
1. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**, aprire il menu di scelta rapida per il **EmployeesListDefinition** nodo del progetto e quindi scegliere **proprietà**.  
  
    Verrà visualizzata la finestra di proprietà dell'Editor/finestra di progettazione.  
  
2. Nel **SharePoint** scheda, impostare il **configurazione distribuzione attiva** proprietà **aggiornamento**.  
  
    Questa configurazione di distribuzione personalizzato include il nuovo passaggio di distribuzione dell'aggiornamento.  
  
3. Aprire il menu di scelta rapida per il **elenco di dipendenti** dell'elemento di progetto e quindi scegliere **proprietà** oppure **Open**.  
  
    Verrà visualizzata la finestra di proprietà dell'Editor/finestra di progettazione.  
  
4. Nel **viste** scheda, scegliere il **posta elettronica** colonna e quindi scegliere il **<** per spostare la colonna dalla chiave il **colonneselezionate**elencati per il **colonne disponibili** elenco.  
  
    Questa azione rimuove questi campi dalla visualizzazione predefinita della **dipendenti** elenco nel sito di SharePoint.  
  
5. Avviare il debug scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.  
  
6. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nel `CanExecute` (metodo).  
  
7. Scegliere il **F5** chiave nuovo o, nella barra dei menu, scegliere **Debug** > **continua**.  
  
8. Verificare che il codice si interrompe al punto di interruzione impostato in precedenza nel `Execute` (metodo).  
  
9. Scegliere il **F5** chiave alternativa, sulla barra dei menu, scegliere **Debug** > **continua** un'ultima volta.  
  
     Il web browser si apre il sito di SharePoint.  
  
10. Nel **sono elencati** sezione nell'area avvio veloce, scegliere il **dipendenti** elencare e verificare i dettagli seguenti:  
  
    - L'elemento che sono stati aggiunti manualmente in precedenza (per Andy, la gestione di strutture) è ancora presente nell'elenco.  
  
    - Il **telefono dell'ufficio** e **indirizzo di posta elettronica** colonne non vengono visualizzati in questa visualizzazione dell'elenco.  
  
      Il **aggiornare** Modifica configurazione distribuzione esistente **dipendenti** istanza di elenco nel sito di SharePoint. Se è stato usato il **predefinito** configurazione della distribuzione anziché il **aggiornare** configurazione, si potrebbe verificarsi un conflitto di distribuzione. Visual Studio potrebbe risolvere il conflitto, sostituendo il **dipendenti** elenco e della voce di Andy, la gestione di strutture, verranno eliminati.  
  
## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il passaggio di distribuzione dell'aggiornamento di test, rimuovere l'istanza e la definizione di elenco dal sito di SharePoint e rimuovere l'estensione di passaggio di distribuzione da Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Per rimuovere l'istanza di elenco dal sito di SharePoint  
  
1.  Aprire il **dipendenti** elencare nel sito di SharePoint, se l'elenco non è già aperto.  
  
2.  Nella barra multifunzione nel sito di SharePoint, scegliere il **elenco degli strumenti** scheda e quindi scegliere il **elenco** scheda.  
  
3.  Nel **le impostazioni** gruppo, scegliere il **le impostazioni dell'elenco** elemento.  
  
4.  Sotto **autorizzazioni e gestione**, scegliere il **eliminare questo elenco** comando, scegliere **OK** per confermare che si desidera inviare l'elenco nel Cestino e quindi chiudere il web Browser.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Per rimuovere la definizione di elenco dal sito di SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **compilare** > **Retract**.  
  
     Visual Studio viene ritratta la definizione di elenco dal sito di SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni, scegliere **aggiornare il passaggio di distribuzione per progetti SharePoint**, quindi scegliere il **Disinstalla** comando.  
  
3.  Nella finestra di dialogo visualizzata, scegliere **Yes** per confermare che si desidera disinstallare l'estensione e quindi scegliere **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione UpgradeDeploymentStep è aperta).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
