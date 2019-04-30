---
title: 'Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9417c2116dde909bda948e7d9140d7f52b090d68
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430482"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1
  È possibile estendere il sistema di progetto SharePoint in Visual Studio tramite la creazione di tipi di elemento di un progetto. In questa procedura dettagliata, si creerà un elemento del progetto che può essere aggiunti a un progetto di SharePoint per creare un'azione personalizzata in un sito di SharePoint. L'azione personalizzata aggiunge una voce di menu per il **Azioni sito** menu del sito di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per un'azione personalizzata. Il nuovo tipo di elemento di progetto implementa diverse funzionalità personalizzate:

  - Menu di scelta rapida che viene usato come punto di partenza per altre attività correlate all'elemento del progetto, ad esempio visualizzando una finestra di progettazione per l'azione personalizzata in Visual Studio.

  - Codice eseguito quando uno sviluppatore modificato alcune proprietà dell'elemento del progetto e il progetto che lo contiene.

  - Un'icona personalizzata visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.

- Creazione di un modello di elemento di Visual Studio per l'elemento del progetto.

- Creazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire il modello di elemento di progetto e l'assembly dell'estensione.

- Il debug e test dell'elemento di progetto.

  Si tratta di una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento del progetto mediante l'aggiunta di una procedura guidata per il modello di elemento. Per altre informazioni, vedere [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> È possibile scaricare un esempio dal [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) che mostra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:

- Le edizioni di Visual Studio, SharePoint e Microsoft Windows.

- Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [l'azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177800).

- Modelli di elementi in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX. Questo progetto consente di creare il pacchetto VSIX per distribuire l'elemento del progetto SharePoint.

- Un progetto di modello di elemento. Questo progetto consente di creare un modello di elemento che può essere utilizzato per aggiungere l'elemento del progetto SharePoint a un progetto SharePoint.

- Un progetto di libreria di classi. Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento del progetto SharePoint.

  Avviare la procedura dettagliata mediante la creazione di progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nell'elenco nella parte superiore della **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** sia selezionata.

4. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.

    > [!NOTE]
    > Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

5. Scegliere il **progetto VSIX** modello.

6. Nel **Name** casella, immettere **CustomActionProjectItem**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **CustomActionProjectItem** progetto al **Esplora soluzioni**.

#### <a name="to-create-the-item-template-project"></a>Per creare il progetto di modello di elemento

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nell'elenco nella parte superiore della **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** sia selezionata.

3. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.

4. Nell'elenco dei modelli di progetto, scegliere il **modello di elemento di linguaggio c#** oppure **modello di elemento di Visual Basic** modello.

5. Nel **Name** casella, immettere **ItemTemplate**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ItemTemplate** progetto alla soluzione.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nell'elenco nella parte superiore della **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** sia selezionata.

3. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, scegliere il **Windows** nodo e quindi scegliere il  **Libreria di classi** modello di progetto.

4. Nel **Name** casella, immettere **ProjectItemDefinition**e quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ProjectItemDefinition** progetto alla soluzione e apre il file di codice predefinita Class1.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per definire il tipo di elemento di progetto SharePoint, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

2. Nell'elenco degli elementi del progetto, scegliere **File di codice**.

3. Nel **Name** immettere il nome **CustomAction** con l'appropriato estensione del nome file e quindi scegliere il **Aggiungi** pulsante.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto e quindi scegliere **Aggiungi riferimento**.

5. Nel **gestione riferimenti - ProjectItemDefinition** finestra di dialogo scegliere la **assembly** nodo e quindi scegliere il **Framework** nodo.

6. Selezionare la casella di controllo accanto a ogni degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Scegliere il **Extensions** nodo, selezionare la casella di controllo accanto all'assembly Microsoft.VisualStudio.Sharepoint e quindi scegliere il **OK** pulsante.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint
 Creare una classe che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di elemento di progetto.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint

1. Nel progetto ProjectItemDefinition, aprire il file di codice CustomAction con l'account.

2. Sostituire il codice in questo file con il codice seguente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Creare un'icona per l'elemento del progetto in Esplora soluzioni
 Quando si crea un elemento di progetto SharePoint personalizzato, è possibile associare un'immagine (un'icona o bitmap) con l'elemento del progetto. Questa immagine viene visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.

 Nella procedura seguente, creare un'icona per l'elemento del progetto e tale icona viene incorporata nell'assembly di estensione. Fa riferimento questa icona il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> del `CustomActionProjectItemTypeProvider` classe creata in precedenza.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Per creare un'icona personalizzata per l'elemento del progetto

1. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto, scegliere **Add**, quindi scegliere **nuovo elemento...** .

2. Nell'elenco degli elementi del progetto, scegliere il **File di icona** elemento.

    > [!NOTE]
    > Nei progetti Visual Basic, è necessario scegliere il **generali** nodo per visualizzare i **File di icona** elemento.

3. Nel **Name** casella, immettere **CustomAction_SolutionExplorer. ico**e quindi scegliere il **Aggiungi** pulsante.

     Viene aperta la nuova icona nel **Editor di immagini**.

