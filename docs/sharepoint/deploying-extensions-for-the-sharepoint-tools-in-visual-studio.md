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
ms.openlocfilehash: 0e7bcb4c03a274c958b097ab7869cb58120b0ee7
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740144"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Distribuire estensioni per gli strumenti di SharePoint in Visual Studio

Per distribuire un'estensione degli strumenti di SharePoint, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) che contenga l'assembly dell'estensione e tutti gli altri file che si desidera distribuire con l'estensione. Un pacchetto VSIX è un file compresso che segue lo standard Open Packaging Conventions (OPC). I pacchetti VSIX hanno l'estensione *VSIX* .

Dopo aver creato un pacchetto VSIX, altri utenti possono eseguire il file VSIX per installare l'estensione. Quando un utente installa l'estensione, tutti i file vengono installati nella cartella%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Per distribuire l'estensione, è possibile caricare il pacchetto VSIX nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oppure è possibile distribuire il pacchetto ai clienti in altri modi, ad esempio ospitando il pacchetto in una condivisione di rete o in un altro sito Web.

Per ulteriori informazioni sulla creazione di pacchetti VSIX e sulla relativa distribuzione alla [Visual Studio Marketplace](https://marketplace.visualstudio.com/), vedere la pagina relativa alla distribuzione delle [estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 È possibile creare un pacchetto VSIX usando il modello di **progetto VSIX** in Visual Studio oppure è possibile creare manualmente un pacchetto VSIX.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Usare progetti VSIX per creare pacchetti VSIX

È possibile usare il modello di **progetto VSIX** fornito da Visual Studio SDK per creare pacchetti VSIX per le estensioni degli strumenti di SharePoint. L'uso di un progetto VSIX offre diversi vantaggi rispetto alla creazione manuale di un pacchetto VSIX:

- Visual Studio genera automaticamente il pacchetto VSIX quando si compila il progetto. Le attività quali l'aggiunta dei file di distribuzione al pacchetto e la creazione del file [Content_Types]. XML per il pacchetto vengono eseguite per l'utente.

- È possibile configurare il progetto VSIX per includere l'output di compilazione del progetto di estensione e altri file, ad esempio modelli di progetto e modelli di elementi, nel pacchetto VSIX.

Per altre informazioni sull'uso di un progetto VSIX, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizzare i progetti

Per impostazione predefinita, i progetti VSIX generano solo pacchetti VSIX, non assembly. Di conseguenza, in genere non si implementa un'estensione degli strumenti di SharePoint in un progetto VSIX. Generalmente si utilizzano almeno due progetti:

- Progetto VSIX.

- Progetto di libreria di classi che implementa l'estensione.

È anche possibile usare progetti aggiuntivi per determinati tipi di estensioni:

- Progetto di libreria di classi che implementa tutti i comandi di SharePoint utilizzati dall'estensione. Per una procedura dettagliata in cui viene illustrato questo scenario, vedere [procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Un modello di elemento o un progetto di modello di progetto che consente di creare un modello di elemento o un modello di progetto, se l'estensione definisce un nuovo tipo di elemento di progetto SharePoint. Per una procedura dettagliata in cui viene illustrato questo scenario, vedere [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Progetto di libreria di classi che implementa una procedura guidata personalizzata per un modello di elemento o un modello di progetto, se l'estensione include un modello. Per una procedura dettagliata in cui viene illustrato questo scenario, vedere [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Se si includono tutti i progetti nella stessa soluzione di Visual Studio, è possibile modificare il file source. Extension. vsixmanifest nel progetto VSIX per includere l'output di compilazione dei progetti della libreria di classi.

### <a name="edit-the-vsix-manifest"></a>Modificare il manifesto VSIX

È necessario modificare il file source. Extension. vsixmanifest nel progetto VSIX per includere le voci per tutti gli elementi che si desidera includere nell'estensione. Quando si apre il file source. Extension. vsixmanifest dal relativo menu di scelta rapida, il file viene visualizzato in una finestra di progettazione che fornisce un'interfaccia utente per la modifica del codice XML nel file. Per ulteriori informazioni, vedere [VSIX manifest designer](../extensibility/vsix-manifest-designer.md).

È necessario aggiungere voci al file source. Extension. vsixmanifest per gli elementi seguenti:

- Assembly dell'estensione.

- Assembly che implementa tutti i comandi di SharePoint utilizzati dall'estensione.

- Qualsiasi modello di progetto o modello di elemento associato all'estensione.

- Procedura guidata personalizzata per un modello associato all'estensione.

Nelle procedure seguenti viene descritto come aggiungere voci al file con estensione vsixmanifest per ognuno di questi elementi.

#### <a name="to-include-the-extension-assembly"></a>Per includere l'assembly dell'estensione

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere **Apri**.

     Il file verrà aperto nella finestra di progettazione

2. Nella scheda **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

4. Nell'elenco **origine** eseguire uno dei passaggi seguenti:

    - Se l'assembly dell'estensione viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nell'elenco **progetto** scegliere il nome del progetto.

    - Se l'assembly dell'estensione è incluso come file nel progetto, scegliere file nel file **System**. Nell'elenco **percorso** immettere il percorso completo del file di assembly dell'estensione oppure usare il pulsante **Sfoglia** per individuare e scegliere il file di assembly.

5. Fare clic su **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Per includere un assembly del comando di SharePoint

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere il pulsante **Apri** .

     Il file verrà aperto nella finestra di progettazione.

2. Nella sezione **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nella casella **tipo** immettere **SharePoint. Commands. v4**.

4. Nell'elenco **origine** eseguire uno dei passaggi seguenti:

    - Se l'assembly del comando è compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nell'elenco **progetto** scegliere il nome del progetto.

    - Se l'assembly del comando è incluso come file nel progetto, scegliere file nel file **System**. Nell'elenco **percorso** immettere il percorso completo del file di assembly dell'estensione oppure usare il pulsante **Sfoglia** per individuare e scegliere il file di assembly.

5. Fare clic su **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Per includere un modello creato

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere il pulsante **Apri** .

     Il file verrà aperto nella finestra di progettazione.

2. Nella sezione **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. ProjectTemplate** o **Microsoft. VisualStudio. ItemTemplate**.

4. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

5. Nell'elenco **progetto** , scegliere il nome del progetto, quindi scegliere il pulsante **OK** .

6. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto di modello di progetto o di elemento, quindi scegliere **Scarica progetto**.

7. Aprire di nuovo il menu di scelta rapida per il nodo del progetto, quindi scegliere **modifica**_NomeProgettoModello_**. csproj** o **modifica**_NomeProgettoModello_**. vbproj**.

8. Individuare l' `VSTemplate` elemento seguente nel file di progetto.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Sostituisci l'elemento con il codice XML seguente.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` elemento specifica altre cartelle nel percorso in cui viene creato il modello di progetto quando si compila il progetto. Le cartelle specificate qui assicurano che il modello di elemento sarà disponibile solo quando i clienti aprono la finestra di dialogo **Aggiungi nuovo progetto** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

10. Salvare e chiudere il file.

11. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto modello di progetto o modello di elemento, quindi scegliere **Ricarica progetto**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Per includere un modello creato manualmente

1. Nel progetto VSIX aggiungere una nuova cartella al progetto per contenere il modello.

2. In questa nuova cartella creare le sottocartelle seguenti e quindi aggiungere il file del modello (con estensione zip) alla cartella *ID impostazioni locali* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID locale*

     *YourTemplateName*. zip

     Se, ad esempio, si dispone di un modello di elemento denominato ContosoCustomAction.zip che supporta le impostazioni locali per la lingua inglese (Stati Uniti), il percorso completo può essere *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. In **Esplora soluzioni**scegliere il file modello (*YourTemplateName*. zip).

4. Nella finestra **Proprietà** impostare la proprietà **azione di compilazione** su **contenuto**.

5. Aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere **Apri**.

     Il file verrà aperto nella finestra di progettazione.

6. Nella sezione **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

7. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. ItemTemplate** o **Microsoft. VisualStudio. ProjectTemplate**.

8. Nell'elenco **origine** scegliere **file su file System**.

9. Nel campo **percorso** immettere il percorso completo dell'assembly, ad esempio *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, oppure usare il pulsante **Sfoglia** per individuare e scegliere l'assembly, quindi scegliere il pulsante **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Per includere una procedura guidata per un modello di progetto o un modello di elemento

1. Nel progetto VSIX aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere **Apri**.

     Il file verrà aperto nella finestra di progettazione.

2. Nella sezione **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. assembly**.

4. Nell'elenco **origine** eseguire uno dei passaggi seguenti:

    - Se l'assembly della procedura guidata viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nell'elenco **progetto** scegliere il nome del progetto.

    - Se l'assembly della procedura guidata è incluso come file nel progetto, scegliere **file**nel file System. Nel campo **percorso** immettere il percorso completo del file di assembly oppure usare il pulsante **Sfoglia** per individuare e scegliere l'assembly.

5. Fare clic su **OK** .

### <a name="related-walkthroughs"></a>Procedure dettagliate correlate

La tabella seguente elenca le procedure dettagliate che illustrano come usare un progetto VSIX per distribuire tipi diversi di estensioni degli strumenti di SharePoint.

|Tipo di estensione|Procedure dettagliate correlate|
|--------------------|--------------------------|
|Estensione che include solo l'assembly dell'estensione|[Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procedura dettagliata: creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procedura dettagliata: chiamare il modello a oggetti del client di SharePoint in un'estensione Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Estensione che include i comandi di SharePoint|[Procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Estensione che include un modello di Visual Studio|[Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Estensione che include una procedura guidata per i modelli|[Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Creare pacchetti VSIX manualmente

Se si vuole creare manualmente il pacchetto VSIX per l'estensione degli strumenti di SharePoint, seguire questa procedura:

1. Creare il file con estensione vsixmanifest e il file [Content_Types]. XML in una nuova cartella. Per altre informazioni, vedere [anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. In Esplora risorse fare clic con il pulsante destro del mouse sulla cartella che contiene i due file XML, scegliere Invia a e quindi fare clic su cartella compressa. Rinominare il file ZIP risultante in Nomefile.vsix, dove Nomefile è il nome del file ridistribuibile che installa il pacchetto.

3. Aggiungere l'assembly dell'estensione al pacchetto VSIX. Se l'estensione include un comando di SharePoint, aggiungere anche l'assembly che implementa il comando di SharePoint al pacchetto VSIX.

4. Modificare il file con estensione vsixmanifest:

    - Aggiungere un `Microsoft.VisualStudio.MefComponent` elemento sotto l' `Assets` elemento, quindi impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa l'estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Se l'estensione include un comando di SharePoint che effettua chiamate nel modello a oggetti del server per SharePoint, aggiungere un `Microsoft.VisualStudio.Assembly` elemento sotto l' `Assets` elemento. Impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa il comando di SharePoint nel pacchetto VSIX. Per altre informazioni, vedere [elemento asset (schema VSX)](/previous-versions/dd393737(v=vs.110)).

    - Se l'estensione include un modello di progetto o un modello di elemento, aggiungere un `ProjectTemplate` `ItemTemplate` elemento o sotto l' `Assets` elemento. Impostare il valore del nuovo elemento sul percorso relativo della cartella che contiene il modello nel pacchetto VSIX. Per altre informazioni, vedere [elemento ProjectTemplate (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) e [elemento ITEMTEMPLATE (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Se l'estensione include una procedura guidata personalizzata per un modello di progetto o di elemento, aggiungere un `Assembly` elemento sotto l' `Assets` elemento. Impostare il valore del nuovo elemento sul percorso relativo dell'assembly nel pacchetto VSIX, quindi impostare l' `AssemblyName` attributo sul nome completo dell'assembly (incluse la versione, le impostazioni cultura e il token di chiave pubblica). Per altre informazioni, vedere [elemento dependency (schema VSX)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato il contenuto di un file Extension. vsixmanifest per un'estensione degli strumenti di SharePoint. L'estensione viene implementata in un assembly denominato Contoso.ProjectExtension.dll. L'estensione include un assembly dei comandi di SharePoint denominato Contoso.ExtensionCommands.dll e un modello di elemento in una cartella denominata **ItemTemplates** nel pacchetto VSIX. Questo esempio si basa sul presupposto che entrambi gli assembly si trovino nella stessa cartella del file Extension. vsixmanifest nel pacchetto VSIX.

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

- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Chiamare nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)