---
title: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: eccb9038b9fd929c713422aa79082c94ade512fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015929"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1
  Per estendere il sistema del progetto SharePoint in Visual Studio, è possibile creare tipi di elemento di progetto personalizzati. In questa procedura dettagliata verrà creato un elemento del progetto che può essere aggiunto a un progetto SharePoint per creare un'azione personalizzata in un sito di SharePoint. L'azione personalizzata consente di aggiungere una voce di menu al menu **Azioni sito** del sito di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per un'azione personalizzata. Il nuovo tipo di elemento di progetto implementa diverse funzionalità personalizzate:

  - Menu di scelta rapida che funge da punto di partenza per ulteriori attività correlate all'elemento del progetto, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata in Visual Studio.

  - Codice eseguito quando uno sviluppatore modifica determinate proprietà dell'elemento del progetto e del progetto che lo contiene.

  - Icona personalizzata visualizzata accanto all'elemento del progetto in **Esplora soluzioni**.

- Creazione di un modello di elemento di Visual Studio per l'elemento del progetto.

- Creazione di un pacchetto di estensione di Visual Studio (VSIX) per distribuire il modello di elemento di progetto e l'assembly dell'estensione.

- Debug e test dell'elemento del progetto.

  Si tratta di una procedura dettagliata autonoma. Al termine di questa procedura dettagliata, è possibile migliorare l'elemento del progetto aggiungendo una procedura guidata al modello di elemento. Per ulteriori informazioni, vedere [procedura dettagliata: creare un elemento del progetto di azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> È possibile scaricare un esempio da [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) che Mostra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [azione personalizzata](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Modelli di elemento in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'elemento del progetto SharePoint.

- Progetto di modello di elemento. Questo progetto crea un modello di elemento che può essere utilizzato per aggiungere l'elemento di progetto SharePoint a un progetto SharePoint.

- Un progetto libreria di classi. Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento del progetto SharePoint.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nell'elenco nella parte superiore della finestra di dialogo **nuovo progetto** verificare che sia selezionata l'opzione **.NET Framework 4,5** .

4. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

5. Scegliere il modello di **progetto VSIX** .

6. Nella casella **nome** immettere **CustomActionProjectItem**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **CustomActionProjectItem** a **Esplora soluzioni**.

#### <a name="to-create-the-item-template-project"></a>Per creare il progetto di modello di elemento

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nell'elenco nella parte superiore della finestra di dialogo **nuovo progetto** verificare che sia selezionata l'opzione **.NET Framework 4,5** .

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

4. Nell'elenco dei modelli di progetto scegliere il modello di **elemento C#** o modello **Visual Basic elemento** .

5. Nella casella **nome** immettere **ItemTemplate**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **ItemTemplate** alla soluzione.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nell'elenco nella parte superiore della finestra di dialogo **nuovo progetto** verificare che sia selezionata l'opzione **.NET Framework 4,5** .

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , scegliere il nodo **Windows** , quindi scegliere il modello di progetto **libreria di classi** .

4. Nella casella **nome** immettere **ProjectItemDefinition**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **ProjectItemDefinition** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere il codice per definire il tipo di elemento del progetto SharePoint, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** , scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

2. Nell'elenco di elementi del progetto scegliere **file di codice**.

3. Nella casella **nome** immettere il nome **CustomAction** con l'estensione del nome file appropriata, quindi scegliere il pulsante **Aggiungi** .

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** , quindi scegliere **Aggiungi riferimento**.

5. Nella finestra di dialogo **Gestione riferimenti-ProjectItemDefinition** scegliere il nodo **assembly** , quindi scegliere il nodo **Framework** .

6. Selezionare la casella di controllo accanto a ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Scegliere il nodo **estensioni** , selezionare la casella di controllo accanto all'assembly Microsoft. VisualStudio. SharePoint, quindi scegliere il pulsante **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint
 Creare una classe che implementi l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia quando si desidera definire un nuovo tipo di elemento di progetto.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint

1. Nel progetto ProjectItemDefinition aprire il file di codice CustomAction.

2. Sostituire il codice nel file con il codice seguente.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Creare un'icona per l'elemento del progetto in Esplora soluzioni
 Quando si crea un elemento di progetto SharePoint personalizzato, è possibile associare un'immagine, ovvero un'icona o una bitmap, all'elemento del progetto. Questa immagine viene visualizzata accanto all'elemento del progetto in **Esplora soluzioni**.

 Nella procedura seguente viene creata un'icona per l'elemento del progetto e incorporata l'icona nell'assembly dell'estensione. A questa icona viene fatto riferimento dall'oggetto <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> della `CustomActionProjectItemTypeProvider` classe creata in precedenza.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Per creare un'icona personalizzata per l'elemento del progetto

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** , scegliere **Aggiungi**, quindi scegliere **nuovo elemento.**

2. Nell'elenco degli elementi del progetto scegliere l'elemento del **file icona** .

    > [!NOTE]
    > In Visual Basic progetti è necessario scegliere il nodo **generale** per visualizzare l'elemento del **file icona** .

