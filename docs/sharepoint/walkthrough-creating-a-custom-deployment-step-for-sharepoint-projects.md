---
title: Creare un passaggio di distribuzione personalizzato per SharePoint progetti
description: In questa procedura dettagliata viene creato un passaggio di distribuzione personalizzato per aggiornare SharePoint soluzioni di progetto in un server che esegue SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4e445ecbc48abfd91149d45af7adb19eeaa7fe03
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092709"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per SharePoint progetti
  Quando si distribuisce un SharePoint, Visual Studio esegue una serie di passaggi di distribuzione in un ordine specifico. Visual Studio include molti passaggi di distribuzione predefiniti, ma è anche possibile crearne di personalizzati.

 In questa procedura dettagliata verrà creato un passaggio di distribuzione personalizzato per aggiornare le soluzioni in un server che esegue SharePoint. Visual Studio include passaggi di distribuzione predefiniti per molte attività, ad esempio il ritiro o l'aggiunta di soluzioni, ma non include un passaggio di distribuzione per l'aggiornamento delle soluzioni. Per impostazione predefinita, quando si distribuisce una soluzione SharePoint, Visual Studio prima di tutto ritrae la soluzione (se è già distribuita) e quindi ridistribuisce l'intera soluzione. Per altre informazioni sui passaggi di distribuzione predefiniti, vedere Distribuire, pubblicare e aggiornare SharePoint [pacchetti della soluzione.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di Visual Studio'estensione che esegue due attività principali:

  - L'estensione definisce un passaggio di distribuzione personalizzato per aggiornare SharePoint soluzioni.

  - L'estensione crea un'estensione di progetto che definisce una nuova configurazione di distribuzione, ovvero un set di passaggi di distribuzione eseguiti per un determinato progetto. La nuova configurazione di distribuzione include il passaggio di distribuzione personalizzato e diversi passaggi di distribuzione predefiniti.

- Creare due comandi SharePoint personalizzati che l'assembly di estensione chiama. SharePoint comandi sono metodi che possono essere chiamati dagli assembly di estensione per usare le API nel modello a oggetti del server per SharePoint. Per altre informazioni, vedere [Chiamare i modelli SharePoint a oggetti.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Compilazione di Visual Studio (VSIX) per distribuire entrambi gli assembly.

- Test del nuovo passaggio di distribuzione.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- SDK Visual Studio. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'estensione. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Utilizzo del modello a oggetti del server per SharePoint. Per altre informazioni, vedere [Using the SharePoint Foundation Server-Side Object Model](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- SharePoint soluzioni. Per altre informazioni, vedere [Panoramica delle soluzioni.](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))

- Aggiornamento SharePoint soluzioni. Per altre informazioni, vedere [Aggiornamento di una soluzione.](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14))

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.

- Progetto di libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione .NET Framework 4.5.

- Progetto di libreria di classi che definisce i comandi SharePoint personalizzati. Questo progetto deve avere come destinazione .NET Framework 3.5.

  Iniziare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

3. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **nodo Extensibility.**

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

5. Scegliere il **modello di Project VSIX,** assegnare al progetto il nome **UpgradeDeploymentStep** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto UpgradeDeploymentStep** **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **Windows** nodo.

3. Nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5** nell'elenco delle versioni del .NET Framework.

4. Scegliere il **modello di progetto** Libreria di classi, assegnare al progetto il nome **DeploymentStepExtension** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto DeploymentStepExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

#### <a name="to-create-the-sharepoint-command-project"></a>Per creare il progetto SharePoint comando

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra **di dialogo Project** espandere Visual **C#** o **Visual Basic** e quindi scegliere il **Windows** nodo.

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 3.5** nell'elenco delle versioni del .NET Framework.

4. Scegliere il **modello di progetto** Libreria di classi, assegnare al progetto il nome **SharePointCommands** e quindi scegliere **il pulsante OK.**

     Visual Studio aggiunge il **progetto SharePointCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere codice per creare il passaggio di distribuzione personalizzato, è necessario aggiungere file di codice e riferimenti ad assembly ed è necessario configurare i progetti.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Per configurare il progetto DeploymentStepExtension

1. Nel progetto **DeploymentStepExtension** aggiungere due file di codice con i nomi seguenti:

    - Passaggio di aggiornamento

    - DeploymentConfigurationExtension

2. Aprire il menu di scelta rapida nel progetto DeploymentStepExtension e quindi scegliere **Aggiungi riferimento.**

