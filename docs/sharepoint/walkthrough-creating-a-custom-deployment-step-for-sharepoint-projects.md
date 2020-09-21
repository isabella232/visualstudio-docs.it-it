---
title: Creazione di un passaggio di distribuzione personalizzato per i progetti SharePoint
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b739db2755336958492a0aa67c9d5f0809f74bb
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740019"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint
  Quando si distribuisce un progetto SharePoint, Visual Studio esegue una serie di passaggi di distribuzione in un ordine specifico. Visual Studio include molti passaggi di distribuzione incorporati, ma è anche possibile crearne di personalizzati.

 In questa procedura dettagliata verrà creato un passaggio di distribuzione personalizzato per aggiornare le soluzioni in un server in cui è in esecuzione SharePoint. Visual Studio include passaggi di distribuzione incorporati per molte attività, ad esempio la ritrazione o l'aggiunta di soluzioni, ma non include una fase di distribuzione per l'aggiornamento delle soluzioni. Per impostazione predefinita, quando si distribuisce una soluzione SharePoint, Visual Studio prima ritira la soluzione, se è già stata distribuita, e quindi ridistribuisce l'intera soluzione. Per ulteriori informazioni sui passaggi di distribuzione incorporati, vedere [distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che esegue due attività principali:

  - L'estensione definisce un passaggio di distribuzione personalizzato per aggiornare le soluzioni SharePoint.

  - L'estensione crea un'estensione di progetto che definisce una nuova configurazione di distribuzione, ovvero un set di passaggi di distribuzione eseguiti per un determinato progetto. La nuova configurazione di distribuzione include il passaggio di distribuzione personalizzato e diversi passaggi di distribuzione incorporati.

- Creare due comandi di SharePoint personalizzati chiamati dall'assembly di estensione. I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensione per utilizzare le API nel modello a oggetti del server per SharePoint. Per ulteriori informazioni, vedere [la pagina relativa alla chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Creazione di un pacchetto di estensione di Visual Studio (VSIX) per distribuire entrambi gli assembly.

