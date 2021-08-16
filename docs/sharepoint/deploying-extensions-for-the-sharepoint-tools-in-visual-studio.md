---
title: Distribuzione di estensioni per gli strumenti SharePoint in Visual Studio | Microsoft Docs
description: Distribuire estensioni per SharePoint strumenti in Visual Studio. Usare Visual Studio di estensione (VSIX) per creare pacchetti VSIX.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ad4645a6c23d13642bf7e417ca552f1dc196dad1a0e379eafefa9f179a45c8ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121269223"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Distribuire estensioni per gli strumenti SharePoint in Visual Studio

Per distribuire un'estensione degli strumenti di SharePoint, creare un pacchetto di estensione (VSIX) contenente l'assembly dell'estensione e qualsiasi altro file che si [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] desidera distribuire con l'estensione. Un pacchetto VSIX è un file compresso che segue lo standard Open Packaging Conventions (OPC). I pacchetti VSIX hanno *l'estensione vsix.*

Dopo aver creato un pacchetto VSIX, altri utenti possono eseguire il file con estensione vsix per installare l'estensione. Quando un utente installa l'estensione, tutti i file vengono installati nella cartella %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Per distribuire l'estensione, è possibile caricare il pacchetto VSIX nel sito Web marketplace di [Visual Studio](https://marketplace.visualstudio.com/) oppure distribuire il pacchetto ai clienti con altri mezzi, ad esempio ospitando il pacchetto in una condivisione di rete o in un altro sito Web.

