---
title: Creare un elemento di progetto azione personalizzata con il modello di elemento, parte 1
titleSuffix: ''
description: Usando un modello di elemento, creare un elemento di progetto che può essere aggiunto a un progetto SharePoint per creare un'azione personalizzata in un SharePoint sito.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8662dfb53be04ef86e6587b26ff2897f869939bef2bbdea99c747e3d79145daa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385133"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 1
  È possibile estendere il SharePoint di progetto in Visual Studio creando tipi di elemento di progetto personalizzati. In questa procedura dettagliata si creerà un elemento di progetto che può essere aggiunto a un progetto SharePoint per creare un'azione personalizzata in un SharePoint sito. L'azione personalizzata aggiunge una voce di menu al menu **Azioni sito** del SharePoint sito.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di Visual Studio che definisce un nuovo tipo di SharePoint di progetto per un'azione personalizzata. Il nuovo tipo di elemento di progetto implementa diverse funzionalità personalizzate:

  - Menu di scelta rapida che funge da punto di partenza per attività aggiuntive correlate all'elemento di progetto, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata in Visual Studio.

  - Codice eseguito quando uno sviluppatore modifica determinate proprietà dell'elemento di progetto e del progetto che lo contiene.

  - Icona personalizzata visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.

- Creazione di un Visual Studio modello di elemento per l'elemento di progetto.

- Compilazione di un pacchetto Visual Studio Extension (VSIX) per distribuire il modello di elemento di progetto e l'assembly dell'estensione.

- Debug e test dell'elemento di progetto.

  Si tratta di una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento di progetto aggiungendo una procedura guidata al modello di elemento. Per altre informazioni, vedere [Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 2.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)

> [!NOTE]
> È possibile scaricare un esempio da [GitHub che](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) illustra come creare attività personalizzate per un flusso di lavoro.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.

- Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Extend the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Azioni personalizzate in SharePoint. Per altre informazioni, vedere [Azione personalizzata](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Modelli di elemento in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'SharePoint progetto.

- Un progetto modello di elemento. Questo progetto crea un modello di elemento che può essere usato per aggiungere l'elemento SharePoint progetto a un SharePoint progetto.

- Progetto di libreria di classi. Questo progetto implementa un'Visual Studio che definisce il comportamento dell'elemento SharePoint progetto.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

3. Nell'elenco nella parte superiore della finestra di dialogo Nuovo **Project** assicurarsi che sia selezionato **.NET Framework 4.5.**

4. Nella finestra **di dialogo Nuovo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il nodo **Estendibilità.**

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione dei prerequisiti più indietro in questo argomento.

5. Scegliere il **modello di Project VSIX.**

6. Nella casella **Nome** immettere **CustomActionProjectItem** e quindi scegliere **IL PULSANTE OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto CustomActionProjectItem** **Esplora soluzioni**.

#### <a name="to-create-the-item-template-project"></a>Per creare il progetto modello di elemento

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

2. Nell'elenco nella parte superiore della finestra di dialogo Nuovo **Project** assicurarsi che sia selezionato **.NET Framework 4.5.**

3. Nella finestra **di dialogo Nuovo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il nodo **Estendibilità.**

4. Nell'elenco dei modelli di progetto scegliere il modello di elemento **C#** **o Visual Basic modello di elemento.**

5. Nella casella **Nome** immettere **ItemTemplate** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ItemTemplate** alla soluzione.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

2. Nell'elenco nella parte superiore della finestra di dialogo Nuovo **Project** assicurarsi che sia selezionato **.NET Framework 4.5.**

3. Nella finestra di **dialogo Nuovo Project** espandere i nodi **Visual C#** o  **Visual Basic,** scegliere il nodo Windows e quindi scegliere il modello **di** progetto Libreria di classi.

4. Nella casella **Nome** immettere **ProjectItemDefinition** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ProjectItemDefinition** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per definire il tipo SharePoint elemento di progetto, è necessario aggiungere file di codice e riferimenti all'assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ProjectItemDefinition,** scegliere **Aggiungi** e quindi **Nuovo elemento.**

2. Nell'elenco degli elementi di progetto scegliere **File di codice**.

3. Nella casella **Nome** immettere il nome **CustomAction** con l'estensione di file appropriata e quindi scegliere il **pulsante** Aggiungi.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ProjectItemDefinition** e quindi scegliere **Aggiungi riferimento**.

5. Nella finestra di dialogo Gestione riferimenti **- ProjectItemDefinition** scegliere il **nodo Assembly** e quindi scegliere il **nodo Framework.**

6. Selezionare la casella di controllo accanto a ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Scegliere il **nodo Estensioni,** selezionare la casella di controllo accanto all'assembly Microsoft.VisualStudio.Sharepoint e quindi scegliere **OK.**

## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di SharePoint progetto
 Creare una classe che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di elemento di progetto.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di SharePoint progetto

1. Nel progetto ProjectItemDefinition aprire il file di codice CustomAction.

2. Sostituire il codice in questo file con il codice seguente.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb" id="Snippet1":::

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Creare un'icona per l'elemento di progetto in Esplora soluzioni
 Quando si crea un elemento SharePoint progetto personalizzato, è possibile associare un'immagine (un'icona o una bitmap) all'elemento di progetto. Questa immagine viene visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.

 Nella procedura seguente si crea un'icona per l'elemento di progetto e si incorpora l'icona nell'assembly di estensione. A questa icona fa riferimento <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> la classe della classe creata in `CustomActionProjectItemTypeProvider` precedenza.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Per creare un'icona personalizzata per l'elemento di progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ProjectItemDefinition,** scegliere **Aggiungi** e quindi **Nuovo elemento.**

