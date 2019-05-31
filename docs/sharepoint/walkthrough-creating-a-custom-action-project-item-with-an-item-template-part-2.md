---
title: Crea elemento di progetto azione personalizzata con modello di elemento, parte 2
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6fa4915b9621789c68ed994440de3a1ef544c40c
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401171"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2
  Dopo aver definito un tipo di elemento di progetto SharePoint personalizzato e associarlo a un modello di elemento in Visual Studio, potrebbe anche voler fornire una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando usano il modello per aggiungere una nuova istanza dell'elemento del progetto a un progetto. Le informazioni raccolte sono utilizzabile per inizializzare l'elemento del progetto.

 In questa procedura dettagliata si aggiungerà una procedura guidata per l'elemento di progetto azione personalizzata che viene illustrata in [procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione personalizzata (ad esempio la posizione e l'URL a cui passare quando un utente finale sceglie) e aggiunge queste informazioni per il *Elements. XML* file nel nuovo elemento di progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di elemento.

- Definizione di una procedura guidata personalizzata dell'interfaccia utente simile alle procedure guidate predefinite per gli elementi di progetto SharePoint in Visual Studio.

- Uso dei parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.

- Il debug e test della procedura guidata.

> [!NOTE]
> È possibile scaricare un esempio dal [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) che mostra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire questa procedura dettagliata, è innanzitutto necessario creare la soluzione CustomActionProjectItem completando [procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Sono inoltre necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:

- Procedure guidate per i modelli di progetto ed elemento in Visual Studio. Per altre informazioni, vedere [Procedura: Usare le procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [l'azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177800).

## <a name="create-the-wizard-project"></a>Creare il progetto della procedura guidata
 Per completare questa procedura dettagliata, è necessario aggiungere un progetto alla soluzione creata in CustomActionProjectItem [procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Si implementeranno i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia e definire la procedura guidata dell'interfaccia utente in questo progetto.

#### <a name="to-create-the-wizard-project"></a>Per creare il progetto della procedura guidata

1. In Visual Studio, aprire la soluzione CustomActionProjectItem

2. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

3. Nel **nuovo progetto** finestra di dialogo, espandere il **Visual c#** oppure **Visual Basic** nodi e quindi scegliere il **Windows** nodo.

4. In cima il **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.

5. Scegliere il **libreria di controlli utente WPF** modello di progetto, denominare il progetto **ItemTemplateWizard**, quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ItemTemplateWizard** progetto alla soluzione.

6. Eliminare l'elemento UserControl1 dal progetto.

## <a name="configure-the-wizard-project"></a>Configurare il progetto della procedura guidata
 Prima di creare la procedura guidata, è necessario aggiungere una finestra di Windows Presentation Foundation (WPF), un file di codice e i riferimenti ad assembly al progetto.

#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida dalle **ItemTemplateWizard** nodo del progetto e quindi scegliere **proprietà**.

2. Nel **Progettazione progetti**, assicurarsi che il framework di destinazione sia impostato su .NET Framework 4.5.

     Per i progetti Visual c#, è possibile impostare questo valore sul **applicazione** scheda. Per i progetti Visual Basic, è possibile impostare questo valore sul **Compile** scheda. Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

3. Nel **ItemTemplateWizard** del progetto, aggiungere un **finestra (WPF)** elemento al progetto e quindi denominare l'elemento **nome WizardWindow**.

4. Aggiungere due file di codice denominati CustomActionWizard e stringhe.

5. Aprire il menu di scelta rapida per il **ItemTemplateWizard** del progetto e quindi scegliere **Aggiungi riferimento**.

6. Nel **gestione riferimenti - ItemTemplateWizard** nella finestra di dialogo il **assembly** nodo, scegliere il **estensioni** nodo.

7. Selezionare le caselle di controllo accanto agli assembly seguenti e quindi scegliere il **OK** pulsante:

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. Nella **Esplora soluzioni**, nella **riferimenti** cartella per il progetto ItemTemplateWizard, selezionare il **EnvDTE** riferimento.

9. Nel **le proprietà** finestra, modificare il valore della **incorpora tipi di interoperabilità** proprietà **False**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definire il percorso predefinito e le stringhe di ID per le azioni personalizzate
 Per ogni azione personalizzata ha un percorso e un ID specificato nella `GroupID` e `Location` attributi del `CustomAction` elemento nel *Elements. XML* file. In questo passaggio è definire alcune delle stringhe valide per questi attributi nel progetto ItemTemplateWizard. Dopo aver completato questa procedura dettagliata, tali stringhe vengono scritti i *Elements* file nell'elemento di progetto azione personalizzata quando gli utenti di specificare un percorso e un ID nella procedura guidata.

 Per semplicità, in questo esempio supporta solo un subset di percorsi predefiniti disponibili e gli ID. Per un elenco completo, vedere [percorsi di azione personalizzati predefiniti e gli ID](http://go.microsoft.com/fwlink/?LinkId=181964).

#### <a name="to-define-the-default-location-and-id-strings"></a>Per definire il percorso predefinito e le stringhe ID

1. aprire.

2. Nel **ItemTemplateWizard** del progetto, sostituire il codice nel file di codice le stringhe con il codice seguente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Creazione guidata dell'interfaccia utente
 Aggiungere XAML per definire l'interfaccia utente della procedura guidata e aggiungere il codice per associare alcuni controlli della procedura guidata per le stringhe di ID. La procedura guidata che si crea è simile alla procedura guidata predefinita per i progetti di SharePoint in Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Per creare la procedura guidata dell'interfaccia utente

1. Nel **ItemTemplateWizard** del progetto, aprire il menu di scelta rapida per il **WizardWindow** del file e quindi scegliere **aprire** per aprire la finestra nella finestra di progettazione.

2. Nella visualizzazione XAML, sostituire il XAML corrente con il XAML seguente. il XAML definisce un'interfaccia utente che include un'intestazione, i controlli che consentono di specificare il comportamento dell'azione personalizzati e i pulsanti di navigazione nella parte inferiore della finestra.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto avrà alcuni errori di compilazione. Questi errori scompare quando si aggiunge codice nei passaggi successivi.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > La finestra che viene creata in questo XAML viene ottenuta il <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe di base. Quando si aggiunge una finestra di dialogo WPF personalizzata in Visual Studio, è consigliabile derivare da questa classe sono coerenti con l'applicazione di stili con altre finestre di dialogo in Visual Studio ed evitare i problemi che potrebbero altrimenti verificarsi con finestre di dialogo modale la finestra di dialogo. Per altre informazioni, vedere [creazione e la gestione delle finestre di dialogo modale](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3. Se si sta sviluppando un progetto Visual Basic, rimuovere il `ItemTemplateWizard` dello spazio dei nomi dal `WizardWindow` nome di classe nel `x:Class` attributo del `Window` elemento. Questo elemento è nella prima riga della finestra di XAML. Al termine, la prima riga dovrebbe essere simile al seguente:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Nel file code-behind per il file WizardWindow, sostituire il codice corrente con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire le funzionalità della procedura guidata mediante l'implementazione di <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata

1. Nel **ItemTemplateWizard** project, aprire il **CustomActionWizard** file di codice e quindi sostituire il codice corrente in questo file con il codice seguente:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata è ora nel progetto. Compilare il progetto per assicurarsi che venga compilata senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

## <a name="associate-the-wizard-with-the-item-template"></a>La procedura guidata associazione con il modello di elemento
 Ora che è stata implementata la procedura guidata, è necessario associarlo con il **l'azione personalizzata** modello di elemento completando tre passaggi principali:

1. Firmare l'assembly della procedura guidata con un nome sicuro.

2. Ottenere la chiave pubblica token per l'assembly della procedura guidata.

3. Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il **l'azione personalizzata** modello di elemento.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida dalle **ItemTemplateWizard** nodo del progetto e quindi scegliere **proprietà**.

2. Nel **Signing** scheda, seleziona la **firmare l'assembly** casella di controllo.

3. Nel **Scegli un file chiave con nome sicuro** casella di riepilogo  **\<nuovo... >** .

4. Nel **Crea chiave con nome sicuro** finestra di dialogo immettere un nome, deselezionare le **Proteggi file di chiave con una password** casella di controllo e quindi scegliere il **OK** pulsante.

5. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata

1. In una finestra del Prompt dei comandi di Visual Studio, eseguire questo comando, sostituendo *PathToWizardAssembly* con il percorso completo per l'assembly compilato ItemTemplateWizard. dll per il progetto ItemTemplateWizard sullo sviluppo computer.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Il token di chiave pubblica per il *ItemTemplateWizard. dll* assembly viene scritto nella finestra del Prompt dei comandi di Visual Studio.

2. Mantenere aperta la finestra del Prompt dei comandi di Visual Studio. È necessario il token di chiave pubblica per completare la procedura successiva.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate

1. Nelle **Esplora soluzioni**, espandere il **ItemTemplate** nodo del progetto e quindi aprire il *ItemTemplate* file.

2. Verso la fine del file, aggiungere quanto segue `WizardExtension` elemento tra il `</TemplateContent>` e `</VSTemplate>` tag. Sostituire il *YourToken* pari al `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Per altre informazioni sul `WizardExtension` elemento, vedere [elemento WizardExtension &#40;modelli di Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3. Salvare e chiudere il file.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Aggiungere parametri sostituibili per il *Elements* file nel modello di elemento
 Aggiungere parametri sostituibili diversi per il *Elements. XML* file nel progetto di ItemTemplate. Questi parametri vengono inizializzati nel `PopulateReplacementDictionary` nel metodo il `CustomActionWizard` classe definita in precedenza. Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto, Visual Studio sostituisce automaticamente questi parametri, il *Elements* file nel nuovo elemento di progetto con i valori che vengono specificati nella procedura guidata.

 Un parametro sostituibile è un token che inizia e termina con il simbolo di dollaro ($). Oltre a definire i propri parametri sostituibili, è possibile usare alcuni parametri predefiniti che definisce e ne inizializza il sistema di progetto SharePoint. Per altre informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili per il *Elements* file

1. Nel progetto di ItemTemplate, sostituire il contenuto del *Elements* file con il codice XML seguente.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     Il nuovo codice XML modificano i valori del `Id`, `GroupId`, `Location`, `Description`, e `Url` attributi a parametri sostituibili.

2. Salvare e chiudere il file.

## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata per il pacchetto VSIX
 Nel file vsixmanifest nel progetto VSIX, aggiungere un riferimento al progetto della procedura guidata in modo che venga distribuita con il pacchetto VSIX che contiene l'elemento del progetto.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata per il pacchetto VSIX

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida dal **vsixmanifest** nel progetto CustomActionProjectItem e quindi scegliere **aprire** aprire il file nell'editor del manifesto.

2. Nell'editor del manifesto, scegliere il **Assets** tab, quindi scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

3. Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.Assembly**.

4. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

5. Nel **progetto** scegliere **ItemTemplateWizard**, quindi scegliere il **OK** pulsante.

6. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto si è pronti testare la procedura guidata. Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per l'elemento di progetto azione personalizzata in un progetto di SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che l'azione personalizzata funziona come previsto.

#### <a name="to-start-to-debug-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.

2. Nel progetto ItemTemplateWizard, aprire il file di codice CustomActionWizard e quindi aggiungere un punto di interruzione per la prima riga del codice nel `RunStarted` (metodo).

3. Nella barra dei menu, scegliere **Debug** > **eccezioni**.

4. Nel **eccezioni** finestra di dialogo, assicurarsi che le **generata** e **User-unhandled** caselle di controllo per **eccezioni Common Language Runtime**vengono cancellati e quindi scegliere il **OK** pulsante.

5. Avviare il debug scegliendo il **F5** chiave, o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.

     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 progetto di azione e viene avviata un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.

2. Espandere la **Visual c#** o **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di elemento), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

3. Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**, denominare il progetto **CustomActionWizardTest**, quindi scegliere il **OK** pulsante.

4. Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **fine** pulsante.

5. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

6. Nel **Aggiungi nuovo elemento - CustomItemWizardTest** finestra di dialogo, espandere il **SharePoint** nodo, quindi espandere il **2010** nodo.

7. Nell'elenco degli elementi del progetto, scegliere il **l'azione personalizzata** elemento e quindi scegliere il **Add** pulsante.

8. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nel `RunStarted` (metodo).

9. Continuare il debug del progetto scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **continua**.

     Viene visualizzata la personalizzazione guidata SharePoint.

10. Sotto **ubicazione**, scegliere il **elenco Modifica** pulsante di opzione.

11. Nel **ID del gruppo** elenco, scegliere **Communications**.

12. Nel **Title** casella, immettere **Centro per sviluppatori SharePoint**.

13. Nel **Description** casella, immettere **apre il sito Web di SharePoint Developer Center**.

14. Nel **URL** immettere **https://docs.microsoft.com/sharepoint/dev/** , quindi scegliere il **fine** pulsante.

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il *Elements* file nell'editor. Verificare che *Elements* contiene i valori specificati nella procedura guidata.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale di Visual Studio, scegliere il **F5** chiave alternativa, sulla barra dei menu, scegliere **Debug** > **Avvia debug**.

     L'azione personalizzata viene incluso nel pacchetto e distribuito nel sito di SharePoint specificato per il **URL sito** proprietà del progetto e il web browser viene visualizzata la pagina predefinita del sito.

    > [!NOTE]
    > Se il **debug degli Script disabilitato** verrà visualizzata la finestra di dialogo, scegliere il **Yes** pulsante.

2. Nell'area di elenchi del sito di SharePoint, scegliere il **attività** collegamento.

     Il **attività - tutte le attività** verrà visualizzata la pagina.

3. Nel **strumenti elenco** scheda della barra multifunzione, scegliere il **elenco** scheda e quindi nel **impostazioni** gruppo, scegliere **impostazioni elenco**.

     Il **le impostazioni dell'elenco** verrà visualizzata la pagina.

4. Sotto il **Communications** intestazione nella parte superiore della pagina, scegliere il **Centro per sviluppatori SharePoint** collegare, verificare che nel browser verrà aperto il sito Web https://docs.microsoft.com/sharepoint/dev/e quindi chiudere il browser.

## <a name="cleaning-up-the-development-computer"></a>Pulizia dei computer di sviluppo
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni, scegliere il **elemento di progetto azione personalizzata** estensione, quindi scegliere il **Disinstalla** pulsante.

3. Nella finestra di dialogo visualizzata, scegliere il **Yes** per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** pulsante per completare la disinstallazione.

4. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione CustomActionProjectItem è aperta).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Gli ID e i percorsi predefiniti azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=181964)