Per altre informazioni sulla creazione di pacchetti VSIX e sulla loro [distribuzione in Visual Studio Marketplace,](https://marketplace.visualstudio.com/)vedere [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 È possibile creare un pacchetto VSIX usando il modello **Project VSIX** in Visual Studio oppure creare un pacchetto VSIX manualmente.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Usare progetti VSIX per creare pacchetti VSIX

È possibile usare il **modello di Project VSIX** fornito da Visual Studio SDK per creare pacchetti VSIX per SharePoint tools. L'uso di un progetto VSIX offre diversi vantaggi rispetto alla creazione manuale di un pacchetto VSIX:

- Visual Studio genera automaticamente il pacchetto VSIX quando si compila il progetto. Le attività come l'aggiunta dei file di distribuzione al pacchetto e la creazione del file [Content_Types].xml per il pacchetto vengono eseguite per l'utente.

- È possibile configurare il progetto VSIX in modo da includere l'output di compilazione del progetto di estensione e altri file, ad esempio modelli di progetto e modelli di elemento, nel pacchetto VSIX.

Per altre informazioni sull'uso di un progetto VSIX, vedere [VsIX Project Template](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizzare i progetti

Per impostazione predefinita, i progetti VSIX generano solo pacchetti VSIX, non assembly. Di conseguenza, in genere non si implementa un'SharePoint strumenti di distribuzione in un progetto VSIX. In genere si lavora con almeno due progetti:

- Un progetto VSIX.

- Progetto di libreria di classi che implementa l'estensione.

È anche possibile usare progetti aggiuntivi per determinati tipi di estensioni:

- Un progetto di libreria di classi che implementa SharePoint comandi usati dall'estensione. Per una procedura dettagliata che illustra questo scenario, vedere [Walkthrough: Extend Esplora server to display web parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Un modello di elemento o Project che crea un modello di elemento o un modello di progetto, se l'estensione definisce un nuovo tipo di SharePoint progetto. Per una procedura dettagliata che illustra questo scenario, vedere Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di [elemento, parte 1.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- Progetto di libreria di classi che implementa una procedura guidata personalizzata per un modello di elemento o un modello di progetto, se l'estensione include un modello. Per una procedura dettagliata che illustra questo scenario, vedere Procedura dettagliata: Creare un elemento di progetto azione personalizzata con [un modello di elemento, parte 2.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)

Se si includono tutti i progetti nella stessa soluzione Visual Studio, è possibile modificare il file source.extension.vsixmanifest nel progetto VSIX per includere l'output di compilazione dei progetti di libreria di classi.

### <a name="edit-the-vsix-manifest"></a>Modificare il manifesto VSIX

È necessario modificare il file source.extension.vsixmanifest nel progetto VSIX per includere le voci per tutti gli elementi da includere nell'estensione. Quando si apre il file source.extension.vsixmanifest dal relativo menu di scelta rapida, il file viene visualizzato in una finestra di progettazione che fornisce un'interfaccia utente per la modifica del codice XML nel file. Per altre informazioni, vedere [Progettazione manifesto VSIX.](../extensibility/vsix-manifest-designer.md)

È necessario aggiungere voci al file source.extension.vsixmanifest per gli elementi seguenti:

- Assembly dell'estensione.

- Assembly che implementa qualsiasi SharePoint comandi usati dall'estensione.

- Tutti i modelli di progetto o i modelli di elemento associati all'estensione.

- Procedura guidata personalizzata per un modello associato all'estensione.

Le procedure seguenti descrivono come aggiungere voci al file con estensione vsixmanifest per ognuno di questi elementi.

#### <a name="to-include-the-extension-assembly"></a>Per includere l'assembly dell'estensione

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere **Apri.**

     Il file viene aperto nella finestra di progettazione

2. Nella **scheda Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

4. **Nell'elenco** Origine eseguire una delle operazioni seguenti:

    - Se l'assembly dell'estensione viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere Un progetto **nella soluzione corrente.** **Nell'Project** selezionare il nome del progetto.

    - Se l'assembly dell'estensione è incluso come file nel progetto, scegliere **File nel file system**. **Nell'elenco Percorso** immettere il percorso completo del file  di assembly dell'estensione oppure usare il pulsante Sfoglia per individuare e scegliere il file di assembly.

5. Fare clic su **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Per includere un assembly SharePoint comando

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere il **pulsante** Apri.

     Il file viene aperto nella finestra di progettazione.

2. Nella **sezione Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. Nella casella **Tipo** immettere **SharePoint. Commands.v4**.

4. **Nell'elenco** Origine eseguire una delle operazioni seguenti:

    - Se l'assembly dei comandi viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere Un progetto **nella soluzione corrente.** **Nell'Project** selezionare il nome del progetto.

    - Se l'assembly dei comandi è incluso come file nel progetto, scegliere **File nel file system**. **Nell'elenco Percorso** immettere il percorso completo del file  di assembly dell'estensione oppure usare il pulsante Sfoglia per individuare e scegliere il file di assembly.

5. Fare clic su **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Per includere un modello creato

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere il **pulsante** Apri.

     Il file viene aperto nella finestra di progettazione.

2. Nella **sezione Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate.**

4. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

5. **Nell'Project** selezionare il nome del progetto e quindi scegliere **il pulsante OK.**

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto modello Project o modello di elemento e quindi scegliere **Scarica** Project .

7. Aprire di nuovo il menu di scelta rapida per il nodo del progetto e quindi scegliere Edit _YourTemplateProjectName_**.csproj** o **Edit**_YourTemplateProjectName_**.vbproj**.

8. Individuare `VSTemplate` l'elemento seguente nel file di progetto.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Sostituisci l'elemento con il codice XML seguente.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L'elemento specifica cartelle aggiuntive nel percorso in cui viene creato il modello `OutputSubPath` di progetto quando si compila il progetto. Le cartelle specificate qui assicurano che il modello di elemento sia disponibile solo quando i clienti aprono la finestra di dialogo Aggiungi nuovo **Project,** espandono il nodo **SharePoint** e quindi scelgono il **nodo 2010.**

10. Salvare e chiudere il file.

11. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto modello Project o modello di elemento e quindi scegliere **Ricarica** Project .

#### <a name="to-include-a-template-that-you-create-manually"></a>Per includere un modello creato manualmente

1. Nel progetto VSIX aggiungere una nuova cartella al progetto per contenere il modello.

2. In questa nuova cartella creare le sottocartelle seguenti e quindi aggiungere il file modello (.zip) alla cartella *LOCALE ID.*

     *Cartella Modello*

     **SharePoint**

     **SharePoint14**

     *ID locale*

     *NomeModello.zip*

     Ad esempio, se si dispone di un modello di elemento denominato ContosoCustomAction.zip che supporta le impostazioni locali della lingua inglese (Stati Uniti), il percorso completo potrebbe *essereItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. In **Esplora soluzioni** scegliere il file modello (*YourTemplateName*.zip).

4. Nella finestra **Proprietà** impostare la proprietà **Azione di** compilazione su **Contenuto**.

5. Aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere **Apri.**

     Il file viene aperto nella finestra di progettazione.

6. Nella **sezione Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

7. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.ItemTemplate** o **Microsoft.VisualStudio.ProjectTemplate.**

8. **Nell'elenco Origine** scegliere **File nel file system.**

9. Nel campo **Percorso** immettere il percorso completo dell'assembly, ad esempio *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, oppure usare il pulsante Sfoglia per individuare e scegliere l'assembly, quindi scegliere **il pulsante OK.** 

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Per includere una procedura guidata per un modello di progetto o un modello di elemento

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere **Apri.**

     Il file viene aperto nella finestra di progettazione.

2. Nella **sezione Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.Assembly**.

4. **Nell'elenco** Origine eseguire una delle operazioni seguenti:

    - Se l'assembly della procedura guidata viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere Un progetto **nella soluzione corrente.** **Nell'Project** selezionare il nome del progetto.

    - Se l'assembly della procedura guidata è incluso come file nel progetto, scegliere **File nel file system**. Nel campo **Percorso** immettere il percorso completo del file di assembly oppure usare il **pulsante** Sfoglia per individuare e scegliere l'assembly.

5. Fare clic su **OK** .

### <a name="related-walkthroughs"></a>Procedure dettagliate correlate

Nella tabella seguente sono elencate le procedure dettagliate che illustrano come usare un progetto VSIX per distribuire diversi tipi di SharePoint estensioni degli strumenti.

|Tipo di estensione|Procedure dettagliate correlate|
|--------------------|--------------------------|
|Estensione che include solo l'assembly dell'estensione|[Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procedura dettagliata: Creare un'SharePoint Project personalizzata](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procedura dettagliata: Chiamare nel modello a oggetti SharePoint client in un'Esplora server predefinita](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Estensione che include i SharePoint seguenti|[Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per SharePoint progetti](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Estensione che include un modello Visual Studio personalizzato|[Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Estensione che include una creazione guidata modello|[Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Creare pacchetti VSIX manualmente

Se si vuole creare manualmente il pacchetto VSIX per l'estensione SharePoint Tools, seguire questa procedura:

1. Creare il file extension.vsixmanifest e il file [Content_Types].xml in una nuova cartella. Per altre informazioni, vedere [Anatomia di un pacchetto VSIX.](../extensibility/anatomy-of-a-vsix-package.md)

2. In Windows fare clic con il pulsante destro del mouse sulla cartella contenente i due file XML, scegliere Invia ae quindi fare clic su Cartella compressa. Rinominare il file ZIP risultante in Nomefile.vsix, dove Nomefile è il nome del file ridistribuibile che installa il pacchetto.

3. Aggiungere l'assembly dell'estensione al pacchetto VSIX. Se l'estensione include un SharePoint, aggiungere anche l'assembly che implementa il comando SharePoint al pacchetto VSIX.

4. Modificare il file extension.vsixmanifest:

    - Aggiungere un elemento sotto l'elemento e quindi impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa l'estensione `Microsoft.VisualStudio.MefComponent` `Assets` nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

    - Se l'estensione include un SharePoint che chiama nel modello a oggetti del server per SharePoint, aggiungere un `Microsoft.VisualStudio.Assembly` elemento sotto `Assets` l'elemento . Impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa SharePoint comando nel pacchetto VSIX. Per altre informazioni, vedere [Elemento Asset (schema VSX).](/previous-versions/dd393737(v=vs.110))

    - Se l'estensione include un modello di progetto o un modello di elemento, aggiungere un `ProjectTemplate` `ItemTemplate` elemento o sotto `Assets` l'elemento . Impostare il valore del nuovo elemento sul percorso relativo della cartella che contiene il modello nel pacchetto VSIX. Per altre informazioni, vedere [Elemento ProjectTemplate (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) e [Elemento ItemTemplate (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))

    - Se l'estensione include una procedura guidata personalizzata per un modello di progetto o un modello di elemento, aggiungere `Assembly` un elemento sotto `Assets` l'elemento . Impostare il valore del nuovo elemento sul percorso relativo dell'assembly nel pacchetto VSIX, quindi impostare l'attributo sul nome completo dell'assembly,inclusi versione, impostazioni cultura e token di `AssemblyName` chiave pubblica. Per altre informazioni, vedere [Elemento Dependency (schema VSX).](/previous-versions/dd393682(v=vs.110))

### <a name="example"></a>Esempio

L'esempio seguente mostra il contenuto di un file extension.vsixmanifest per un'SharePoint tools. L'estensione viene implementata in un assembly denominato Contoso.ProjectExtension.dll. L'estensione include SharePoint un assembly di comandi denominato Contoso.ExtensionCommands.dll e un modello di elemento in una cartella denominata **ItemTemplates** nel pacchetto VSIX. Questo esempio presuppone che entrambi gli assembly siano nella stessa cartella del file extension.vsixmanifest nel pacchetto VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Vedi anche

- [Estendere il SharePoint del progetto](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Eseguire il debug delle estensioni per SharePoint strumenti in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)