3. Nella scheda **Framework** selezionare la casella di controllo per l'assembly System.ComponentModel.Composition.

4. Nella scheda **Estensioni** selezionare la casella di controllo per Microsoft.VisualStudio. SharePoint assembly e quindi scegliere **il pulsante OK.**

#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointCommands

1. Nel **progetto SharePointCommands** aggiungere un file di codice denominato Commands.

2. In **Esplora soluzioni** aprire il menu di scelta rapida nel nodo **del progetto SharePointCommands** e quindi scegliere **Aggiungi riferimento.**

3. Nella scheda **Estensioni** selezionare le caselle di controllo per gli assembly seguenti e quindi fare clic sul **pulsante OK**

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Comandi

## <a name="define-the-custom-deployment-step"></a>Definire il passaggio di distribuzione personalizzato
 Creare una classe che definisce il passaggio di distribuzione dell'aggiornamento. Per definire il passaggio di distribuzione, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole definire un passaggio di distribuzione personalizzato.

#### <a name="to-define-the-custom-deployment-step"></a>Per definire il passaggio di distribuzione personalizzato

1. Nel progetto **DeploymentStepExtension** aprire il file di codice UpgradeStep e incollarlo al suo interno.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto avrà alcuni errori di compilazione, ma non verranno più aggiunti quando si aggiungerà il codice nei passaggi successivi.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet1":::

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Creare una configurazione di distribuzione che includa il passaggio di distribuzione personalizzato
 Creare un'estensione di progetto per la nuova configurazione di distribuzione, che include diversi passaggi di distribuzione predefiniti e il nuovo passaggio di distribuzione dell'aggiornamento. La creazione di questa estensione consente agli sviluppatori SharePoint di usare il passaggio di distribuzione dell'aggiornamento SharePoint progetti.

 Per creare la configurazione della distribuzione, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole creare un'SharePoint di progetto.

#### <a name="to-create-the-deployment-configuration"></a>Per creare la configurazione della distribuzione

1. Nel progetto **DeploymentStepExtension** aprire il file di codice DeploymentConfigurationExtension e incollarlo al suo interno.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb" id="Snippet2":::

## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi SharePoint personalizzati
 Creare due comandi personalizzati che chiamano nel modello a oggetti del server per SharePoint. Un comando determina se una soluzione è già distribuita. l'altro comando aggiorna una soluzione.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i SharePoint seguenti

1. Nel progetto **SharePointCommands** aprire il file di codice Commands e incollarlo al suo interno.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet4":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il passaggio di distribuzione personalizzato e i comandi SharePoint sono ora presenti nei progetti. Compilarli per assicurarsi che siano compilati senza errori.

#### <a name="to-build-the-projects"></a>Per generare i progetti

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto DeploymentStepExtension** e quindi scegliere **Compila.**

2. Aprire il menu di scelta rapida **per il progetto SharePointCommands** e quindi scegliere **Compila.**

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare prima di tutto il pacchetto VSIX modificando il file source.extension.vsixmanifest nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** nel progetto **UpgradeDeploymentStep** aprire il menu di scelta rapida per il file **source.extension.vsixmanifest** e quindi scegliere **Apri.**

     Visual Studio apre il file nell'editor manifesto. Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere Upgrade Deployment Step for SharePoint Projects (Passaggio di **distribuzione aggiornamento per SharePoint progetti).**

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **Fornisce un passaggio di distribuzione dell'aggiornamento personalizzato che può essere usato nei SharePoint personalizzati**.

5. Nella **scheda Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

7. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

8. **Nell'Project** distribuzione scegliere **DeploymentStepExtension** e quindi scegliere **il pulsante OK.**

9. Nell'editor del manifesto scegliere di **nuovo il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

10. **Nell'elenco** Tipo immettere **SharePoint. Commands.v4**.

    > [!NOTE]
    > Questo elemento specifica un'estensione personalizzata che si vuole includere nell'Visual Studio personalizzata. Per altre informazioni, vedere [Elemento Asset (schema VSX).](/previous-versions/dd393737(v=vs.110))

11. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

12. **Nell'Project,** scegliere **SharePointComandi** e quindi scegliere **il pulsante OK.**

13. Nella barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che la  >  soluzione venga compilata senza errori.

