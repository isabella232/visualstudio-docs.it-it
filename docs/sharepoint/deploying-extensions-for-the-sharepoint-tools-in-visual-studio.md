---
title: Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3cbd581da1e2a081636c4f4cf7885241c15eff97
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876265"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Distribuire le estensioni per gli strumenti di SharePoint in Visual Studio

Per distribuire un'estensione degli strumenti di SharePoint, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) che contiene l'assembly dell'estensione e qualsiasi altro file che si desidera distribuire con l'estensione. Un pacchetto VSIX non è un file compresso che segue lo standard Open Packaging Conventions (OPC). Pacchetti VSIX hanno le *VSIX* estensione.

Dopo aver creato un pacchetto VSIX, altri utenti possono eseguire il file VSIX per installare l'estensione. Quando un utente installa l'estensione, tutti i file vengono installati nella cartella %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Per distribuire l'estensione, è possibile caricare il pacchetto VSIX per la [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web, oppure è possibile distribuire il pacchetto ai tuoi clienti con altri mezzi, ad esempio che ospita il pacchetto in una condivisione di rete o un altro sito Web.

Per altre informazioni sulla creazione di pacchetti VSIX e la distribuzione per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847), vedere [spedizione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 È possibile creare un pacchetto VSIX usando il **progetto VSIX** modello in Visual Studio, oppure è possibile creare manualmente un pacchetto VSIX.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Usare i progetti VSIX per creare pacchetti VSIX

È possibile usare la **progetto VSIX** modello fornito da Visual Studio SDK per creare pacchetti VSIX per estensioni degli strumenti di SharePoint. Utilizzo di un progetto VSIX offre diversi vantaggi rispetto creazione manuale di un pacchetto VSIX:

-   Quando si compila il progetto, Visual Studio genera automaticamente il pacchetto VSIX. Le attività, ad esempio aggiungendo i file di distribuzione per il pacchetto e creando il file [Content_Types] XML per il pacchetto vengono eseguite automaticamente.

-   È possibile configurare il progetto VSIX per includere l'output di compilazione del progetto di estensione e altri file, ad esempio i modelli di progetto e modelli di elemento, nel pacchetto VSIX.

Per altre informazioni sull'uso di un progetto VSIX, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizzare i progetti

Per impostazione predefinita, solo i progetti VSIX generano pacchetti VSIX, non gli assembly. Pertanto, in genere non si implementa un'estensione degli strumenti di SharePoint in un progetto VSIX. Generalmente si lavora con almeno due progetti:

-   Un progetto VSIX.

-   Un progetto libreria di classi che implementa l'estensione.

È anche possibile lavorare con i progetti aggiuntivi per determinati tipi di estensioni:

-   Un progetto libreria di classi che implementa i comandi di SharePoint che vengono utilizzati dall'estensione. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Un progetto di modello di elemento o modello di progetto che crea un modello di elemento o un modello di progetto, se l'estensione consente di definire un nuovo tipo di elemento di progetto SharePoint. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Un progetto libreria di classi che implementa una procedura guidata personalizzata per un modello di elemento o un modello di progetto, se l'estensione include un modello. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Se si includono tutti i progetti nella stessa soluzione di Visual Studio, è possibile modificare il file vsixmanifest nel progetto VSIX per includere l'output di compilazione di progetti libreria di classi.

### <a name="edit-the-vsix-manifest"></a>Modificare il manifesto VSIX

È necessario modificare il file vsixmanifest nel progetto VSIX per includere le voci per tutti gli elementi che si desidera includere nella propria estensione. Quando si apre il file vsixmanifest dal relativo menu di scelta rapida, il file viene visualizzato in una finestra di progettazione che fornisce un'interfaccia utente per modificare il codice XML nel file. Per altre informazioni, vedere [progettazione del manifesto VSIX](../extensibility/vsix-manifest-designer.md).

È necessario aggiungere le voci del file vsixmanifest per gli elementi seguenti:

-   L'assembly dell'estensione.

-   L'assembly che implementa i comandi di SharePoint che vengono utilizzati dall'estensione.

-   Tutti i modelli di progetto o modelli di elementi associati con l'estensione.

-   Una procedura guidata personalizzata per un modello che è associato all'estensione.

Le procedure seguenti descrivono come aggiungere voci per il file con estensione vsixmanifest per ognuno di questi elementi.

#### <a name="to-include-the-extension-assembly"></a>Per includere l'assembly dell'estensione

1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aprire**.

     Il file viene aperto nella finestra di progettazione

2.  Nel **asset** della scheda dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

3.  Nel **tipo** casella di riepilogo **MEFComponent**.

4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:

    -   Se l'assembly dell'estensione viene compilata da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** scegliere il nome del progetto.

    -   Se l'assembly dell'estensione è inclusa in un file nel progetto, scegliere **File in filesystem**. Nel **percorso** elenco, immettere il percorso completo al file di assembly di estensione o utilizzare il **Sfoglia** per individuare e selezionare il file di assembly.

5.  Fare clic sul pulsante **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Per includere un assembly di comando di SharePoint

1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere il **aprire** pulsante.

     Il file viene aperto nella finestra di progettazione.

2.  Nel **Assets** sezione dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

3.  Nel **tipo** casella, immettere **v4**.

4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:

    -   Se l'assembly del comando viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** scegliere il nome del progetto.

    -   Se l'assembly del comando è incluso un file nel progetto, scegliere **File in filesystem**. Nel **percorso** elenco, immettere il percorso completo al file di assembly di estensione o utilizzare il **Sfoglia** per individuare e selezionare il file di assembly.

5.  Fare clic sul pulsante **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Per includere un modello che si crea

1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere il **aprire** pulsante.

     Il file viene aperto nella finestra di progettazione.

2.  Nel **Assets** sezione dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

3.  Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.ProjectTemplate** oppure **Microsoft.VisualStudio.ItemTemplate**.

4.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

5.  Nel **Project** elenco, scegliere il nome del progetto e quindi scegliere il **OK** pulsante.

6.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto modello di progetto o modello di elemento e quindi scegliere **Scarica progetto**.

7.  Aprire di nuovo il menu di scelta rapida per il nodo del progetto e quindi scegliere **Edit**_NomeProgettoModello_**csproj** oppure **Edit**  _NomeProgettoModello_**vbproj**.

8.  Individuare la seguente `VSTemplate` elemento nel file di progetto.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Sostituire l'elemento con il codice XML seguente.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Il `OutputSubPath` elemento specifica cartelle aggiuntive nel percorso in cui il modello di progetto viene creato quando si compila il progetto. Le cartelle specificate in questo caso assicurarsi che il modello di elemento sarà disponibile solo quando i clienti aprire il **Aggiungi nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.

10. Salvare e chiudere il file.

11. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto di modello di progetto o modello di elemento e quindi scegliere **Ricarica progetto**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Per includere un modello creato manualmente

1.  Nel progetto VSIX, aggiungere una nuova cartella al progetto per includere il modello.

2.  In questa nuova cartella, creare le sottocartelle seguenti e quindi aggiungere il file di modello (con estensione zip) per il *ID delle impostazioni locali* cartella.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID delle impostazioni locali*

     *YourTemplateName*.zip

     Ad esempio, se si dispone di un modello di elemento denominato ContosoCustomAction. zip che supportano le impostazioni locali inglese (Stati Uniti), potrebbe essere il percorso completo *Itemtemplates\sharepoint\sharepoint14\1033\contosocustomaction.zip*.

3.  Nelle **Esplora soluzioni**, scegliere il file di modello (*YourTemplateName*con estensione zip).

4.  Nel **le proprietà** impostare nella finestra di **azione di compilazione** proprietà **contenuto**.

5.  Aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aperto**.

     Il file viene aperto nella finestra di progettazione.

6.  Nel **Assets** sezione dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

7.  Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.ItemTemplate** oppure **Microsoft.VisualStudio.ProjectTemplate**.

8.  Nel **origine** casella di riepilogo **File in filesystem**.

9. Nel **percorso** immettere il percorso completo dell'assembly (ad esempio, *Itemtemplates\sharepoint\sharepoint14\1033\contosocustomaction.zip.*, o usare il **Sfoglia**per individuare e selezionare l'assembly e quindi scegliere il **OK** pulsante.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Per includere una procedura guidata per un modello di progetto o un modello di elemento

1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aprire**.

     Il file viene aperto nella finestra di progettazione.

2.  Nel **Assets** sezione dell'editor, scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

3.  Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.Assembly**.

4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:

    -   Se l'assembly della procedura guidata viene compilata da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** scegliere il nome del progetto.

    -   Se l'assembly della procedura guidata è incluso un file nel progetto, scegliere **File in filesystem**. Nel **percorso** campo, immettere il percorso completo del file di assembly o utilizzare il **Sfoglia** per individuare e selezionare l'assembly.

5.  Fare clic sul pulsante **OK** .

### <a name="related-walkthroughs"></a>Procedure dettagliate correlate

Nella tabella seguente sono elencate procedure dettagliate che illustrano come usare un progetto VSIX per distribuire diversi tipi di estensioni degli strumenti di SharePoint.

|Tipo di estensione|Procedure dettagliate correlate|
|--------------------|--------------------------|
|Un'estensione che include solo l'assembly dell'estensione|[Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procedura dettagliata: Creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procedura dettagliata: Chiamare il modello a oggetti client SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Un'estensione che include i comandi di SharePoint|[Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Un'estensione che include un modello di Visual Studio|[Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Un'estensione che include una procedura guidata modello|[Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Creare manualmente i pacchetti VSIX

Se si vuole creare manualmente il pacchetto VSIX dell'estensione strumenti di SharePoint, eseguire la procedura seguente:

1.  Creare il file extension vsixmanifest e il file [Content_Types] XML in una nuova cartella. Per altre informazioni, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2.  In Windows Explorer, fare clic sulla cartella che contiene i due file XML, fare clic su Invia a e quindi fare clic sulla cartella compressa. Rinominare il file ZIP risultante in Filename.vsix, in cui nomefile è il nome del file ridistribuibile che installa il pacchetto.

3.  Aggiungere l'assembly di estensioni per il pacchetto VSIX. Se l'estensione include un comando di SharePoint, è necessario aggiungere anche l'assembly che implementa il comando di SharePoint per il pacchetto VSIX.

4.  Modificare il file extension vsixmanifest:

    -   Aggiungere un `Microsoft.VisualStudio.MefComponent` elemento sotto il `Assets` elemento e quindi impostare il valore del nuovo elemento al percorso relativo dell'assembly che implementa l'estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    -   Se l'estensione include un comando di SharePoint che effettua chiamate nel modello a oggetti del server per SharePoint, aggiungere un `Microsoft.VisualStudio.Assembly` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento al percorso relativo dell'assembly che implementa il comando di SharePoint nel pacchetto VSIX. Per altre informazioni, vedere [Asset Element (Schema di VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Se l'estensione include un modello di progetto o un modello di elemento, aggiungere un `ProjectTemplate` oppure `ItemTemplate` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento al percorso relativo della cartella che contiene il modello nel pacchetto VSIX. Per altre informazioni, vedere [ProjectTemplate Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) e [elemento ItemTemplate (Schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    -   Se l'estensione include una procedura guidata personalizzata per un modello di progetto o un modello di elemento, aggiungere un' `Assembly` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento al percorso relativo dell'assembly nel pacchetto VSIX e quindi impostare il `AssemblyName` attributo sul nome dell'assembly completo (incluso versione, impostazioni cultura e token di chiave pubblica). Per altre informazioni, vedere [dipendenza Element (Schema di VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato il contenuto di un file extension vsixmanifest per un'estensione degli strumenti di SharePoint. L'estensione viene implementato in un assembly denominato Contoso.ProjectExtension.dll. L'estensione include un assembly di comando di SharePoint denominato Contoso.ExtensionCommands.dll e un modello di elemento in una cartella denominata **ItemTemplates** nel pacchetto VSIX. Questo esempio si presuppone che entrambi gli assembly si trovano nella stessa cartella del file Extension. vsixmanifest nel pacchetto VSIX.

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

## <a name="see-also"></a>Vedere anche

- [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Eseguire il debug delle estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
