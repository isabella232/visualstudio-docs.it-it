---
title: Creare un elemento di progetto azione personalizzata con il modello di elemento, parte 2
titleSuffix: ''
description: In questa procedura dettagliata aggiungere una procedura guidata per raccogliere informazioni dagli utenti quando usano un modello di elemento per aggiungere un elemento di progetto Azione personalizzata in un SharePoint sito.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 961b2c42f7c676271e9cf7d75418e9b9b66047534aed2abf0087809bf6957871
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367408"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2
  Dopo aver definito un tipo personalizzato di SharePoint progetto e associato a un modello di elemento in Visual Studio, è anche possibile fornire una procedura guidata per il modello. È possibile usare la procedura guidata per raccogliere informazioni dagli utenti quando usano il modello per aggiungere una nuova istanza dell'elemento di progetto a un progetto. Le informazioni raccolte possono essere usate per inizializzare l'elemento del progetto.

 In questa procedura dettagliata si aggiungerà una procedura guidata all'elemento di progetto Azione personalizzata illustrata in Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di [elemento, Parte 1.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md) Quando un utente aggiunge un elemento di progetto Azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione personalizzata (ad esempio il percorso e l'URL a cui passare quando l'utente finale lo sceglie) e aggiunge queste informazioni al file *Elements.xmlnel* nuovo elemento di progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una procedura guidata per un tipo SharePoint elemento di progetto personalizzato associato a un modello di elemento.

- Definizione di un'interfaccia utente personalizzata della procedura guidata simile alle procedure guidate incorporate per SharePoint di progetto in Visual Studio.

- Uso di parametri sostituibili per inizializzare SharePoint file di progetto con i dati raccolti nella procedura guidata.

- Debug e test della procedura guidata.

> [!NOTE]
> È possibile scaricare un esempio da [GitHub che](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) illustra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire questa procedura dettagliata, è prima necessario creare la soluzione CustomActionProjectItem completando Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di [elemento, parte 1.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

 Per completare questa procedura dettagliata sono necessari anche i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- L Visual Studio SDK. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Procedure guidate per i modelli di progetto e di elemento Visual Studio. Per altre informazioni, vedere [Procedura: Usare procedure guidate](../extensibility/how-to-use-wizards-with-project-templates.md) con Project modelli e l'interfaccia. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [Azione personalizzata](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Creare il progetto della procedura guidata
 Per completare questa procedura dettagliata, è necessario aggiungere un progetto alla soluzione CustomActionProjectItem creata in Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di [elemento, Parte 1.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md) Si implementerà <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia e si definirà l'interfaccia utente della procedura guidata in questo progetto.

#### <a name="to-create-the-wizard-project"></a>Per creare il progetto della procedura guidata

1. In Visual Studio aprire la soluzione CustomActionProjectItem

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

3. Nella finestra **di dialogo Nuovo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **Windows** nodo.

4. Nella parte superiore della finestra **di dialogo New Project** (Nuovo Project) assicurarsi che .NET Framework **4.5** sia selezionato nell'elenco delle versioni del .NET Framework.

5. Scegliere il **modello di progetto Libreria di controlli utente WPF,** assegnare al progetto il nome **ItemTemplateWizard** e quindi scegliere **OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ItemTemplateWizard** alla soluzione.

6. Eliminare l'elemento UserControl1 dal progetto.

## <a name="configure-the-wizard-project"></a>Configurare il progetto della procedura guidata
 Prima di creare la procedura guidata, è necessario aggiungere una finestra Windows Presentation Foundation (WPF), un file di codice e riferimenti all'assembly al progetto.

#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata

1. In **Esplora soluzioni** aprire il menu di scelta rapida dal nodo **del progetto ItemTemplateWizard** e quindi scegliere **Proprietà**.

2. In Progettazione **Project assicurarsi** che il framework di destinazione sia impostato su .NET Framework 4.5.

     Per i progetti Visual C#, è possibile impostare questo valore nella **scheda** Applicazione. Per Visual Basic progetti, è possibile impostare questo valore nella **scheda** Compila. Per altre informazioni, vedere [Procedura: Impostare come](../ide/visual-studio-multi-targeting-overview.md)destinazione una versione del .NET Framework .

3. Nel progetto **ItemTemplateWizard** aggiungere un **elemento Window (WPF)** al progetto e quindi assegnare all'elemento il nome **WizardWindow**.

4. Aggiungere due file di codice denominati CustomActionWizard e Strings.

5. Aprire il menu di scelta rapida per **il progetto ItemTemplateWizard** e quindi scegliere **Aggiungi riferimento**.

6. Nella finestra di dialogo Gestione riferimenti -  **ItemTemplateWizard** scegliere il nodo Estensioni nel **nodo** Assembly.

7. Selezionare le caselle di controllo accanto agli assembly seguenti e quindi scegliere **OK:**

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. In **Esplora soluzioni**, nella cartella **Riferimenti** per il progetto ItemTemplateWizard scegliere il riferimento **EnvDTE.**

9. Nella finestra **Proprietà** modificare il valore della proprietà Incorpora tipi **di** interoperabilità in **False**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definire il percorso predefinito e le stringhe ID per le azioni personalizzate
 Ogni azione personalizzata ha un percorso e un ID specificati negli `GroupID` attributi e `Location` dell'elemento `CustomAction` nel file *Elements.xml.* In questo passaggio vengono definite alcune stringhe valide per questi attributi nel progetto ItemTemplateWizard. Al termine di questa procedura dettagliata, queste stringhe vengono scritte nel file *Elements.xml* nell'elemento di progetto Azione personalizzata quando gli utenti specificano un percorso e un ID nella procedura guidata.

 Per semplicità, questo esempio supporta solo un subset dei percorsi predefiniti e degli ID disponibili. Per un elenco completo, vedere Percorsi e ID [predefiniti delle azioni personalizzate.](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))