2. Nell'elenco degli elementi del progetto scegliere **l'elemento File** icona.

    > [!NOTE]
    > Nei Visual Basic, è necessario scegliere il **nodo Generale** per visualizzare l'elemento **File icona.**

3. Nella casella **Nome** immettere **CustomAction_SolutionExplorer.ico** e quindi scegliere il **pulsante** Aggiungi.

     La nuova icona viene aperta **nell'editor di immagini**.

4. Modificare la versione 16x16 del file dell'icona in modo che abbia una progettazione che è possibile riconoscere e quindi salvare il file dell'icona.

5. In **Esplora soluzioni** scegliere **CustomAction_SolutionExplorer.ico**.

6. Nella finestra **Proprietà** scegliere la freccia accanto alla **proprietà Azione di** compilazione.

7. Nell'elenco visualizzato scegliere **Risorsa incorporata**.

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'elemento di progetto si trova ora nel progetto. Compilare il progetto per verificare che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Aprire il menu di scelta rapida per **il progetto ProjectItemDefinition** e scegliere **Compila.**

## <a name="create-a-visual-studio-item-template"></a>Creare un modello Visual Studio elemento personalizzato
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, è necessario creare un modello di progetto o un modello di elemento. Gli sviluppatori usano questi modelli Visual Studio creare un'istanza dell'elemento di progetto creando un nuovo progetto o aggiungendo un elemento a un progetto esistente. Per questa procedura dettagliata, usare il progetto ItemTemplate per configurare l'elemento di progetto.

#### <a name="to-create-the-item-template"></a>Per creare il modello di elemento

1. Eliminare il file di codice Class1 dal progetto ItemTemplate.

2. Nel progetto ItemTemplate aprire il file *ItemTemplate.vstemplate.*

3. Sostituire il contenuto del file con il codice XML seguente, quindi salvare e chiudere il file.

    > [!NOTE]
    > Il codice XML seguente è per un modello di elemento di Visual C#. Se si sta creando un modello Visual Basic elemento personalizzato, sostituire il valore `ProjectType` dell'elemento con `VisualBasic` .

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

     Questo file definisce il contenuto e il comportamento del modello di elemento. Per altre informazioni sul contenuto di questo file, vedere riferimento Visual Studio [schema del modello.](../extensibility/visual-studio-template-schema-reference.md)

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ItemTemplate,** scegliere **Aggiungi** e quindi **nuovo elemento.**

5. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il modello File **di** testo.

6. Nella casella **Nome** immettere **CustomAction.spdata** e quindi scegliere il **pulsante** Aggiungi.