14. Assicurarsi che la cartella dell'output di compilazione per il progetto UpgradeDeploymentStep contenga ora il file UpgradeDeploymentStep.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Preparare il test del passaggio di distribuzione dell'aggiornamento
 Per testare il passaggio di distribuzione dell'aggiornamento, è innanzitutto necessario distribuire una soluzione di esempio nel SharePoint sito. Per iniziare, eseguire il debug dell'estensione nell'istanza sperimentale di Visual Studio. Creare quindi una definizione di elenco e un'istanza di elenco da usare per testare il passaggio di distribuzione e quindi distribuirle nel SharePoint sito. Modificare quindi la definizione dell'elenco e l'istanza dell'elenco e ridistribuirle per illustrare come il processo di distribuzione predefinito sovrascrive le soluzioni SharePoint sito.

 Più avanti in questa procedura dettagliata si modificheranno la definizione dell'elenco e l'istanza dell'elenco, che verranno quindi aggiornati nel SharePoint sito.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione UpgradeDeploymentStep.

2. Nel progetto DeploymentStepExtension aprire il file di codice UpgradeStep e quindi aggiungere un punto di interruzione alla prima riga di codice nei `CanExecute` metodi `Execute` e .

3. Avviare il debug premendo **F5 oppure,** sulla barra dei menu, **scegliere Debug**  >  **Avvia debug**.

4. Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade Deployment Step for SharePoint Projects\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà il passaggio di distribuzione dell'aggiornamento in questa istanza di Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Per creare un progetto SharePoint con una definizione di elenco e un'istanza di elenco

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **File**  >    >  **Nuovo Project**.

2. Nella finestra **di dialogo Project** espandere il nodo Visual **C#** o il nodo **Visual Basic,** espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