#### <a name="to-define-the-default-location-and-id-strings"></a>Per definire la posizione predefinita e le stringhe ID

1. Aperto.

2. Nel progetto **ItemTemplateWizard** sostituire il codice nel file di codice Strings con il codice seguente.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>Creare l'interfaccia utente della procedura guidata
 Aggiungere XAML per definire l'interfaccia utente della procedura guidata e aggiungere codice per associare alcuni dei controlli della procedura guidata alle stringhe ID. La procedura guidata creata è simile alla procedura guidata incorporata per SharePoint progetti in Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Per creare l'interfaccia utente della procedura guidata

1. Nel progetto **ItemTemplateWizard** aprire il menu di scelta rapida per il file **WizardWindow.xaml** e quindi scegliere **Apri** per aprire la finestra nella finestra di progettazione.

2. Nella visualizzazione XAML sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un'intestazione, controlli per specificare il comportamento dell'azione personalizzata e pulsanti di spostamento nella parte inferiore della finestra.

    > [!NOTE]
    > Il progetto avrà alcuni errori di compilazione dopo l'aggiunta di questo codice. Questi errori verranno visualizzati quando si aggiunge il codice nei passaggi successivi.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > La finestra creata in questo codice XAML deriva dalla classe <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> di base. Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile derivare la finestra di dialogo da questa classe per applicare uno stile coerente con altre finestre di dialogo in Visual Studio ed evitare problemi che altrimenti potrebbero verificarsi con le finestre di dialogo modali. Per altre informazioni, vedere [Creazione e gestione di finestre di dialogo modali](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Se si sviluppa un progetto Visual Basic, rimuovere lo spazio dei nomi dal nome della classe `ItemTemplateWizard` `WizardWindow` `x:Class` nell'attributo `Window` dell'elemento . Questo elemento si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile al codice seguente:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Nel file code-behind per il file WizardWindow.xaml sostituire il codice corrente con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire la funzionalità della procedura guidata implementando <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia .

#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata

1. Nel progetto **ItemTemplateWizard** aprire il file di codice **CustomActionWizard** e quindi sostituire il codice corrente in questo file con il codice seguente:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata si trova ora nel progetto. Compilare il progetto per assicurarsi che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

## <a name="associate-the-wizard-with-the-item-template"></a>Associare la procedura guidata al modello di elemento
 Dopo aver implementato la procedura guidata, è necessario associarla al modello di elemento **Azione** personalizzata completando tre passaggi principali:

1. Firmare l'assembly della procedura guidata con un nome sicuro.

2. Ottenere il token di chiave pubblica per l'assembly della procedura guidata.

3. Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il **modello di elemento Azione** personalizzata.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro

1. In **Esplora soluzioni** aprire il menu di scelta rapida dal nodo **del progetto ItemTemplateWizard** e quindi scegliere **Proprietà**.

2. Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.

3. **Nell'elenco Scegliere un file di chiave con nome** sicuro scegliere **\<New...>** .

4. Nella finestra **di dialogo Crea** chiave con nome sicuro immettere un nome, deselezionare la casella di controllo Proteggi il file di chiave con una **password** e quindi scegliere **OK.**

5. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata

1. In una finestra Visual Studio prompt dei comandi eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ItemTemplateWizard.dll compilato per il progetto ItemTemplateWizard nel computer di sviluppo.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Il token di chiave pubblica per *lItemTemplateWizard.dll* assembly viene scritto nella finestra Visual Studio prompt dei comandi.

2. Mantenere aperta Visual Studio prompt dei comandi. Per completare la procedura successiva, è necessario il token di chiave pubblica.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate

1. In **Esplora soluzioni** espandere il **nodo di progetto ItemTemplate** e quindi aprire il file *ItemTemplate.vstemplate.*

2. Alla fine del file aggiungere l'elemento `WizardExtension` seguente tra i tag e `</TemplateContent>` `</VSTemplate>` . Sostituire il *valore YourToken* dell'attributo con il token di chiave `PublicKeyToken` pubblica ottenuto nella procedura precedente.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Per altre informazioni `WizardExtension` sull'elemento , vedere [WizardExtension Element &#40;Visual Studio Templates&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Salvare e chiudere il file.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Aggiungere parametri sostituibili al *fileElements.xml* nel modello di elemento
 Aggiungere diversi parametri sostituibili al file *Elements.xml* nel progetto ItemTemplate. Questi parametri vengono inizializzati nel `PopulateReplacementDictionary` metodo nella classe definita in `CustomActionWizard` precedenza. Quando un utente aggiunge un elemento di progetto Azione personalizzata a un progetto, Visual Studio sostituisce automaticamente questi parametri nel file *Elements.xml* nel nuovo elemento di progetto con i valori specificati nella procedura guidata.

 Un parametro sostituibile è un token che inizia e termina con il simbolo del dollaro ($). Oltre a definire parametri sostituibili personalizzati, è possibile usare i parametri predefiniti che il SharePoint di progetto definisce e inizializza. Per altre informazioni, vedere [Parametri sostituibili.](../sharepoint/replaceable-parameters.md)

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili al file *Elements.xml* file

1. Nel progetto ItemTemplate sostituire il contenuto del file *Elements.xml* con il codice XML seguente.

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

     Il nuovo codice XML modifica i valori degli attributi `Id` , , , e in parametri `GroupId` `Location` `Description` `Url` sostituibili.

2. Salvare e chiudere il file.

## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata al pacchetto VSIX
 Nel file source.extension.vsixmanifest nel progetto VSIX aggiungere un riferimento al progetto della procedura guidata in modo che sia distribuito con il pacchetto VSIX che contiene l'elemento di progetto.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata al pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida dal file **source.extension.vsixmanifest** nel progetto CustomActionProjectItem e quindi scegliere **Apri** per aprire il file nell'editor manifesto.

2. Nell'editor del manifesto scegliere la **scheda Asset** e quindi scegliere **il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.Assembly**.

4. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

5. **Nell'Project,** scegliere **ItemTemplateWizard** e quindi fare clic sul **pulsante OK.**

6. Sulla barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che  >  la soluzione venga compilata senza errori.

## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto è possibile testare la procedura guidata. Iniziare prima di tutto a eseguire il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per l'elemento di progetto Azione personalizzata in un progetto SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il SharePoint per verificare che l'azione personalizzata funzioni come previsto.

#### <a name="to-start-to-debug-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.

2. Nel progetto ItemTemplateWizard aprire il file di codice CustomActionWizard e quindi aggiungere un punto di interruzione alla prima riga di codice nel `RunStarted` metodo .

3. Sulla barra dei menu scegliere **Debug**  >  **eccezioni**.