3. Nella casella **nome** immettere **CustomAction_SolutionExplorer. ico**, quindi scegliere il pulsante **Aggiungi** .

     La nuova icona verrà aperta nell' **editor di immagini**.

4. Modificare la versione 16x16 del file icona in modo che disponga di una progettazione che è possibile riconoscere, quindi salvare il file dell'icona.

5. In **Esplora soluzioni**scegliere **CustomAction_SolutionExplorer. ico**.

6. Nella finestra **Proprietà** scegliere la freccia accanto alla proprietà azione di **compilazione** .

7. Nell'elenco visualizzato scegliere **risorsa incorporata**.

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'elemento del progetto è ora presente nel progetto. Compilare il progetto per verificare che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** e scegliere **Compila**.

## <a name="create-a-visual-studio-item-template"></a>Creare un modello di elemento di Visual Studio
 Per consentire ad altri sviluppatori di usare l'elemento del progetto, è necessario creare un modello di progetto o un modello di elemento. Gli sviluppatori usano questi modelli in Visual Studio per creare un'istanza dell'elemento di progetto creando un nuovo progetto oppure aggiungendo un elemento a un progetto esistente. Per questa procedura dettagliata, usare il progetto ItemTemplate per configurare l'elemento del progetto.

#### <a name="to-create-the-item-template"></a>Per creare il modello di elemento

1. Eliminare il file di codice Class1 dal progetto ItemTemplate.

2. Nel progetto ItemTemplate aprire il file *ItemTemplate. vstemplate* .