3. Nella parte superiore della finestra di dialogo verificare che **.NET Framework 3.5** sia visualizzato nell'elenco delle versioni del .NET Framework.

    I progetti [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] per e richiedono questa versione del [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere SharePoint **2010 Project,** assegnare al progetto il nome **EmployeesListDefinition** e quindi scegliere **il pulsante OK.**

5. Nella **Personalizzazione guidata SharePoint** immettere l'URL del sito che si vuole usare per il debug.

6. In **Qual è il livello di attendibilità per questa soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come** soluzione farm.

   > [!NOTE]
   > Il passaggio di distribuzione dell'aggiornamento non supporta le soluzioni in modalità sandbox.

7. Fare clic sul pulsante **Fine**.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto EmployeesListDefinition.

8. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition, scegliere **Aggiungi** e quindi nuovo **elemento.**

9. Nella finestra di dialogo Aggiungi nuovo elemento **- EmployeesListDefinition** **espandere** il nodo SharePoint e quindi scegliere il **nodo 2010.**

10. Scegliere il **modello Elemento** elenco, assegnare all'elemento il nome **Employees List** e quindi scegliere il **pulsante** Aggiungi.

     Verrà visualizzata SharePoint personalizzazione guidata impostazioni

11. Nella pagina **Impostazioni** elenco verificare le impostazioni seguenti e quindi scegliere il **pulsante** Fine:

    1. **Employees List** (Elenco dipendenti) viene visualizzato nella casella What name do you want to display for your list? (Quale nome si **vuole visualizzare per l'elenco?** ).

    2. Viene **scelto il pulsante di opzione Crea** un elenco personalizzabile basato su: .

    3. **Il valore predefinito (vuoto)** viene scelto nell'elenco **Crea un elenco personalizzabile basato su:** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea l'elemento Elenco dipendenti con una colonna Titolo e una singola istanza vuota e apre Progettazione elenchi.

12. Nella scheda Colonne di  Progettazione elenchi  scegliere la riga Digitare un nome di colonna nuovo o esistente e quindi aggiungere le colonne seguenti nell'elenco Nome **visualizzato** colonna :

    1. Nome

    2. Company

    3. Telefono ufficio

    4. Posta elettronica

13. Salvare tutti i file e quindi chiudere Progettazione elenchi.

14. In **Esplora soluzioni** espandere il **nodo Employees List** e quindi espandere il nodo figlio Employees **List Instance.**

15. Nel file *Elements.xml* sostituire il codice XML predefinito in questo file con il codice XML seguente. Questo codice XML modifica il nome dell'elenco **in Employees** e aggiunge le informazioni per un dipendente di nome Jim Hance.

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

16. Salvare e chiudere il file *Elements.xml.*

17. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition e quindi **scegliere Apri** o **Proprietà.**

     Verrà visualizzata la finestra Di progettazione proprietà.

18. Nella scheda **SharePoint** deselezionare la casella di controllo **Auto-retract after debugging** (Ritira automaticamente dopo il debug) e quindi salvare le proprietà.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Per distribuire la definizione dell'elenco e l'istanza di elenco

1. In **Esplora soluzioni** scegliere il **nodo del progetto EmployeesListDefinition.**

2. Nella finestra **Proprietà** verificare che la proprietà **Configurazione** distribuzione attiva sia impostata su **Predefinito.**

3. Premere **F5 oppure** scegliere Debug Avvia debug sulla barra dei  >  menu.

4. Verificare che il progetto sia compilato correttamente, che il Web browser si apra nel sito di SharePoint, che l'elemento **Elenchi** nella barra di Avvio veloce includa il nuovo elenco **Employees** e che l'elenco **Employees** includa la voce relativa a Jim Hance.

5. Chiudere il Web browser.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Per modificare la definizione dell'elenco e l'istanza dell'elenco e ridistribuirle

1. Nel progetto EmployeesListDefinition aprire il file *Elements.xml* figlio dell'elemento di progetto **Employee List Instance.**

2. Rimuovere `Data` l'elemento e i relativi elementi figlio per rimuovere la voce per Jim Hance dall'elenco.

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

3. Salvare e chiudere il file *Elements.xml.*

4. Aprire il menu di scelta rapida per **l'elemento di** progetto Employees List e quindi **scegliere Apri** o **Proprietà.**

5. In Progettazione elenchi scegliere la **scheda** Visualizzazioni.

6. **Nell'elenco Colonne** selezionate scegliere **Allegati** e quindi scegliere la chiave < per spostare la colonna nell'elenco **Colonne** disponibili .

7. Ripetere il passaggio precedente per spostare la colonna **Business Telefono** dall'elenco **Colonne** selezionate all'elenco **Colonne** disponibili .

     Questa azione rimuove questi campi dalla visualizzazione predefinita dell'elenco **Employees** nel SharePoint sito.

8. Avviare il debug premendo **F5 oppure,** sulla barra dei menu, **scegliere Debug**  >  **Avvia debug**.

9. Verificare che venga visualizzata **la finestra di** dialogo Conflitti di distribuzione .

     Questa finestra di dialogo viene visualizzata quando Visual Studio tenta di distribuire una soluzione (l'istanza di elenco) in un sito di SharePoint in cui tale soluzione è già stata distribuita. Questa finestra di dialogo non verrà visualizzata quando si esegue il passaggio di distribuzione dell'aggiornamento più avanti in questa procedura dettagliata.

10. Nella finestra **di dialogo Conflitti** di distribuzione scegliere il pulsante di opzione **Risolvi** automaticamente .

     Visual Studio elimina l'istanza dell'elenco nel sito SharePoint, distribuisce l'elemento elenco nel progetto e quindi apre il SharePoint sito.

11. Nella sezione **Elenchi** della barra Avvio veloce selezionare l'elenco **Dipendenti** e quindi verificare i dettagli seguenti:

    - Le **colonne** Allegati **e Home Telefono** non vengono visualizzate in questa visualizzazione dell'elenco.

    - L'elenco è vuoto. Quando è stata usata la **configurazione** di distribuzione predefinita per ridistribuire la soluzione, l'elenco **Employees** è stato sostituito con il nuovo elenco vuoto nel progetto.

## <a name="test-the-deployment-step"></a>Testare il passaggio di distribuzione
 A questo punto è possibile testare il passaggio di distribuzione dell'aggiornamento. Aggiungere prima di tutto un elemento all'istanza di elenco in SharePoint. Modificare quindi la definizione dell'elenco e l'istanza dell'elenco, aggiornarle nel sito SharePoint e verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il nuovo elemento.

#### <a name="to-manually-add-an-item-to-the-list"></a>Per aggiungere manualmente un elemento all'elenco

1. Nella barra multifunzione del sito SharePoint, nella **scheda Strumenti** elenco scegliere la **scheda** Elementi.

2. Nel gruppo **Nuovo** scegliere **Nuovo elemento**.

     In alternativa, è possibile scegliere il **collegamento Aggiungi nuovo elemento** nell'elenco di elementi stesso.

3. Nella casella Titolo della finestra Employees **- New Item** (Dipendenti - Nuovo elemento) immettere Facilities **Manager**. 

4. Nella casella **First Name (Nome)** immettere **Andy**.

5. Nella casella **Società** digitare **Contoso**.

6. Scegliere il **pulsante** Salva, verificare che il nuovo elemento venga visualizzato nell'elenco e quindi chiudere il Web browser.

     Più avanti in questa procedura dettagliata si userà questo elemento per verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il contenuto di questo elenco.

#### <a name="to-test-the-upgrade-deployment-step"></a>Per testare il passaggio di distribuzione dell'aggiornamento

1. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni** aprire il menu di scelta rapida per il nodo di progetto **EmployeesListDefinition** e quindi scegliere **Proprietà**.

    Verrà aperto Editor proprietà/Finestra di progettazione.

2. Nella scheda **SharePoint** impostare la proprietà **Configurazione distribuzione** attiva su **Aggiorna**.

    Questa configurazione di distribuzione personalizzata include il nuovo passaggio di distribuzione dell'aggiornamento.

3. Aprire il menu di scelta rapida per **l'elemento di** progetto Elenco dipendenti e quindi **scegliere Proprietà** o **Apri**.

    Verrà aperto Editor proprietà/Finestra di progettazione.

4. Nella scheda **Visualizzazioni** scegliere la colonna **Posta** elettronica e quindi scegliere la chiave per spostare la colonna dall'elenco Colonne selezionate all'elenco **<** **Colonne** disponibili. 

    Questa azione rimuove questi campi dalla visualizzazione predefinita dell'elenco **Dipendenti** nel SharePoint sito.

5. Avviare il debug scegliendo **il tasto F5** o, sulla barra dei menu, scegliendo **Debug**  >  **Avvia debug**.

6. Verificare che il codice nell'altra istanza di Visual Studio si arresti sul punto di interruzione impostato in precedenza nel `CanExecute` metodo .

7. Scegliere di **nuovo F5** oppure, sulla barra dei menu, scegliere **Continua**  >  **debug**.

8. Verificare che il codice si arresti sul punto di interruzione impostato in precedenza nel `Execute` metodo .

9. Scegliere il **tasto F5** oppure, nella barra dei menu, scegliere **Debug**  >  **Continua** un'ora finale.

     Il Web browser apre il SharePoint sito.

10. Nella sezione **Elenchi** dell'area Avvio veloce selezionare l'elenco **Dipendenti** e quindi verificare i dettagli seguenti:

    - L'elemento aggiunto manualmente in precedenza (per Andy, il gestore delle strutture) è ancora presente nell'elenco.

    - Le **colonne Telefono** e Indirizzo di **posta** elettronica non vengono visualizzate in questa visualizzazione dell'elenco.

      La **configurazione della** distribuzione di aggiornamento modifica l'istanza **dell'elenco Employees** esistente nel SharePoint sito. Se è stata usata la **configurazione di** distribuzione predefinita anziché la **configurazione di** aggiornamento, si verifica un conflitto di distribuzione. Visual Studio risolvere il conflitto sostituendo l'elenco **Employees** e l'elemento per Andy, il responsabile delle strutture, verrebbe eliminato.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il test del passaggio di distribuzione dell'aggiornamento, rimuovere l'istanza di elenco e la definizione dell'elenco dal sito SharePoint e rimuovere l'estensione del passaggio di distribuzione dal Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Per rimuovere l'istanza di elenco dal SharePoint sito

1. Aprire **l'elenco** Dipendenti nel SharePoint, se l'elenco non è già aperto.

2. Nella barra multifunzione del sito SharePoint scegliere la **scheda Strumenti** elenco e quindi scegliere **la scheda** Elenco.

3. Nel gruppo **Impostazioni** selezionare **l'elemento Impostazioni** elenco.

4. In **Autorizzazioni e** gestione  scegliere il comando Elimina questo elenco, scegliere **OK** per confermare che si vuole inviare l'elenco al Cestino e quindi chiudere il Web browser.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Per rimuovere la definizione dell'elenco dal SharePoint sito

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Build**  >  **Retract**.

     Visual Studio la definizione dell'elenco dal SharePoint sito.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Estensioni**  >  **e aggiornamenti degli strumenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Passaggio di distribuzione** di aggiornamento per SharePoint progetti e quindi scegliere il comando **Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere **Sì** per confermare che si vuole disinstallare l'estensione e quindi **scegliere** Riavvia ora per completare la disinstallazione.

4. Chiudere entrambe le istanze Visual Studio (istanza sperimentale e istanza di Visual Studio in cui è aperta la soluzione UpgradeDeploymentStep).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)