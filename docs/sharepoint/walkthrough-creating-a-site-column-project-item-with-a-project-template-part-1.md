---
title: 'Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 202a9ac88310656c59fa507cbb8fe271b6f1d040
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813212"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1
  I progetti SharePoint sono contenitori per uno o più elementi di progetto SharePoint. È possibile estendere il sistema di progetto SharePoint in Visual Studio, creazione di propri tipi di elemento di progetto SharePoint e quindi associandoli con un modello di progetto. In questa procedura dettagliata, si definirà un tipo di elemento di progetto per la creazione di una colonna del sito e quindi si creerà un modello di progetto che può essere utilizzato per creare un nuovo progetto che contiene un elemento di progetto colonna del sito.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
- Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per una colonna del sito. Il tipo di elemento di progetto include una semplice proprietà personalizzata che viene visualizzato nei **proprietà** finestra.  
  
- Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto per l'elemento del progetto.  
  
- Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per distribuire il modello di progetto e l'assembly dell'estensione.  
  
- Il debug e test dell'elemento di progetto.  
  
  Si tratta di una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento del progetto mediante l'aggiunta di una procedura guidata per il modello di progetto. Per altre informazioni, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Per una serie di flussi di lavoro di esempio, vedere [esempi di flusso di lavoro di SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
- Edizioni supportate di Microsoft Windows, SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Oggetto [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Conoscenza del concetto di seguito è utile, ma non obbligatorio, completare la procedura dettagliata:  
  
- Colonne del sito in SharePoint. Per altre informazioni, vedere [colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
- Modelli di progetto in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
- Un progetto VSIX. Questo progetto consente di creare il pacchetto VSIX per distribuire l'elemento di progetto colonna del sito e il modello di progetto.  
  
- Un progetto di modello di progetto. Questo progetto consente di creare un modello di progetto che può essere utilizzato per creare un nuovo progetto di SharePoint che contiene l'elemento di progetto colonna del sito.  
  
- Un progetto di libreria di classi. Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto colonna del sito.  
  
  Avviare la procedura dettagliata mediante la creazione di progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
3.  In cima il **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
4.  Espandere la **Visual Basic** o **Visual c#** nodi, quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **progetto VSIX**.  
  
6.  Nel **Name** casella, immettere **SiteColumnProjectItem**e quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **SiteColumnProjectItem** progetto al **Esplora soluzioni**.  
  
#### <a name="to-create-the-project-template-project"></a>Per creare il progetto di modello di progetto  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
2.  In cima il **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere la **Visual c#** o **Visual Basic** nodo, quindi scegliere il **estendibilità** nodo.  
  
4.  Nell'elenco dei modelli di progetto, scegliere il **modello di progetto c#** oppure **modello di progetto Visual Basic** modello.  
  
5.  Nel **Name** casella, immettere **SiteColumnProjectTemplate**e quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **SiteColumnProjectTemplate** progetto alla soluzione.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
7.  Se è stato creato un progetto Visual Basic, eliminare anche i file seguenti dal progetto:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources. resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings. Settings  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
2.  In cima il **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere la **Visual c#** oppure **Visual Basic** nodi, scegliere il **Windows** nodo e quindi scegliere il **libreria di classi** modello.  
  
4.  Nel **Name** casella, immettere **ProjectItemTypeDefinition** e quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ProjectItemTypeDefinition** progetto alla soluzione e apre il file di codice predefinita Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Aggiungere i file di codice e i riferimenti ad assembly per configurare il progetto di estensione.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  Nel progetto ProjectItemTypeDefinition, aggiungere un file di codice denominato **SiteColumnProjectItemTypeProvider**.  
  
2.  Nella barra dei menu scegliere **Progetto** > **Aggiungi riferimento**.  
  
3.  Nel **gestione riferimenti - ProjectItemTypeDefinition** finestra di dialogo espandere il **assembly** nodo, scegliere il **Framework** nodo e quindi selezionare il Casella di controllo Composition.  
  
4.  Scegliere il **Extensions** nodo, selezionare la casella di controllo accanto all'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint
 Creare una classe che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di elemento di progetto.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint  
  
1.  Nel **SiteColumnProjectItemTypeProvider** file di codice, sostituire il codice predefinito con il codice seguente e quindi salvare il file.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Creare un modello di progetto di Visual Studio
 Tramite la creazione di un modello di progetto, consentire ad altri sviluppatori di creare progetti di SharePoint che contengono gli elementi di progetto colonna del sito. Un modello di progetto SharePoint include i file necessari per tutti i progetti in Visual Studio, ad esempio *file con estensione csproj* oppure *vbproj* e *vstemplate* di file e i file sono specifiche per i progetti SharePoint. Per altre informazioni, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 In questa procedura, si crea un progetto SharePoint vuoto per generare i file che sono specifici dei progetti SharePoint. Aggiungere quindi questi file al progetto SiteColumnProjectTemplate in modo che sono stati inclusi nel modello che viene generato da questo progetto. È inoltre configurare il file di progetto SiteColumnProjectTemplate per specificare dove verrà visualizzato il modello di progetto di **nuovo progetto** nella finestra di dialogo.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Per creare i file del modello di progetto  
  
1. Avviare una seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative.  
  
2. Creare un progetto di SharePoint 2010 che è denominato **BaseSharePointProject**.  
  
   > [!IMPORTANT]  
   >  Nel **Personalizzazione guidata SharePoint**, non selezionare la **Distribuisci come soluzione farm** pulsante di opzione.  
  
3. Aggiungere un elemento vuoto al progetto e quindi denominare l'elemento **Field1**.  
  
4. Salvare il progetto e quindi chiudere la seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5. Nell'istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la soluzione SiteColumnProjectItem, in **Esplora soluzioni**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo del progetto, scegliere  **Aggiungere**, quindi scegliere **elemento esistente**.  
  
6. Nel **Aggiungi elemento esistente** finestra di dialogo, aprire l'elenco di estensioni di file e quindi scegliere **tutti i file (\*.\*)** .  
  
7. Nella directory che contiene il progetto BaseSharePointProject, selezionare il file snk e quindi scegliere il **Add** pulsante.  
  
   > [!NOTE]  
   >  In questa procedura dettagliata, il modello di progetto creato utilizza lo stesso file snk per firmare ogni progetto che viene creato usando il modello. Per informazioni su come espandere questo esempio per creare un file snk diverso per ogni istanza del progetto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8. Ripetere i passaggi da 5 a 8 per aggiungere i file seguenti dalle cartelle secondarie specificati nella directory BaseSharePointProject:  
  
   - *\Field1\Elements.Xml*  
  
   - *\Field1\SharePointProjectItem.spdata*  
  
   - *\Features\Feature1\Feature1.feature*  
  
   - *\Features\Feature1\Feature1.Template.Xml*  
  
   - *\Package\Package.package*  
  
   - *\Package\Package.Template.Xml*  
  
     Aggiungere questi file direttamente al progetto SiteColumnProjectTemplate; non ricreare le sottocartelle Field1, funzionalità o pacchetto nel progetto. Per altre informazioni su questi file, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Per configurare come gli sviluppatori di individuare il modello di progetto nella finestra di dialogo Nuovo progetto
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo del progetto e quindi scegliere **Scarica progetto**. Se viene chiesto di salvare le modifiche a tutti i file, scegliere il **Sì** pulsante.  
  
2.  Aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo anche in questo caso, quindi scegliere **Modifica SiteColumnProjectTemplate. csproj** o **modificare SiteColumnProjectTemplate**.  
  
3.  Nel file di progetto, individuare la seguente `VSTemplate` elemento.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Sostituire l'elemento con il codice XML seguente.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Il `OutputSubPath` elemento specifica cartelle aggiuntive nel percorso in cui il modello di progetto viene creato quando si compila il progetto. Le cartelle specificate in questo caso assicurarsi che il modello di progetto sarà disponibile solo quando i clienti aprire il **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.  
  
5.  Salvare e chiudere il file.  
  
6.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** del progetto e quindi scegliere **Ricarica progetto**.  
  
## <a name="edit-the-project-template-files"></a>Modificare i file di modello di progetto
 Nel progetto SiteColumnProjectTemplate, modificare i file seguenti per definire il comportamento del modello di progetto:  
  
- *AssemblyInfo.cs* o *AssemblyInfo. vb*  
  
- *Elements. Xml*  
  
- *SharePointProjectItem*  
  
- *Feature1*  
  
- *Package. package*  
  
- *SiteColumnProjectTemplate*  
  
- *Csproj* o *ProjectTemplate*  
  
  Nelle procedure seguenti, si aggiungeranno parametri sostituibili per alcuni di questi file. Un parametro sostituibile è un token che inizia e termina con il simbolo di dollaro ($). Quando un utente Usa questo modello di progetto per creare un progetto, Visual Studio sostituisce automaticamente questi parametri nel nuovo progetto con valori specifici. Per altre informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Per modificare il file AssemblyInfo.cs o AssemblyInfo. vb
  
1.  Nel progetto SiteColumnProjectTemplate, aprire il *AssemblyInfo.cs* oppure *AssemblyInfo. vb* file e quindi aggiungere l'istruzione seguente all'inizio di esso:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Quando la **soluzione creata mediante sandbox** di un progetto SharePoint viene impostata su **True**, Visual Studio aggiunge il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> al file di codice AssemblyInfo. Tuttavia, non importa il file di codice AssemblyInfo nel modello di progetto di <xref:System.Security> dello spazio dei nomi per impostazione predefinita. È necessario aggiungerli **usando** oppure **importazioni** istruzione per evitare errori di compilazione.  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Per modificare il file Elements. Xml
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *Elements* file con il codice XML seguente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Il nuovo codice XML viene aggiunto un `Field` elemento che definisce il nome della colonna del sito, il tipo di base e il gruppo in cui elencare la colonna del sito nella raccolta. Per altre informazioni sul contenuto di questo file, vedere [Schema di definizione del campo](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Per modificare il file SharePointProjectItem
  
1. Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *SharePointProjectItem* file con il codice XML seguente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
     <Files>  
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
     </Files>   
   </ProjectItem>  
   ```  
  
    Il nuovo codice XML apporta le modifiche seguenti al file:  
  
   - Modifiche i `Type` attributo del `ProjectItem` elemento sulla stessa stringa che viene passato al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto (il `SiteColumnProjectItemTypeProvider` classe creata in precedenza in questa procedura dettagliata).  
  
   - Rimuove il `SupportedTrustLevels` e `SupportedDeploymentScopes` gli attributi dal `ProjectItem` elemento. Questi valori di attributo sono necessari perché i livelli di attendibilità e ambiti di distribuzione vengono specificati nel `SiteColumnProjectItemTypeProvider` classe nel progetto ProjectItemTypeDefinition.  
  
     Per altre informazioni sul contenuto di *spdata* i file, vedere [riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2. Salvare e chiudere il file.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Per modificare il file Feature1
  
1. Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *Feature1* file con il codice XML seguente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
     <projectItems>  
       <projectItemReference itemId="$guid2$" />  
     </projectItems>  
   </feature>  
   ```  
  
    Il nuovo codice XML apporta le modifiche seguenti al file:  
  
   - Modifica i valori del `Id` e `featureId` attributi delle `feature` elemento `$guid4$`.  
  
   - Modifica i valori del `itemId` attributo del `projectItemReference` elemento `$guid2$`.  
  
     Per altre informazioni sulle *feature* i file, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Salvare e chiudere il file.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Per modificare il file package.
  
1. Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *package. package* file con il codice XML seguente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
     <features>  
       <featureReference itemId="$guid4$" />  
     </features>  
   </package>  
   ```  
  
    Il nuovo codice XML apporta le modifiche seguenti al file:  
  
   - Modifica i valori del `Id` e `solutionId` attributi delle `package` elemento `$guid3$`.  
  
   - Modifica i valori del `itemId` attributo del `featureReference` elemento `$guid4$`.  
  
     Per altre informazioni sulle *package* i file, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Salvare e chiudere il file.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Per modificare il file SiteColumnProjectTemplate
  
1. Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file SiteColumnProjectTemplate con una delle seguenti sezioni di codice XML.  
  
   -   Se si sta creando un modello di progetto Visual c#, usare il codice XML seguente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>CSharp</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
   -   Se si sta creando un modello di progetto Visual Basic, usare il codice XML seguente.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>VisualBasic</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Il nuovo codice XML apporta le modifiche seguenti al file:  
  
   - Imposta il `Name` elemento sul valore **colonna del sito**. (Questo nome viene visualizzato nei **nuovo progetto** nella finestra di dialogo).  
  
   - Aggiunge `ProjectItem` elementi per ogni filethat del inclusi in ogni istanza del progetto.  
  
   - Usa lo spazio dei nomi "<http://schemas.microsoft.com/developer/vstemplate/2005>". Altri file di progetto in uso questa soluzione di "<http://schemas.microsoft.com/developer/msbuild/2003>" dello spazio dei nomi. Pertanto, verranno generati messaggi di avviso di XML schema, ma è possibile ignorare tali in questa procedura dettagliata.  
  
     Per altre informazioni sul contenuto di *vstemplate* i file, vedere [riferimenti allo Schema di Visual Studio modello](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2. Salvare e chiudere il file.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Per modificare il file csproj o ProjectTemplate
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *csproj* file o *ProjectTemplate* file con una delle seguenti sezioni di codice XML.  
  
    -   Se si sta creando un modello di progetto Visual c#, usare il codice XML seguente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Se si sta creando un modello di progetto Visual Basic, usare il codice XML seguente.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Il nuovo codice XML apporta le modifiche seguenti al file:  
  
    -   Usa il `TargetFrameworkVersion` elemento per specificare .NET Framework 3.5, non 4.5.  
  
    -   Aggiunge `SignAssembly` e `AssemblyOriginatorKeyFile` elementi da firmare l'output del progetto.  
  
    -   Aggiunge `Reference` elementi per l'assembly fa riferimento che usano i progetti SharePoint.  
  
    -   Aggiunge gli elementi per ogni file predefinito nel progetto, ad esempio *Elements* e *SharePointProjectItem*.  
  
2.  Salvare e chiudere il file.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Creare un pacchetto VSIX per distribuire il modello di progetto
 Per distribuire l'estensione, usare il progetto VSIX nel **SiteColumnProjectItem** soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  Nelle **Esplora soluzioni**, nella **SiteColumnProjectItem** del progetto, aprire il file vsixmanifest nell'editor del manifesto.  
  
     Il file vsixmanifest costituisce la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** casella, immettere **colonna del sito**.  
  
3.  Nel **Author** casella, immettere **Contoso**.  
  
4.  Nel **Description** casella, immettere **progetto di SharePoint per la creazione di colonne del sito**.  
  
5.  Scegliere il **Assets** scheda e quindi scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `ProjectTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di progetto. Per altre informazioni, vedere [ProjectTemplate Element (Schema di VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** elenco e scegliere **SiteColumnProjectTemplate**, quindi scegliere il **OK** pulsante.  
  
9. Scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
10. Nel **tipo** casella di riepilogo **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
12. Nel **progetto** scegliere **ProjectItemTypeDefinition**, quindi scegliere il **OK** pulsante.  
  
13. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.  
  
## <a name="test-the-project-template"></a>Il modello di progetto di test
 A questo punto si è pronti testare il modello di progetto. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi il **colonne del sito** progetto nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che la colonna del sito funziona come previsto.  
  
#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  
  
3.  Nel file di codice SiteColumnProjectItemTypeProvider, aggiungere un punto di interruzione per la prima riga del codice nel `InitializeType` metodo e quindi scegliere il **F5** chiave per avviare il debug.  
  
     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Per testare il progetto in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.  
  
2.  Espandere la **Visual c#** o **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di progetto), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere il **colonne del sito** modello.  
  
4.  Nel **Name** casella, immettere **SiteColumnTest** e quindi scegliere il **OK** pulsante.  
  
     Nelle **Esplora soluzioni**, verrà visualizzato un nuovo progetto con un elemento del progetto denominato **Field1**.  
  
5.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nella `InitializeType` metodo e quindi scegliere il **F5** un tasto per continuare il debug del progetto.  
  
6.  In **Esplora soluzioni**, scegliere il **Field1** nodo, quindi scegliere il **F4** chiave.  
  
     Il **proprietà** verrà visualizzata la finestra.  
  
7.  Nell'elenco delle proprietà, verificare che la proprietà **esempio di proprietà** viene visualizzata.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint  
  
1.  Nelle **Esplora soluzioni**, scegliere il **SiteColumnTest** nodo.  
  
2.  Nel **le proprietà** nella casella di testo accanto alla finestra la **URL del sito** proprietà, immettere **http://localhost**.  
  
     Questo passaggio specifica il sito di SharePoint locale nel computer di sviluppo che si desidera utilizzare per il debug.  
  
    > [!NOTE]  
    >  Il **URL sito** proprietà è vuota per impostazione predefinita perché il modello di progetto colonna del sito non fornisce una procedura guidata per la raccolta di questo valore quando viene creato il progetto. Per informazioni su come aggiungere una procedura guidata che richiede lo sviluppatore per questo valore e quindi configura questa proprietà nel nuovo progetto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Premere **F5**.  
  
     È incluso nel pacchetto e distribuita nel sito di SharePoint specificato nella colonna del sito di **URL sito** proprietà del progetto. Il browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** verrà visualizzata la finestra di dialogo, scegliere il **Yes** per continuare il debug del progetto.  
  
4.  Nel **Azioni sito** menu, scegliere **Impostazioni sito**.  
  
5.  Nel **Impostazioni sito** nella pagina il **raccolte** scegliere il **colonne del sito** collegamento.  
  
6.  Nell'elenco delle colonne del sito, verificare che un **colonne personalizzate** gruppo contiene una colonna denominata **SiteColumnTest**.  
  
7.  Chiudere il Web browser.  
  
## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni, scegliere il **colonna del sito** estensione, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere il **Chiudi** pulsante per completare la disinstallazione.  
  
5.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione SiteColumnProjectItem è aperta).  
  
## <a name="next-steps"></a>Passaggi successivi
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata per il modello di progetto. Quando un utente crea un progetto colonna del sito, la procedura guidata chiede all'utente l'URL del sito da utilizzare per il debug e se la nuova soluzione è in modalità sandbox e la procedura guidata consente di configurare il nuovo progetto con queste informazioni. Anche la procedura guidata raccoglie le informazioni relative alla colonna (ad esempio il tipo di base e il gruppo in cui elencare la colonna nella raccolta di colonne del sito) e aggiunge queste informazioni per il *Elements* file nel nuovo progetto. Per altre informazioni, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