3. Sostituire il contenuto del file con il codice XML seguente, quindi salvare e chiudere il file.

    > [!NOTE]
    > Il codice XML seguente è relativo a un modello di elemento di Visual C#. Se si sta creando un modello di elemento Visual Basic, sostituire il valore dell' `ProjectType` elemento con `VisualBasic` .

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

     Questo file definisce il contenuto e il comportamento del modello di elemento. Per altre informazioni sul contenuto di questo file, vedere [riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ItemTemplate** , scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

5. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il modello **file di testo** .

6. Nella casella **nome** immettere **CustomAction. spdata**e quindi scegliere il pulsante **Aggiungi** .

7. Aggiungere il seguente codice XML al file *CustomAction. spdata* e quindi salvare e chiudere il file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Questo file contiene informazioni sui file contenuti nell'elemento del progetto. L' `Type` attributo dell' `ProjectItem` elemento deve essere impostato sulla stessa stringa passata a nella definizione dell'elemento di <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> progetto (la `CustomActionProjectItemTypeProvider` classe creata in precedenza in questa procedura dettagliata). Per ulteriori informazioni sul contenuto dei file con *estensione spdata* , vedere [riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ItemTemplate** , scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

9. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il modello di **file XML** .

10. Nella casella **nome** immettere **Elements.xml**, quindi scegliere il pulsante **Aggiungi** .

11. Sostituire il contenuto del file di *Elements.xml* con il codice XML seguente, quindi salvare e chiudere il file.

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

     Questo file definisce un'azione personalizzata predefinita che crea una voce di menu nel menu **Azioni sito** del sito di SharePoint. Quando un utente sceglie la voce di menu, l'URL specificato nell' `UrlAction` elemento verrà aperto nel Web browser. Per ulteriori informazioni sugli elementi XML che è possibile utilizzare per definire un'azione personalizzata, vedere [definizioni delle azioni personalizzate](/sharepoint/dev/schema/custom-action-definition-schema).

12. Facoltativamente, aprire il file *ItemTemplate. ico* e modificarlo in modo che disponga di una progettazione che è possibile riconoscere. Questa icona verrà visualizzata accanto all'elemento del progetto nella finestra di dialogo **Aggiungi nuovo elemento** .

13. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ItemTemplate** , quindi scegliere **Scarica progetto**.

14. Aprire di nuovo il menu di scelta rapida per il progetto **ItemTemplate** , quindi scegliere **Modifica ItemTemplate. csproj** o **Modifica ItemTemplate. vbproj**.

15. Individuare l' `VSTemplate` elemento seguente nel file di progetto.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Sostituire questo `VSTemplate` elemento con il codice XML seguente, quindi salvare e chiudere il file.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` elemento specifica altre cartelle nel percorso in cui viene creato il modello di elemento quando si compila il progetto. Le cartelle specificate qui assicurano che il modello di elemento sarà disponibile solo quando i clienti aprono la finestra di dialogo **Aggiungi nuovo elemento** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

17. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ItemTemplate** , quindi scegliere **Ricarica progetto**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Creare un pacchetto VSIX per distribuire l'elemento di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il file **source. Extension. vsixmanifest** nel progetto CustomActionProjectItem, quindi scegliere **Apri**.

     Visual Studio apre il file nell'editor manifesto. Il file source. Extension. vsixmanifest è la base per il file Extension. vsixmanifest che tutti i pacchetti VSIX richiedono. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nella casella **nome prodotto** immettere **elemento progetto azione personalizzata**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **un elemento del progetto SharePoint che rappresenta un'azione personalizzata**.

5. Nella scheda **Asset** scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. ItemTemplate**.

    > [!NOTE]
    > Questo valore corrisponde all' `ItemTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di elemento di progetto. Per altre informazioni, vedere [elemento ItemTemplate (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** scegliere **ItemTemplate**, quindi scegliere il pulsante **OK** .

9. Nella scheda **Asset** scegliere di nuovo il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

10. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

12. Nell'elenco **progetto** scegliere **ProjectItemDefinition**.

13. Fare clic su **OK** .

14. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.

15. Assicurarsi che la cartella di output di compilazione per il progetto CustomActionProjectItem contenga il file CustomActionProjectItem. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il progetto CustomActionProjectItem.

## <a name="test-the-project-item"></a>Testare l'elemento del progetto
 A questo punto è possibile eseguire il test dell'elemento del progetto. Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi l'elemento del progetto di **azione personalizzata** in un progetto SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto SharePoint per verificare che l'azione personalizzata funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione CustomActionProjectItem.

2. Aprire il file di codice CustomAction, quindi aggiungere un punto di interruzione alla prima riga di codice nel `InitializeType` metodo.

3. Premere il tasto **F5** per avviare il debug.

     Visual Studio installa l'estensione nel progetto di azione Applicazione\locale\microsoft\visualstudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Per testare l'elemento del progetto in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Espandere **Visual C#** o **Visual Basic** (a seconda della lingua supportata dal modello di elemento), espandere **SharePoint**, quindi scegliere il nodo **2010** .

3. Nell'elenco dei modelli di progetto scegliere **progetto SharePoint 2010**.

4. Nella casella **nome** immettere **CustomActionTest**, quindi scegliere il pulsante **OK** .

5. Nella **procedura guidata di personalizzazione di SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug, quindi scegliere il pulsante **fine** .

6. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

7. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **2010** nel nodo **SharePoint** .

     Verificare che l'elemento **azione personalizzata** venga visualizzato nell'elenco degli elementi del progetto.

8. Scegliere l'elemento **azione personalizzata** , quindi scegliere il pulsante **Aggiungi** .

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il file di *Elements.xml* nell'editor.

9. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `InitializeType` metodo.

10. Premere il tasto **F5** per continuare a eseguire il debug del progetto.

11. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **CustomAction1** , quindi scegliere **Visualizza finestra di progettazione azione personalizzata**.

12. Verificare che venga visualizzata una finestra di messaggio, quindi scegliere il pulsante **OK** .

     È possibile utilizzare questo menu di scelta rapida per fornire opzioni o comandi aggiuntivi per gli sviluppatori, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata.

13. Sulla barra dei menu scegliere **Visualizza**  >  **output**.

     Verrà visualizzata la finestra **output** .

14. In **Esplora soluzioni**aprire il menu di scelta rapida per l'elemento **CustomAction1** , quindi modificarne il nome in **MyCustomAction**.

     Nella finestra **output** viene visualizzato un messaggio di conferma. Questo messaggio viene scritto dal <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> gestore eventi definito nella `CustomActionProjectItemTypeProvider` classe. È possibile gestire questo evento e altri eventi dell'elemento di progetto per implementare il comportamento personalizzato quando lo sviluppatore modifica l'elemento del progetto.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale di Visual Studio aprire il file *Elements.xml* figlio dell'elemento di progetto **MyCustomAction** .

2. Nel file di *Elements.xml* apportare le modifiche seguenti e quindi salvare il file:

    - Nell' `CustomAction` elemento impostare l' `Id` attributo su un GUID o su un'altra stringa univoca come illustrato nell'esempio seguente:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Nell' `CustomAction` elemento impostare l' `Title` attributo come illustrato nell'esempio seguente:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Nell' `CustomAction` elemento impostare l' `Description` attributo come illustrato nell'esempio seguente:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Nell' `UrlAction` elemento impostare l' `Url` attributo come illustrato nell'esempio seguente:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Premere **F5**.

     L'azione personalizzata viene assemblata e distribuita nel sito di SharePoint specificato nella proprietà **URL sito** del progetto. Il Web browser si apre alla pagina predefinita del sito.

    > [!NOTE]
    > Se viene visualizzata la finestra di dialogo **debug script disabilitato** , scegliere il pulsante **Sì** per continuare a eseguire il debug del progetto.

4. Nel menu **Azioni sito** scegliere Centro per **sviluppatori SharePoint**, verificare che il browser apra il sito Web https://docs.microsoft.com/sharepoint/dev/ e quindi chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test dell'elemento del progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere **elemento progetto azione personalizzata**, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si vuole disinstallare l'estensione.

4. Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

5. Chiudere l'istanza sperimentale di Visual Studio e l'istanza in cui è aperta la soluzione CustomActionProjectItem.

## <a name="next-steps"></a>Passaggi successivi
 Al termine di questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di elemento. Quando un utente aggiunge un elemento del progetto di azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione, ad esempio la posizione e l'URL a cui passare quando viene scelta l'azione, e aggiunge tali informazioni al file *Elements.xml* nel nuovo elemento del progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creare un elemento del progetto di azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di un'altra immagine &#40;editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)