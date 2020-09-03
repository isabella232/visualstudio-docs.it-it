---
title: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c96546f85b21ee0ca8a559059a16158b743cb915
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016098"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2
  Dopo aver definito un tipo personalizzato di elemento di progetto SharePoint e averlo associato a un modello di elemento in Visual Studio, potrebbe essere necessario fornire anche una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per aggiungere una nuova istanza dell'elemento del progetto a un progetto. Le informazioni raccolte possono essere utilizzate per inizializzare l'elemento del progetto.

 In questa procedura dettagliata verrà aggiunta una procedura guidata all'elemento del progetto di azione personalizzata illustrato in [procedura dettagliata: creare un elemento del progetto di azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Quando un utente aggiunge un elemento del progetto di azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione personalizzata, ad esempio il percorso e l'URL a cui passare quando viene scelto da un utente finale, e aggiunge tali informazioni al file *Elements.xml* nel nuovo elemento del progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di elemento.

- Definizione di un'interfaccia utente personalizzata della procedura guidata simile alle procedure guidate predefinite per gli elementi del progetto SharePoint in Visual Studio.

- Utilizzo di parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.

- Debug e test della procedura guidata.

> [!NOTE]
> È possibile scaricare un esempio da [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) che Mostra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire questa procedura dettagliata, è necessario innanzitutto creare la soluzione CustomActionProjectItem completando [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Per completare questa procedura dettagliata, è inoltre necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Procedure guidate per i modelli di progetto e di elemento in Visual Studio. Per altre informazioni, vedere [procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [azione personalizzata](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Creare il progetto della procedura guidata
 Per completare questa procedura dettagliata, è necessario aggiungere un progetto alla soluzione CustomActionProjectItem creata in [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). L'interfaccia verrà implementata <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> e verrà definita l'interfaccia utente della procedura guidata in questo progetto.

#### <a name="to-create-the-wizard-project"></a>Per creare il progetto della procedura guidata

1. In Visual Studio aprire la soluzione CustomActionProjectItem

2. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **Windows** .

4. Nella parte superiore della finestra di dialogo **nuovo progetto** assicurarsi che **.NET Framework 4,5** sia selezionato nell'elenco delle versioni del .NET Framework.

5. Scegliere il modello di progetto **libreria di controlli utente WPF** , denominare il progetto **ItemTemplateWizard**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ItemTemplateWizard** alla soluzione.

6. Eliminare l'elemento UserControl1 dal progetto.

## <a name="configure-the-wizard-project"></a>Configurare il progetto della procedura guidata
 Prima di creare la procedura guidata, è necessario aggiungere una finestra Windows Presentation Foundation (WPF), un file di codice e i riferimenti ad assembly al progetto.

#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata

1. In **Esplora soluzioni**aprire il menu di scelta rapida dal nodo del progetto **ItemTemplateWizard** , quindi scegliere **proprietà**.

2. In **Progettazione progetti**verificare che il Framework di destinazione sia impostato su .NET Framework 4,5.

     Per i progetti Visual C#, è possibile impostare questo valore nella scheda **applicazione** . Per Visual Basic progetti, è possibile impostare questo valore nella scheda **Compila** . Per altre informazioni, vedere [How to: target a version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. Nel progetto **ItemTemplateWizard** aggiungere un elemento **Window (WPF)** al progetto e quindi denominare l'elemento **WizardWindow**.

4. Aggiungere due file di codice denominati CustomActionWizard e Strings.

5. Aprire il menu di scelta rapida per il progetto **ItemTemplateWizard** , quindi scegliere **Aggiungi riferimento**.

6. Nella finestra di dialogo **Gestione riferimenti-ItemTemplateWizard** , nel nodo **assembly** , scegliere il nodo **estensioni** .

7. Selezionare le caselle di controllo accanto agli assembly seguenti, quindi scegliere il pulsante **OK** :

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. In **Esplora soluzioni**, nella cartella **riferimenti** per il progetto ItemTemplateWizard, scegliere il riferimento a **EnvDTE** .

9. Nella finestra **Proprietà** modificare il valore della proprietà **Incorpora tipi di interoperabilità** su **false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definire il percorso e le stringhe di ID predefiniti per le azioni personalizzate
 Ogni azione personalizzata ha un percorso e un ID specificati negli `GroupID` `Location` attributi e dell' `CustomAction` elemento nel file di *Elements.xml* . In questo passaggio si definiscono alcune delle stringhe valide per questi attributi nel progetto ItemTemplateWizard. Al termine di questa procedura dettagliata, queste stringhe vengono scritte nel file di *Elements.xml* nell'elemento del progetto di azione personalizzata quando gli utenti specificano un percorso e un ID nella procedura guidata.

 Per semplicità, questo esempio supporta solo un subset dei percorsi e degli ID predefiniti disponibili. Per un elenco completo, vedere [percorsi e ID predefiniti per le azioni personalizzate](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Per definire il percorso e le stringhe di ID predefiniti

1. aprire.

2. Nel progetto **ItemTemplateWizard** sostituire il codice nel file di codice delle stringhe con il codice seguente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Creazione dell'interfaccia utente della procedura guidata
 Aggiungere XAML per definire l'interfaccia utente della procedura guidata e aggiungere codice per associare alcuni dei controlli della procedura guidata alle stringhe ID. La procedura guidata creata è simile alla procedura guidata incorporata per i progetti SharePoint in Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Per creare l'interfaccia utente della procedura guidata

1. Nel progetto **ItemTemplateWizard** aprire il menu di scelta rapida per il file **WizardWindow. XAML** , quindi scegliere **Apri** per aprire la finestra nella finestra di progettazione.

2. Nella visualizzazione XAML sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un'intestazione, i controlli per specificare il comportamento dell'azione personalizzata e i pulsanti di spostamento nella parte inferiore della finestra.

    > [!NOTE]
    > Il progetto avrà alcuni errori di compilazione dopo l'aggiunta di questo codice. Questi errori si verificano quando si aggiunge codice nei passaggi successivi.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > La finestra creata in questo codice XAML è derivata dalla <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe base. Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile derivare la finestra di dialogo da questa classe per ottenere uno stile coerente con altre finestre di dialogo in Visual Studio ed evitare problemi che altrimenti potrebbero verificarsi con le finestre di dialogo modali. Per ulteriori informazioni, vedere [creazione e gestione di finestre di dialogo modali](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Se si sta sviluppando un progetto di Visual Basic, rimuovere lo `ItemTemplateWizard` spazio dei nomi dal `WizardWindow` nome della classe nell' `x:Class` attributo dell' `Window` elemento. Questo elemento si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile al codice seguente:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Nel file code-behind per il file WizardWindow. xaml sostituire il codice corrente con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire la funzionalità della procedura guidata implementando l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata

1. Nel progetto **ItemTemplateWizard** aprire il file di codice **CustomActionWizard** e quindi sostituire il codice corrente nel file con il codice seguente:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata è ora presente nel progetto. Compilare il progetto per assicurarsi che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

## <a name="associate-the-wizard-with-the-item-template"></a>Associare la procedura guidata al modello di elemento
 Ora che è stata implementata la procedura guidata, è necessario associarla al modello di elemento dell' **azione personalizzata** completando tre passaggi principali:

1. Firmare l'assembly della procedura guidata con un nome sicuro.

2. Ottenere il token di chiave pubblica per l'assembly della procedura guidata.

3. Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il modello di elemento **azione personalizzato** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro

1. In **Esplora soluzioni**aprire il menu di scelta rapida dal nodo del progetto **ItemTemplateWizard** , quindi scegliere **proprietà**.

2. Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.

3. Nell'elenco **Scegli un file chiave con nome sicuro** scegliere **\<New...>** .

4. Nella finestra di dialogo **Crea chiave con nome sicuro** immettere un nome, deselezionare la casella di controllo **Proteggi file di chiave con una password** , quindi scegliere il pulsante **OK** .

5. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata

1. In una finestra del prompt dei comandi di Visual Studio, eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ItemTemplateWizard.dll compilato per il progetto ItemTemplateWizard nel computer di sviluppo.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Il token di chiave pubblica per l'assembly *ItemTemplateWizard.dll* viene scritto nella finestra del prompt dei comandi di Visual Studio.

2. Lasciare aperta la finestra del prompt dei comandi di Visual Studio. Per completare la procedura successiva, è necessario il token di chiave pubblica.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate

1. In **Esplora soluzioni**espandere il nodo del progetto **ItemTemplate** , quindi aprire il file *ItemTemplate. vstemplate* .

2. In prossimità della fine del file, aggiungere l' `WizardExtension` elemento seguente tra i `</TemplateContent>` `</VSTemplate>` tag e. Sostituire il valore *yourtoken* dell' `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Per altre informazioni sull' `WizardExtension` elemento, vedere [elemento WizardExtension &#40;modelli di Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Salvare e chiudere il file.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Aggiungere parametri sostituibili al file *Elements.xml* nel modello di elemento
 Aggiungere diversi parametri sostituibili al file *Elements.xml* nel progetto ItemTemplate. Questi parametri vengono inizializzati nel `PopulateReplacementDictionary` metodo nella `CustomActionWizard` classe definita in precedenza. Quando un utente aggiunge un elemento del progetto di azione personalizzata a un progetto, Visual Studio sostituisce automaticamente questi parametri nel file di *Elements.xml* nel nuovo elemento del progetto con i valori specificati nella procedura guidata.

 Un parametro sostituibile è un token che inizia e termina con il segno di dollaro ($). Oltre a definire i propri parametri sostituibili, è possibile utilizzare parametri predefiniti che vengono definiti e inizializzati dal sistema del progetto SharePoint. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili al file di *Elements.xml*

1. Nel progetto ItemTemplate sostituire il contenuto del file di *Elements.xml* con il codice XML seguente.

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

     Il nuovo XML modifica i valori degli `Id` attributi, `GroupId` , `Location` , `Description` e `Url` in parametri sostituibili.

2. Salvare e chiudere il file.

## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata al pacchetto VSIX
 Nel file source. Extension. vsixmanifest del progetto VSIX aggiungere un riferimento al progetto della procedura guidata in modo che sia distribuito con il pacchetto VSIX contenente l'elemento del progetto.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata al pacchetto VSIX

1. In **Esplora soluzioni**aprire il menu di scelta rapida dal file **source. Extension. vsixmanifest** nel progetto CustomActionProjectItem, quindi scegliere **Apri** per aprire il file nell'editor manifesto.

2. Nell'editor del manifesto scegliere la scheda **Asset** , quindi scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. assembly**.

4. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

5. Nell'elenco **progetto** scegliere **ItemTemplateWizard**, quindi scegliere il pulsante **OK** .

6. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto si è pronti per testare la procedura guidata. Per prima cosa, iniziare a eseguire il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per l'elemento del progetto di azione personalizzata in un progetto SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto SharePoint per verificare che l'azione personalizzata funzioni come previsto.

#### <a name="to-start-to-debug-the-solution"></a>Per iniziare a eseguire il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione CustomActionProjectItem.

2. Nel progetto ItemTemplateWizard aprire il file di codice CustomActionWizard e quindi aggiungere un punto di interruzione alla prima riga di codice nel `RunStarted` metodo.

3. Nella barra dei menu scegliere **debug**  >  **eccezioni**.

4. Nella finestra di dialogo **eccezioni** assicurarsi che le caselle di controllo **generate** e non **gestite dall'utente** per le **eccezioni Common Language Runtime** siano deselezionate, quindi scegliere il pulsante **OK** .

5. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**dalla barra dei menu.

     Visual Studio installa l'estensione nel progetto di azione%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Espandere il nodo **Visual C#** o **Visual Basic** (a seconda della lingua supportata dal modello di elemento), espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nell'elenco dei modelli di progetto scegliere **progetto SharePoint 2010**, denominare il progetto **CustomActionWizardTest**, quindi scegliere il pulsante **OK** .

4. Nella **procedura guidata di personalizzazione di SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug, quindi scegliere il pulsante **fine** .

5. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

6. Nella finestra di dialogo **Aggiungi nuovo elemento-CustomItemWizardTest** espandere il nodo **SharePoint** , quindi espandere il nodo **2010** .

7. Nell'elenco degli elementi del progetto scegliere l'elemento **azione personalizzata** , quindi scegliere il pulsante **Aggiungi** .

8. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `RunStarted` metodo.

9. Continuare a eseguire il debug del progetto scegliendo il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **continua**.

     Viene visualizzata la Personalizzazione guidata SharePoint.

10. In **percorso**scegliere il pulsante di opzione **modifica elenco** .

11. Nell'elenco **ID gruppo** scegliere **comunicazioni**.

12. Nella casella **titolo** immettere centro per **sviluppatori di SharePoint**.

13. Nella casella  **Descrizione** immettere **apre il sito Web del centro per sviluppatori di SharePoint**.

14. Nella casella **URL** immettere **https://docs.microsoft.com/sharepoint/dev/** , quindi scegliere il pulsante **fine** .

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il file di *Elements.xml* nell'editor. Verificare che *Elements.xml* contenga i valori specificati nella procedura guidata.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale di Visual Studio scegliere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**dalla barra dei menu.

     L'azione personalizzata viene assemblata e distribuita nel sito di SharePoint specificato dalla proprietà **URL sito** del progetto e il Web browser si apre alla pagina predefinita del sito.

    > [!NOTE]
    > Se viene visualizzata la finestra di dialogo **debug script disabilitato** , scegliere il pulsante **Sì** .

2. Nell'area elenchi del sito di SharePoint scegliere il collegamento **attività** .

     Viene visualizzata la pagina **attività-tutte le attività** .

3. Nella scheda **Strumenti elenco** della barra multifunzione scegliere la scheda **elenco** e quindi nel gruppo **Impostazioni** scegliere **Impostazioni elenco**.

     Verrà visualizzata la pagina **Impostazioni elenco** .

4. Sotto l'intestazione **comunicazioni** nella parte superiore della pagina, scegliere il collegamento **centro per sviluppatori SharePoint** , verificare che il browser apra il sito Web https://docs.microsoft.com/sharepoint/dev/ e quindi chiudere il browser.

## <a name="cleaning-up-the-development-computer"></a>Pulizia del computer di sviluppo
 Al termine del test dell'elemento del progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere l'estensione dell' **elemento di progetto azione personalizzata** , quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione, quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

4. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione CustomActionProjectItem).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Percorsi e ID predefiniti per le azioni personalizzate](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