7. Aggiungere il codice XML seguente al file *CustomAction.spdata* e quindi salvare e chiudere il file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Questo file contiene informazioni sui file contenuti nell'elemento di progetto. L'attributo dell'elemento deve essere impostato sulla stessa stringa passata a nella definizione dell'elemento di progetto (la classe creata in precedenza `Type` `ProjectItem` in questa procedura <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> `CustomActionProjectItemTypeProvider` dettagliata). Per altre informazioni sul contenuto dei file con estensione *spdata,* vedere riferimento SharePoint [dello schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md).

8. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ItemTemplate,** scegliere **Aggiungi** e quindi **nuovo elemento.**

9. Nella finestra **di dialogo Aggiungi** nuovo elemento scegliere il modello **File** XML.

10. Nella casella **Nome** immettere **Elements.xml** e quindi scegliere il **pulsante** Aggiungi.

11. Sostituire il contenuto del *fileElements.xml* con il codice XML seguente, quindi salvare e chiudere il file.

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

     Questo file definisce un'azione personalizzata predefinita che crea una voce di menu nel menu **Azioni** sito del SharePoint sito. Quando un utente sceglie la voce di menu, l'URL specificato `UrlAction` nell'elemento viene aperto nel Web browser. Per altre informazioni sugli elementi XML che è possibile usare per definire un'azione personalizzata, vedere [Definizioni di azioni personalizzate.](/sharepoint/dev/schema/custom-action-definition-schema)

12. Facoltativamente, aprire il file *ItemTemplate.ico* e modificarlo in modo che abbia una progettazione che è possibile riconoscere. Questa icona verrà visualizzata accanto all'elemento di progetto nella **finestra di** dialogo Aggiungi nuovo elemento .

13. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **ItemTemplate** e quindi scegliere **Scarica** Project .

14. Aprire di nuovo il menu di scelta rapida per il progetto **ItemTemplate** e quindi scegliere **Modifica ItemTemplate.csproj** o **Modifica ItemTemplate.vbproj.**

15. Individuare `VSTemplate` l'elemento seguente nel file di progetto.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Sostituire questo `VSTemplate` elemento con il codice XML seguente, quindi salvare e chiudere il file.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L'elemento specifica cartelle aggiuntive nel percorso in cui viene creato il modello `OutputSubPath` di elemento quando si compila il progetto. Le cartelle specificate qui assicurano che il modello  di elemento sia disponibile solo quando i clienti aprono la finestra di dialogo Aggiungi nuovo elemento, espandono il nodo **SharePoint** e quindi scelgono il **nodo 2010.**

17. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ItemTemplate** e quindi scegliere **Ricarica Project**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Creare un pacchetto VSIX per distribuire l'elemento di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare prima di tutto il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il file **source.extension.vsixmanifest** nel progetto CustomActionProjectItem e quindi scegliere **Apri.**

     Visual Studio apre il file nell'editor manifesto. Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere **Custom Action (Azione personalizzata) Project Item (Elemento).**

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **un SharePoint progetto che rappresenta un'azione personalizzata.**

5. Nella **scheda Asset scegliere** il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.ItemTemplate.**

    > [!NOTE]
    > Questo valore corrisponde `ItemTemplate` all'elemento nel file extension.vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di elemento di progetto. Per altre informazioni, vedere [Elemento ItemTemplate (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))

7. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

8. **Nell'Project,** scegliere **ItemTemplate** e quindi scegliere **il pulsante OK.**

9. Nella **scheda Asset scegliere** di nuovo **il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

10. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

11. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

12. **Nell'Project** progetto scegliere **ProjectItemDefinition.**

13. Fare clic su **OK** .

14. Sulla barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che  >  il progetto venga compilato senza errori.

15. Assicurarsi che la cartella dell'output di compilazione per il progetto CustomActionProjectItem contenga il file CustomActionProjectItem.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il progetto CustomActionProjectItem.

## <a name="test-the-project-item"></a>Testare l'elemento di progetto
 A questo punto è possibile testare l'elemento di progetto. Per prima cosa, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi **l'elemento di progetto** Azione personalizzata in un progetto SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il SharePoint per verificare che l'azione personalizzata funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.

2. Aprire il file di codice CustomAction e quindi aggiungere un punto di interruzione alla prima riga di codice nel `InitializeType` metodo .

3. Premere **F5 per** avviare il debug.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento di progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Per testare l'elemento di progetto in Visual Studio

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **File**  >    >  **Nuovo Project**.