4. Modificare la versione 16 x 16 del file icona, in modo che ha una struttura, è possibile riconoscere e quindi salvare il file dell'icona.

5. Nelle **Esplora soluzioni**, scegliere **CustomAction_SolutionExplorer. ico**.

6. Nel **delle proprietà** finestra, scegliere la freccia accanto al **azione di compilazione** proprietà.

7. Nell'elenco visualizzato, scegliere **risorsa incorporata**.

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'elemento del progetto è ora nel progetto. Compilare il progetto per verificare che venga compilata senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto e scegliere **compilazione**.

## <a name="create-a-visual-studio-item-template"></a>Creare un modello di elemento di Visual Studio
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, è necessario creare un modello di progetto o un modello di elemento. Gli sviluppatori di usano questi modelli in Visual Studio per creare un'istanza dell'elemento di progetto mediante la creazione di un nuovo progetto, o aggiungendo un elemento a un progetto esistente. Per questa procedura dettagliata, usare il progetto di ItemTemplate per configurare l'elemento di progetto.

#### <a name="to-create-the-item-template"></a>Per creare il modello di elemento

1. Eliminare il file di codice Class1 dal progetto ItemTemplate.

2. Nel progetto ItemTemplate, aprire il *ItemTemplate* file.

3. Sostituire il contenuto del file con il codice XML seguente, quindi salvare e chiudere il file.

    > [!NOTE]
    > Il codice XML seguente è per un modello di elemento di Visual c#. Se si sta creando un modello di elemento di Visual Basic, sostituire il valore dei `ProjectType` elemento con `VisualBasic`.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Questo file definisce il contenuto e il comportamento del modello di elemento. Per altre informazioni sul contenuto di questo file, vedere [riferimenti allo Schema di Visual Studio modello](/visualstudio/extensibility/visual-studio-template-schema-reference).

4. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

5. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File di testo** modello.

6. Nel **Name** casella, immettere **CustomAction. spdata**e quindi scegliere il **Aggiungi** pulsante.

7. Aggiungere il seguente codice XML per il *CustomAction. spdata* file, quindi salvare e chiudere il file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Questo file contiene informazioni sui file di contenuti dall'elemento del progetto. Il `Type` attributo del `ProjectItem` deve essere impostato sulla stessa stringa che viene passato al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto (il `CustomActionProjectItemTypeProvider` classe creata in precedenza in questa procedura dettagliata). Per altre informazioni sul contenuto di *spdata* i file, vedere [riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

9. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File XML** modello.

10. Nel **Name** casella, immettere **Elements. XML**e quindi scegliere il **Aggiungi** pulsante.

11. Sostituire il contenuto del *Elements* file con il codice XML seguente, quindi salvare e chiudere il file.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Questo file definisce un'azione personalizzata predefinita che crea una voce di menu sul **Azioni sito** menu del sito di SharePoint. Quando un utente sceglie la voce di menu, l'URL specificato nella `UrlAction` apre nel browser web. Per altre informazioni sugli elementi XML è possibile usare per definire un'azione personalizzata, vedere [definizioni delle azioni personalizzate](http://go.microsoft.com/fwlink/?LinkId=177801).

12. Facoltativamente, aprire il *ItemTemplate. ico* file e modificarlo in modo che includa una progettazione che è in grado di riconoscere. Questa icona verrà visualizzata accanto all'elemento di progetto nel **Aggiungi nuovo elemento** nella finestra di dialogo.

13. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto e quindi scegliere **Scarica progetto**.

14. Aprire il menu di scelta rapida per il **ItemTemplate** nuovo progetto e quindi scegliere **Modifica ItemTemplate. csproj** oppure **Modifica ItemTemplate**.

15. Individuare la seguente `VSTemplate` elemento nel file di progetto.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Sostituire questo `VSTemplate` elemento con il codice XML seguente e quindi salvare e chiudere il file.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Il `OutputSubPath` elemento specifica cartelle aggiuntive nel percorso in cui viene creato il modello di elemento quando si compila il progetto. Le cartelle specificate in questo caso assicurarsi che il modello di elemento sarà disponibile solo quando i clienti aprire il **Aggiungi nuovo elemento** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.

17. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto e quindi scegliere **Ricarica progetto**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Creare un pacchetto VSIX per distribuire l'elemento del progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **vsixmanifest** nel progetto CustomActionProjectItem e quindi scegliere **aprire**.

     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest costituisce la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nel **Product Name** casella, immettere **elemento di progetto azione personalizzata**.

3. Nel **Author** casella, immettere **Contoso**.

4. Nel **Description** casella, immettere **elemento del progetto di SharePoint che rappresenta un'azione personalizzata**.

5. Nel **asset** scheda, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

6. Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.ItemTemplate**.

    > [!NOTE]
    > Questo valore corrisponde al `ItemTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di elemento di progetto. Per altre informazioni, vedere [elemento ItemTemplate (Schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

8. Nel **progetto** scegliere **ItemTemplate**, quindi scegliere il **OK** pulsante.

9. Nel **Assets** scheda, scegliere il **New** nuovamente clic sul pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

10. Nel **tipo** casella di riepilogo **MEFComponent**.

    > [!NOTE]
    > Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

12. Nel **Project** casella di riepilogo **ProjectItemDefinition**.

13. Fare clic sul pulsante **OK** .

14. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.

15. Assicurarsi che la cartella di output di compilazione per il progetto CustomActionProjectItem contiene il file CustomActionProjectItem.

     Per impostazione predefinita, la cartella di output di compilazione è di... nella cartella \bin\Debug sotto la cartella che contiene il progetto CustomActionProjectItem.

## <a name="test-the-project-item"></a>L'elemento del progetto di test
 A questo punto si è pronti per l'elemento del progetto di test. Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi il **l'azione personalizzata** elemento del progetto in un progetto di SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che l'azione personalizzata funziona come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.

2. Aprire il file di codice CustomAction con l'account e quindi aggiungere un punto di interruzione per la prima riga del codice nel `InitializeType` (metodo).

3. Scegliere il **F5** chiave per avviare il debug.

     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 progetto di azione e viene avviata un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Per testare l'elemento del progetto in Visual Studio

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.

2. Espandere **Visual c#** oppure **Visual Basic** (a seconda del linguaggio che supporta il modello di elemento), espandere **SharePoint**, quindi scegliere il **2010**  nodo.

3. Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**.

4. Nel **Name** casella, immettere **CustomActionTest**e quindi scegliere il **OK** pulsante.

5. Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **fine** pulsante.

6. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.

7. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **2010** nodo sotto il **SharePoint** nodo.

     Verificare che il **l'azione personalizzata** elemento viene visualizzato nell'elenco di elementi di progetto.

8. Scegliere il **l'azione personalizzata** elemento e quindi scegliere il **Add** pulsante.

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il *Elements* file nell'editor.

9. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nel `InitializeType` (metodo).

10. Scegliere il **F5** un tasto per continuare il debug del progetto.

11. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**, aprire il menu di scelta rapida per il **CustomAction1** nodo, quindi scegliere **finestra di progettazione vista personalizzata azione**.

12. Verificare che viene visualizzata una finestra di messaggio e quindi scegliere il **OK** pulsante.

     È possibile usare questo menu di scelta rapida per fornire opzioni aggiuntive o i comandi per gli sviluppatori, ad esempio visualizzando una finestra di progettazione per l'azione personalizzata.

13. Nella barra dei menu, scegliere **View** > **Output**.

     Il **Output** verrà visualizzata la finestra.

14. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **CustomAction1** elemento e quindi modificarne il nome in **MyCustomAction**.

     Nel **Output** verrà visualizzata la finestra, un messaggio di conferma. Questo messaggio viene scritto per la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> gestore dell'evento definito nel `CustomActionProjectItemTypeProvider` classe. È possibile gestire questo evento e altri eventi di elemento di progetto per implementare il comportamento personalizzato quando lo sviluppatore modifica l'elemento del progetto.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale di Visual Studio, aprire il *Elements. XML* file che è un figlio di **MyCustomAction** elemento del progetto.

2. Nel *Elements* file, apportare le modifiche seguenti e quindi salvare il file:

    - Nel `CustomAction` elemento, impostare il `Id` dell'attributo a un GUID o un'altra stringa univoca come illustrato nell'esempio seguente:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Nel `CustomAction` elemento, impostare il `Title` attributo come illustrato nell'esempio seguente:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Nel `CustomAction` elemento, impostare il `Description` attributo come illustrato nell'esempio seguente:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Nel `UrlAction` elemento, impostare il `Url` attributo come illustrato nell'esempio seguente:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Premere **F5**.

     L'azione personalizzata viene incluso nel pacchetto e distribuito nel sito di SharePoint specificato nella **URL sito** proprietà del progetto. Il browser viene visualizzata la pagina predefinita del sito.

    > [!NOTE]
    > Se il **debug degli Script disabilitato** verrà visualizzata la finestra di dialogo, scegliere il **Yes** per continuare il debug del progetto.

4. Nel **Azioni sito** menu, scegliere **Centro per sviluppatori SharePoint**, verificare che nel browser verrà aperto il sito Web https://docs.microsoft.com/sharepoint/dev/e quindi chiudere il browser web.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni, scegliere **elemento di progetto azione personalizzata**, quindi scegliere il **Disinstalla** pulsante.

3. Nella finestra di dialogo visualizzata, scegliere il **Sì** per confermare che si desidera disinstallare l'estensione.

4. Scegliere il **Riavvia ora** pulsante per completare la disinstallazione.

5. Chiudere l'istanza sperimentale di Visual Studio sia l'istanza in cui la soluzione CustomActionProjectItem è aperta.

## <a name="next-steps"></a>Passaggi successivi
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata per il modello di elemento. Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione (ad esempio la posizione e l'URL a cui passare quando viene scelto l'azione) e aggiunge queste informazioni per il *Elements*file nel nuovo elemento di progetto. Per altre informazioni, vedere [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o un'altra immagine &#40;Image Editor for Icons&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)