4. Nella finestra **di** dialogo Eccezioni  assicurarsi che  le caselle di controllo Generato e Non gestito dall'utente per Eccezioni **Common Language Runtime** siano deselezionate e quindi scegliere **OK.**

5. Avviare il debug scegliendo **il tasto F5** oppure, sulla barra dei menu, scegliendo **Debug**  >  **Avvia debug**.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento di progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **File**  >    >  **nuovo Project**.

2. Espandere il nodo **Visual C#** **o Visual Basic** (a seconda del linguaggio che supporta il modello di elemento), espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

3. Nell'elenco dei modelli di progetto scegliere SharePoint **2010 Project**, assegnare al progetto il nome **CustomActionWizardTest** e quindi scegliere **OK.**

4. Nella **Personalizzazione SharePoint guidata** immettere l'URL del sito che si vuole usare per il debug e quindi scegliere il **pulsante** Fine.

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi** e quindi **Nuovo elemento.**

6. Nella finestra di dialogo Aggiungi nuovo elemento -  **CustomItemWizardTest** espandere il nodo SharePoint e quindi espandere il nodo **2010.**

7. Nell'elenco degli elementi del progetto scegliere **l'elemento Azione** personalizzata e quindi scegliere **il pulsante** Aggiungi.

8. Verificare che il codice nell'altra istanza di Visual Studio si arresti sul punto di interruzione impostato in precedenza nel `RunStarted` metodo .

9. Continuare a eseguire il debug del progetto scegliendo **il tasto F5** o, sulla barra dei menu, scegliendo **Debug**  >  **continua**.

     Viene visualizzata la Personalizzazione guidata SharePoint.

10. In **Posizione** scegliere il **pulsante di opzione Elenca** modifica.

11. **Nell'elenco ID gruppo** scegliere **Comunicazioni**.

12. Nella casella **Titolo** immettere SharePoint **Developer Center.**

13. Nella casella **Descrizione** immettere Apre **il sito Web SharePoint Developer Center**.

14. Nella casella **URL** immettere **https://docs.microsoft.com/sharepoint/dev/** e quindi scegliere il **pulsante** Fine.

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il *file* Elements.xmlnell'editor. Verificare che *Elements.xml* contenga i valori specificati nella procedura guidata.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale di Visual Studio premere **F5** oppure, sulla barra dei menu, scegliere **Debug**  >  **Avvia debug**.

     L'azione personalizzata viene in pacchetto e distribuita nel sito SharePoint specificato dalla proprietà **URL** sito del progetto e il Web browser viene aperto nella pagina predefinita del sito.

    > [!NOTE]
    > Se viene **visualizzata la finestra di** dialogo Debug script disabilitato , scegliere il **pulsante** Sì .

2. Nell'area Elenchi del sito SharePoint scegliere il **collegamento** Attività.

     Verrà **visualizzata la pagina Attività - Tutte** le attività.

3. Nella scheda **Strumenti elenco** della barra  multifunzione scegliere la scheda Elenco **e** quindi nel gruppo Impostazioni scegliere Elenco Impostazioni **.**

     Viene **visualizzata Impostazioni** elenco.

4. Sotto **l'intestazione** Comunicazioni nella parte superiore della pagina scegliere il collegamento **SharePoint Developer Center,** verificare che il browser apra il sito Web e quindi https://docs.microsoft.com/sharepoint/dev/ chiudere il browser.

## <a name="cleaning-up-the-development-computer"></a>Pulizia del computer di sviluppo
 Dopo aver completato il test dell'elemento di progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Estensioni**  >  **e aggiornamenti degli strumenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere l'azione **personalizzata Project'estensione Elemento** e quindi scegliere il **pulsante Disinstalla.**

3. Nella finestra di dialogo visualizzata  scegliere il pulsante Sì per confermare che si vuole disinstallare l'estensione e quindi scegliere il pulsante Riavvia **ora** per completare la disinstallazione.

4. Chiudere entrambe le istanze Visual Studio (istanza sperimentale e istanza di Visual Studio in cui è aperta la soluzione CustomActionProjectItem).

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Percorsi e ID predefiniti delle azioni personalizzate](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