2. Espandere **Visual C#** **o Visual Basic** (a seconda del linguaggio che supporta il modello di elemento), espandere SharePoint e quindi scegliere il nodo **2010.** 

3. Nell'elenco dei modelli di progetto **scegliere SharePoint 2010 Project**.

4. Nella casella **Nome** immettere **CustomActionTest** e quindi scegliere **il pulsante OK.**

5. Nella **Personalizzazione guidata SharePoint,** immettere l'URL del sito che si vuole usare per il debug e quindi scegliere il **pulsante** Fine.

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi** e quindi **nuovo elemento.**

7. Nella finestra **di dialogo Aggiungi** nuovo elemento scegliere il nodo **2010** sotto il **SharePoint.**

     Verificare che **l'elemento Azione** personalizzata sia visualizzato nell'elenco degli elementi del progetto.

8. Scegliere **l'elemento Azione** personalizzata e quindi scegliere **il pulsante** Aggiungi.

     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il file *Elements.xml* nell'editor.

9. Verificare che il codice nell'altra istanza di Visual Studio si arresti in corrispondenza del punto di interruzione impostato in precedenza nel `InitializeType` metodo .

10. Premere **F5 per** continuare a eseguire il debug del progetto.

11. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **CustomAction1** e quindi scegliere **Visualizza Progettazione azioni personalizzate.**

12. Verificare che venga visualizzata una finestra di messaggio e quindi scegliere **il pulsante OK.**

     È possibile utilizzare questo menu di scelta rapida per fornire opzioni o comandi aggiuntivi per gli sviluppatori, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata.

13. Sulla barra dei menu scegliere **Visualizza**  >  **output.**

     Verrà **visualizzata la finestra Output.**

14. In **Esplora soluzioni** aprire il menu di scelta rapida per l'elemento **CustomAction1** e quindi modificarne il nome in **MyCustomAction**.

     Nella finestra **Output** viene visualizzato un messaggio di conferma. Questo messaggio viene scritto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> dal gestore eventi definito nella classe `CustomActionProjectItemTypeProvider` . È possibile gestire questo evento e altri eventi dell'elemento di progetto per implementare il comportamento personalizzato quando lo sviluppatore modifica l'elemento di progetto.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint

1. Nell'istanza sperimentale Visual Studio aprire il file *Elements.xml* figlio dell'elemento di progetto **MyCustomAction.**

2. Nel file *Elements.xml* apportare le modifiche seguenti e quindi salvare il file:

    - `CustomAction`Nell'elemento impostare `Id` l'attributo su un GUID o su un'altra stringa univoca, come illustrato nell'esempio seguente:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - `CustomAction`Nell'elemento impostare `Title` l'attributo come illustrato nell'esempio seguente:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - `CustomAction`Nell'elemento impostare `Description` l'attributo come illustrato nell'esempio seguente:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - `UrlAction`Nell'elemento impostare `Url` l'attributo come illustrato nell'esempio seguente:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Premere **F5**.

     L'azione personalizzata viene in pacchetto e distribuita nel sito SharePoint specificato nella proprietà **URL** sito del progetto. Il Web browser apre la pagina predefinita di questo sito.

    > [!NOTE]
    > Se viene **visualizzata la finestra di** dialogo Debug script disabilitato , scegliere il **pulsante** Sì per continuare il debug del progetto.

4. Nel menu **Azioni sito** scegliere SharePoint **Developer Center,** verificare che il browser apra il sito Web https://docs.microsoft.com/sharepoint/dev/ e quindi chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il test dell'elemento di progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **Strumenti**  >  **Estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Azione personalizzata Project Elemento**, quindi scegliere il pulsante **Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere il **pulsante Sì** per confermare che si vuole disinstallare l'estensione.

4. Scegliere il **pulsante Riavvia** ora per completare la disinstallazione.

5. Chiudere sia l'istanza sperimentale Visual Studio che l'istanza in cui è aperta la soluzione CustomActionProjectItem.

## <a name="next-steps"></a>Passaggi successivi
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di elemento. Quando un utente aggiunge un elemento di progetto Azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione (ad esempio il percorso e l'URL a cui passare quando viene scelta l'azione) e aggiunge queste informazioni al file *Elements.xml* nel nuovo elemento di progetto. Per altre informazioni, vedere [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o di un'altra immagine &#40;editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)