- Test del nuovo passaggio di distribuzione.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Utilizzo del modello a oggetti del server per SharePoint. Per ulteriori informazioni, vedere [utilizzo del modello a oggetti lato server di SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Soluzioni di SharePoint. Per altre informazioni, vedere [Panoramica delle soluzioni](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Aggiornamento di soluzioni SharePoint. Per ulteriori informazioni, vedere [aggiornamento di una soluzione](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.

- Progetto di libreria di classi che implementa l'estensione. Il progetto deve avere come destinazione il .NET Framework 4,5.

- Progetto di libreria di classi che definisce i comandi personalizzati di SharePoint. Il progetto deve avere come destinazione il .NET Framework 3,5.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

5. Scegliere il modello di **progetto VSIX** , denominare il progetto **UpgradeDeploymentStep**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **UpgradeDeploymentStep** a **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere **Aggiungi**, quindi **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **Windows** .

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco delle versioni del .NET Framework.

4. Scegliere il modello di progetto **libreria di classi** , denominare il progetto **DeploymentStepExtension**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **DeploymentStepExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

#### <a name="to-create-the-sharepoint-command-project"></a>Per creare il progetto di comando di SharePoint

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere **Aggiungi**, quindi **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere **Visual C#** o **Visual Basic**, quindi scegliere il nodo **Windows** .

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 3,5** nell'elenco delle versioni del .NET Framework.

4. Scegliere il modello di progetto **libreria di classi** , denominare il progetto **SharePointCommands**, quindi scegliere il pulsante **OK** .

     Visual Studio aggiunge il progetto **SharePointCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere il codice per creare il passaggio di distribuzione personalizzato, è necessario aggiungere i file di codice e i riferimenti ad assembly ed è necessario configurare i progetti.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Per configurare il progetto DeploymentStepExtension

1. Nel progetto **DeploymentStepExtension** aggiungere due file di codice con i nomi seguenti:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Aprire il menu di scelta rapida del progetto DeploymentStepExtension, quindi scegliere **Aggiungi riferimento**.

3. Nella scheda **Framework** selezionare la casella di controllo per l'assembly System. ComponentModel. Composition.

4. Nella scheda **estensioni** selezionare la casella di controllo per l'assembly Microsoft. VisualStudio. SharePoint, quindi scegliere il pulsante **OK** .

#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointCommands

1. Nel progetto **SharePointCommands** aggiungere un file di codice denominato Commands.

2. In **Esplora soluzioni**aprire il menu di scelta rapida sul nodo del progetto **SharePointCommands** , quindi scegliere **Aggiungi riferimento**.

3. Nella scheda **estensioni** selezionare le caselle di controllo per gli assembly seguenti, quindi fare clic su scegliere il pulsante **OK** .

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

## <a name="define-the-custom-deployment-step"></a>Definire la fase di distribuzione personalizzata
 Creare una classe che definisce il passaggio di distribuzione dell'aggiornamento. Per definire la fase di distribuzione, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia. Implementare questa interfaccia quando si desidera definire un passaggio di distribuzione personalizzato.

#### <a name="to-define-the-custom-deployment-step"></a>Per definire la fase di distribuzione personalizzata

1. Nel progetto **DeploymentStepExtension** aprire il file di codice UpgradeStep e quindi incollare il codice seguente al suo interno.

    > [!NOTE]
    > Dopo l'aggiunta di questo codice, il progetto avrà alcuni errori di compilazione, ma non sarà più necessario quando si aggiunge il codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Creare una configurazione di distribuzione che includa il passaggio di distribuzione personalizzato
 Creare un'estensione di progetto per la nuova configurazione di distribuzione, che include diversi passaggi di distribuzione incorporati e il nuovo passaggio di distribuzione dell'aggiornamento. Creando questa estensione, è possibile aiutare gli sviluppatori di SharePoint a usare il passaggio di distribuzione dell'aggiornamento nei progetti SharePoint.

 Per creare la configurazione di distribuzione, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Implementare questa interfaccia quando si desidera creare un'estensione di progetto SharePoint.

#### <a name="to-create-the-deployment-configuration"></a>Per creare la configurazione di distribuzione

1. Nel progetto **DeploymentStepExtension** aprire il file di codice DeploymentConfigurationExtension e quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi personalizzati di SharePoint
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti del server per SharePoint. Un comando determina se una soluzione è già stata distribuita. l'altro comando aggiorna una soluzione.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint

1. Nel progetto **SharePointCommands** aprire il file di codice dei comandi, quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la fase di distribuzione personalizzata e i comandi di SharePoint sono ora inclusi nei progetti. Crearli per assicurarsi che vengano compilati senza errori.

#### <a name="to-build-the-projects"></a>Per generare i progetti

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **DeploymentStepExtension** , quindi scegliere **Compila**.

2. Aprire il menu di scelta rapida per il progetto **SharePointCommands** , quindi scegliere **Compila**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto **UpgradeDeploymentStep** , aprire il menu di scelta rapida per il file **source. Extension. vsixmanifest** , quindi scegliere **Apri**.

     Visual Studio apre il file nell'editor manifesto. Il file source. Extension. vsixmanifest è la base per il file Extension. vsixmanifest che tutti i pacchetti VSIX richiedono. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Nella casella **nome prodotto** immettere **Aggiorna passaggio di distribuzione per progetti SharePoint**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **fornisce un passaggio di distribuzione dell'aggiornamento personalizzato che può essere utilizzato nei progetti SharePoint**.

5. Nella scheda **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** scegliere **DeploymentStepExtension**, quindi scegliere il pulsante **OK** .

9. Nell'editor del manifesto scegliere di nuovo il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

10. Nell'elenco **tipo** immettere **SharePoint. Commands. v4**.

    > [!NOTE]
    > Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per altre informazioni, vedere [elemento asset (schema VSX)](/previous-versions/dd393737(v=vs.110)).

11. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

12. Nell'elenco **progetto** scegliere **SharePointCommands**, quindi scegliere il pulsante **OK** .

13. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

14. Assicurarsi che la cartella di output di compilazione per il progetto UpgradeDeploymentStep contenga ora il file UpgradeDeploymentStep. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Preparare il test della fase di distribuzione dell'aggiornamento
 Per testare il passaggio di distribuzione dell'aggiornamento, è necessario innanzitutto distribuire una soluzione di esempio nel sito di SharePoint. Per iniziare, eseguire il debug dell'estensione nell'istanza sperimentale di Visual Studio. Creare quindi una definizione di elenco e un'istanza di elenco da usare per testare il passaggio di distribuzione e quindi distribuirli nel sito di SharePoint. Modificare quindi la definizione dell'elenco e l'istanza di elenco e ridistribuirli per dimostrare in che modo il processo di distribuzione predefinito sovrascrive le soluzioni nel sito di SharePoint.

 Più avanti in questa procedura dettagliata si modificherà la definizione dell'elenco e l'istanza di elenco e quindi si eseguirà l'aggiornamento nel sito di SharePoint.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione UpgradeDeploymentStep.

2. Nel progetto DeploymentStepExtension aprire il file di codice UpgradeStep, quindi aggiungere un punto di interruzione alla prima riga di codice nei `CanExecute` `Execute` metodi e.

3. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**sulla barra dei menu.

4. Visual Studio installa l'estensione nel passaggio di distribuzione%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade per SharePoint Projects\1.0 e avvia un'istanza sperimentale di Visual Studio. Il passaggio di distribuzione dell'aggiornamento verrà testato in questa istanza di Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Per creare un progetto SharePoint con una definizione di elenco e un'istanza di elenco

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual C#** o il nodo **Visual Basic** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nella parte superiore della finestra di dialogo verificare che **.NET Framework 3,5** sia visualizzato nell'elenco delle versioni del .NET Framework.

    I progetti per [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] richiedono questa versione del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **progetto SharePoint 2010**, denominare il progetto **EmployeesListDefinition**, quindi scegliere il pulsante **OK** .

5. Nella **procedura guidata di personalizzazione di SharePoint**immettere l'URL del sito che si desidera utilizzare per il debug.

6. In **Qual è il livello di attendibilità per la soluzione SharePoint**scegliere il pulsante di opzione **Distribuisci come soluzione farm** .

   > [!NOTE]
   > Il passaggio di distribuzione dell'aggiornamento non supporta le soluzioni create mediante sandbox.

7. Fare clic sul pulsante **Fine**.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea il progetto EmployeesListDefinition.

8. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

9. Nella finestra di dialogo **Aggiungi nuovo elemento-EmployeesListDefinition** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

10. Scegliere il modello di elemento **elenco** , denominare l' **elenco Employees**, quindi scegliere il pulsante **Aggiungi** .

     Verrà visualizzata la procedura guidata di personalizzazione di SharePoint

11. Nella pagina **Scegli Impostazioni elenco** verificare le impostazioni seguenti e quindi scegliere il pulsante **fine** :

    1. L' **elenco dei dipendenti** viene visualizzato nella casella specificare il nome da **visualizzare per l'elenco** .

    2. Viene scelto il pulsante di opzione **Crea un elenco personalizzabile in base a:** .

    3. Il **valore predefinito (blank)** viene scelto nell'elenco **Crea un elenco personalizzabile basato su:** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea l'elemento dell'elenco Employees con una colonna title e una singola istanza vuota e apre la finestra di progettazione elenco.

12. Nella scheda **colonne** della finestra di progettazione elenco scegliere la riga **digitare un nome di colonna nuovo o esistente** , quindi aggiungere le colonne seguenti nell'elenco **nome visualizzato colonna** :

    1. Nome

    2. Company

    3. Telefono ufficio

    4. Posta elettronica

13. Salvare tutti i file e quindi chiudere la finestra di progettazione elenco.

14. In **Esplora soluzioni**espandere il nodo **Employees list** , quindi espandere il nodo Child dell' **istanza List Employees** .

15. Nel file di *Elements.xml* sostituire il codice XML predefinito in questo file con il codice XML seguente. Questo XML modifica il nome dell'elenco in **Employees** e aggiunge informazioni per un dipendente denominato Jim Hance.

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

16. Salvare e chiudere il file di *Elements.xml* .

17. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition, quindi scegliere **Apri** o **Proprietà**.

     Verrà visualizzata la finestra di progettazione proprietà.

18. Nella scheda **SharePoint** deselezionare la casella di controllo **ritrazione automatica dopo il debug** , quindi salvare le proprietà.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Per distribuire la definizione elenco e l'istanza elenco

1. In **Esplora soluzioni**scegliere il nodo del progetto **EmployeesListDefinition** .

2. Nella finestra **Proprietà** verificare che la proprietà di **configurazione della distribuzione attiva** sia impostata sul **valore predefinito**.

3. Premere il tasto **F5** o scegliere **debug**  >  **Avvia debug**sulla barra dei menu.

4. Verificare che il progetto venga compilato correttamente, che il Web browser si apra al sito di SharePoint, che l'elemento **elenchi** nella barra avvio veloce includa l'elenco nuovi **dipendenti** e che l'elenco dei **dipendenti** includa la voce per Jim Hance.

5. Chiudere il Web browser.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Per modificare la definizione dell'elenco e l'istanza di elenco e ridistribuirli

1. Nel progetto EmployeesListDefinition aprire il file di *Elements.xml* figlio dell'elemento di progetto dell' **istanza dell'elenco dei dipendenti** .

2. Rimuovere l' `Data` elemento e i relativi elementi figlio per rimuovere la voce per Jim Hance dall'elenco.

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

3. Salvare e chiudere il file di *Elements.xml* .

4. Aprire il menu di scelta rapida per l'elemento del progetto **elenco dei dipendenti** , quindi scegliere **Apri** o **proprietà**.

5. Nella finestra di progettazione elenco scegliere la scheda **viste** .

6. Nell'elenco **colonne selezionate** scegliere **allegati**, quindi scegliere la chiave < per spostare la colonna nell'elenco **colonne disponibili** .

7. Ripetere il passaggio precedente per spostare la colonna **Business Phone** dall'elenco **colonne selezionate** all'elenco **colonne disponibili** .

     Questa azione rimuove questi campi dalla visualizzazione predefinita dell'elenco **Employees** sul sito di SharePoint.

8. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**sulla barra dei menu.

9. Verificare che venga visualizzata la finestra di dialogo **conflitti di distribuzione** .

     Questa finestra di dialogo viene visualizzata quando Visual Studio tenta di distribuire una soluzione (l'istanza dell'elenco) in un sito di SharePoint in cui è già stata distribuita la soluzione. Questa finestra di dialogo non verrà visualizzata quando si esegue il passaggio di distribuzione dell'aggiornamento più avanti in questa procedura dettagliata.

10. Nella finestra di dialogo **conflitti di distribuzione** scegliere il pulsante di opzione **Risolvi automaticamente** .

     Visual Studio Elimina l'istanza dell'elenco nel sito di SharePoint, distribuisce l'elemento elenco nel progetto e quindi apre il sito di SharePoint.

11. Nella sezione **elenchi** della barra avvio veloce scegliere l'elenco **dipendenti** , quindi verificare i seguenti dettagli:

    - Le colonne **Attachments** e **Home Phone** non vengono visualizzate in questa visualizzazione dell'elenco.

    - L'elenco è vuoto. Quando è stata usata la configurazione di distribuzione **predefinita** per ridistribuire la soluzione, l'elenco **Employees** è stato sostituito con il nuovo elenco vuoto nel progetto.

## <a name="test-the-deployment-step"></a>Testare il passaggio di distribuzione
 A questo punto è possibile eseguire il test della fase di distribuzione dell'aggiornamento. In primo luogo, aggiungere un elemento all'istanza dell'elenco in SharePoint. Modificare quindi la definizione dell'elenco e l'istanza di elenco, aggiornarli nel sito di SharePoint e verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il nuovo elemento.

#### <a name="to-manually-add-an-item-to-the-list"></a>Per aggiungere manualmente un elemento all'elenco

1. Sulla barra multifunzione sul sito di SharePoint, nella scheda **Strumenti elenco** scegliere la scheda **elementi** .

2. Nel **nuovo** gruppo scegliere **nuovo elemento**.

     In alternativa, è possibile scegliere il collegamento **Aggiungi nuovo elemento** nell'elenco di elementi.

3. Nella finestra **Employees-New Item** , nella casella **title** , immettere **Gestione strutture**.

4. Nella casella **First Name (nome** ) immettere **Andy**.

5. Nella casella **Company** digitare **Contoso**.

6. Scegliere il pulsante **Salva** , verificare che il nuovo elemento sia visualizzato nell'elenco e quindi chiudere il Web browser.

     Più avanti in questa procedura dettagliata si userà questo elemento per verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il contenuto di questo elenco.

#### <a name="to-test-the-upgrade-deployment-step"></a>Per testare il passaggio di distribuzione dell'aggiornamento

1. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **EmployeesListDefinition** , quindi scegliere **proprietà**.

    Verrà visualizzata la finestra di progettazione o l'editor delle proprietà.

2. Nella scheda **SharePoint** impostare la proprietà di **configurazione della distribuzione attiva** su **Aggiorna**.

    Questa configurazione di distribuzione personalizzata include il nuovo passaggio di distribuzione dell'aggiornamento.

3. Aprire il menu di scelta rapida per l'elemento del progetto **elenco dei dipendenti** , quindi scegliere **Proprietà** o **Apri**.

    Verrà visualizzata la finestra di progettazione o l'editor delle proprietà.

4. Nella scheda **viste** scegliere la colonna **posta elettronica** , quindi scegliere la **<** chiave per spostare la colonna dall'elenco **colonne selezionate** all'elenco **colonne disponibili** .

    Questa azione rimuove questi campi dalla visualizzazione predefinita dell'elenco **Employees** sul sito di SharePoint.

5. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**sulla barra dei menu.

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `CanExecute` metodo.

7. Premere di nuovo il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **continua**.

8. Verificare che il codice venga arrestato in corrispondenza del punto di interruzione impostato in precedenza nel `Execute` metodo.

9. Premere il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **continua** l'ora finale.

     Il Web browser apre il sito di SharePoint.

10. Nella sezione **elenchi** dell'area avvio veloce, scegliere l'elenco **dipendenti** , quindi verificare i seguenti dettagli:

    - L'elemento aggiunto manualmente in precedenza (per Andy, il gestore di strutture) è ancora presente nell'elenco.

    - Le colonne dell' **indirizzo di posta elettronica** e del **telefono aziendale** non vengono visualizzate in questa visualizzazione dell'elenco.

      La configurazione della distribuzione dell' **aggiornamento** modifica l'istanza dell'elenco dei **dipendenti** esistente nel sito di SharePoint. Se è stata usata la configurazione di distribuzione **predefinita** invece della configurazione dell' **aggiornamento** , si verificherà un conflitto di distribuzione. Visual Studio risolverebbe il conflitto sostituendo l'elenco **Employees** e l'elemento per Andy, il gestore di strutture, verrebbe eliminato.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test del passaggio di distribuzione dell'aggiornamento, rimuovere l'istanza dell'elenco e la definizione dell'elenco dal sito di SharePoint e rimuovere l'estensione della fase di distribuzione da Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Per rimuovere l'istanza dell'elenco dal sito di SharePoint

1. Aprire l'elenco **Employees** nel sito di SharePoint, se l'elenco non è già aperto.

2. Sulla barra multifunzione sul sito di SharePoint scegliere la scheda **Strumenti elenco** , quindi scegliere la scheda **elenco** .

3. Nel gruppo **Impostazioni** scegliere l'elemento **Impostazioni elenco** .

4. In **autorizzazioni e gestione**scegliere il comando **Elimina questo elenco** , scegliere **OK** per confermare che si desidera inviare l'elenco al Cestino, quindi chiudere il Web browser.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Per rimuovere la definizione dell'elenco dal sito di SharePoint

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Build**  >  **ritrazione**compilazione.

     Visual Studio ritira la definizione dell'elenco dal sito di SharePoint.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Aggiorna passaggio di distribuzione per progetti SharePoint**, quindi scegliere il comando **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere **Sì** per confermare che si vuole disinstallare l'estensione, quindi scegliere **Riavvia ora** per completare la disinstallazione.

4. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione UpgradeDeploymentStep).

## <a name="see-also"></a>Vedere anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)