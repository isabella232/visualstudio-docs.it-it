---
title: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fea425da8a6e49643997151c6273fbbffc7033db
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016512"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1
  I progetti SharePoint sono contenitori per uno o più elementi del progetto SharePoint. Per estendere il sistema del progetto SharePoint in Visual Studio, è possibile creare tipi di elemento di progetto SharePoint personalizzati e quindi associarli a un modello di progetto. In questa procedura dettagliata verrà definito un tipo di elemento di progetto per la creazione di una colonna del sito, quindi verrà creato un modello di progetto che può essere utilizzato per creare un nuovo progetto che contiene un elemento di progetto colonna del sito.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per una colonna del sito. Il tipo di elemento del progetto include una semplice proprietà personalizzata visualizzata nella finestra **Proprietà** .

- Creazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di un modello di progetto per l'elemento del progetto.

- Compilazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di un pacchetto di estensione (VSIX) per distribuire il modello di progetto e l'assembly dell'estensione.

- Debug e test dell'elemento del progetto.

  Si tratta di una procedura dettagliata autonoma. Al termine di questa procedura dettagliata, è possibile migliorare l'elemento del progetto aggiungendo una procedura guidata al modello di progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Per una serie di flussi di lavoro di esempio, vedere [esempi di flussi di lavoro di SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Microsoft Windows, SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è utile, ma non necessario, conoscere il concetto seguente:

- Colonne del sito in SharePoint. Per ulteriori informazioni, vedere [colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Modelli di progetto in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'elemento di progetto colonna del sito e il modello di progetto.

- Progetto di modello di progetto. Questo progetto crea un modello di progetto che può essere utilizzato per creare un nuovo progetto SharePoint che contiene l'elemento del progetto della colonna del sito.

- Un progetto libreria di classi. Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto della colonna del sito.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella parte superiore della finestra di dialogo **nuovo progetto** assicurarsi che **.NET Framework 4,5** sia selezionato nell'elenco delle versioni del .NET Framework.

4. Espandere i nodi **Visual Basic** o **Visual C#** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

5. Nell'elenco dei modelli di progetto scegliere **progetto VSIX**.

6. Nella casella **nome** immettere **SiteColumnProjectItem**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **SiteColumnProjectItem** a **Esplora soluzioni**.

#### <a name="to-create-the-project-template-project"></a>Per creare il progetto di modello di progetto

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella parte superiore della finestra di dialogo **nuovo progetto** assicurarsi che **.NET Framework 4,5** sia selezionato nell'elenco delle versioni del .NET Framework.

3. Espandere il nodo **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

4. Nell'elenco dei modelli di progetto scegliere il modello di **progetto C#** o **Visual Basic** modello di modello di progetto.

5. Nella casella **nome** immettere **SiteColumnProjectTemplate**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **SiteColumnProjectTemplate** alla soluzione.

6. Eliminare il file di codice Class1 dal progetto.

7. Se è stato creato un progetto di Visual Basic, eliminare anche i file seguenti dal progetto:

    - *Applicazione. designer. vb*

    - MyApplication. myapp

    - *Risorse. designer. vb*

    - *Resources. resx*

    - *Settings. designer. vb*

    - Settings. Settings

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella parte superiore della finestra di dialogo **nuovo progetto** assicurarsi che **.NET Framework 4,5** sia selezionato nell'elenco delle versioni del .NET Framework.

3. Espandere i nodi **Visual C#** o **Visual Basic** , scegliere il nodo **Windows** , quindi scegliere il modello **libreria di classi** .

4. Nella casella **nome** immettere **ProjectItemTypeDefinition** , quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aggiunge il progetto **ProjectItemTypeDefinition** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Aggiungere i file di codice e i riferimenti ad assembly per configurare il progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto ProjectItemTypeDefinition aggiungere un file di codice denominato **SiteColumnProjectItemTypeProvider**.

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi riferimento**.

3. Nella finestra di dialogo **Gestione riferimenti-ProjectItemTypeDefinition** espandere il nodo **assembly** , scegliere il nodo **Framework** , quindi selezionare la casella di controllo System. ComponentModel. Composition.

4. Scegliere il nodo **estensioni** , selezionare la casella di controllo accanto all'assembly Microsoft. VisualStudio. SharePoint, quindi scegliere il pulsante **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint
 Creare una classe che implementi l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia quando si desidera definire un nuovo tipo di elemento di progetto.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint

1. Nel file di codice **SiteColumnProjectItemTypeProvider** sostituire il codice predefinito con il codice seguente e quindi salvare il file.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Creare un modello di progetto di Visual Studio
 Creando un modello di progetto, si consente ad altri sviluppatori di creare progetti SharePoint che contengono elementi di progetto della colonna del sito. Un modello di progetto SharePoint include i file necessari per tutti i progetti in Visual Studio, ad esempio file con *estensione csproj* o *VBPROJ* e *vstemplate* , e file specifici per i progetti SharePoint. Per altre informazioni, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 In questa procedura viene creato un progetto SharePoint vuoto per generare i file specifici dei progetti SharePoint. Si aggiungono quindi questi file al progetto SiteColumnProjectTemplate in modo che siano inclusi nel modello generato da questo progetto. Il file di progetto SiteColumnProjectTemplate viene inoltre configurato per specificare dove viene visualizzato il modello di progetto nella finestra di dialogo **nuovo progetto** .

#### <a name="to-create-the-files-for-the-project-template"></a>Per creare i file per il modello di progetto

1. Avviare una seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative.

2. Creare un progetto SharePoint 2010 denominato **BaseSharePointProject**.

   > [!IMPORTANT]
   > Nella **procedura guidata di personalizzazione di SharePoint**non selezionare il pulsante di opzione **Distribuisci come soluzione farm** .

3. Aggiungere un elemento vuoto al progetto, quindi denominare l'elemento **Field1**.

4. Salvare il progetto, quindi chiudere la seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. Nell'istanza di in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cui è aperta la soluzione SiteColumnProjectItem, in **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SiteColumnProjectTemplate** , scegliere **Aggiungi**, quindi **elemento esistente**.

6. Nella finestra di dialogo **Aggiungi elemento esistente** aprire l'elenco di estensioni di file, quindi scegliere **tutti i file ( \* . \* )**.

7. Nella directory che contiene il progetto BaseSharePointProject selezionare il file Key. snk, quindi scegliere il pulsante **Aggiungi** .

   > [!NOTE]
   > In questa procedura dettagliata, il modello di progetto creato usa lo stesso file Key. snk per firmare ogni progetto creato usando il modello. Per informazioni su come espandere questo esempio per creare un file Key. snk diverso per ogni istanza del progetto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Ripetere i passaggi 5-8 per aggiungere i seguenti file dalle sottocartelle specificate nella directory BaseSharePointProject:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Aggiungere questi file direttamente al progetto SiteColumnProjectTemplate. non ricreare le sottocartelle Field1, features o Package nel progetto. Per altre informazioni su questi file, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Per configurare il modo in cui gli sviluppatori individuano il modello di progetto nella finestra di dialogo nuovo progetto

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SiteColumnProjectTemplate** , quindi scegliere **Scarica progetto**. Se viene richiesto di salvare le modifiche apportate ai file, scegliere il pulsante **Sì** .

2. Aprire di nuovo il menu di scelta rapida per il nodo **SiteColumnProjectTemplate** , quindi scegliere **Modifica SiteColumnProjectTemplate. csproj** o **Modifica SiteColumnProjectTemplate. vbproj**.

3. Nel file di progetto, individuare l' `VSTemplate` elemento seguente.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Sostituisci l'elemento con il codice XML seguente.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` elemento specifica altre cartelle nel percorso in cui viene creato il modello di progetto quando si compila il progetto. Le cartelle specificate qui assicurano che il modello di progetto sarà disponibile solo quando i clienti aprono la finestra di dialogo **nuovo progetto** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

5. Salvare e chiudere il file.

6. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SiteColumnProjectTemplate** , quindi scegliere **Ricarica progetto**.

## <a name="edit-the-project-template-files"></a>Modificare i file del modello di progetto
 Nel progetto SiteColumnProjectTemplate modificare i file seguenti per definire il comportamento del modello di progetto:

- *AssemblyInfo.cs* o *AssemblyInfo. vb*

- *Elements.xml*

- *SharePointProjectItem. spdata*

- *Feature1. feature*

- *Package. Package*

- *SiteColumnProjectTemplate. vstemplate*

- *ProjectTemplate. csproj* o *ProjectTemplate. vbproj*

  Nelle procedure seguenti verranno aggiunti parametri sostituibili ad alcuni di questi file. Un parametro sostituibile è un token che inizia e termina con il segno di dollaro ($). Quando un utente usa questo modello di progetto per creare un progetto, Visual Studio sostituisce automaticamente questi parametri nel nuovo progetto con valori specifici. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Per modificare il file AssemblyInfo.cs o AssemblyInfo. vb

1. Nel progetto SiteColumnProjectTemplate aprire il file *AssemblyInfo.cs* o *AssemblyInfo. vb* , quindi aggiungere l'istruzione seguente alla parte superiore:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Quando la proprietà della **soluzione creata mediante sandbox** di un progetto SharePoint è impostata su **true**, Visual Studio aggiunge al <xref:System.Security.AllowPartiallyTrustedCallersAttribute> file di codice AssemblyInfo. Tuttavia, il file di codice AssemblyInfo nel modello di progetto non importa lo <xref:System.Security> spazio dei nomi per impostazione predefinita. È necessario aggiungere questa istruzione **using** o **Imports** per evitare errori di compilazione.

2. Salvare e chiudere il file.

#### <a name="to-edit-the-elementsxml-file"></a>Per modificare il file di Elements.xml

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file di *Elements.xml* con il codice XML seguente.

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

     Il nuovo XML aggiunge un `Field` elemento che definisce il nome della colonna del sito, il tipo di base e il gruppo in cui elencare la colonna del sito nella raccolta. Per ulteriori informazioni sul contenuto di questo file, vedere [schema di definizione dei campi](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Per modificare il file SharePointProjectItem. spdata

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *SharePointProjectItem. spdata* con il codice XML seguente.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Il nuovo codice XML apporta le seguenti modifiche al file:

   - Modifica l' `Type` attributo dell' `ProjectItem` elemento nella stessa stringa passata a nella definizione dell'elemento di <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> progetto (la `SiteColumnProjectItemTypeProvider` classe creata in precedenza in questa procedura dettagliata).

   - Rimuove gli `SupportedTrustLevels` `SupportedDeploymentScopes` attributi e dall' `ProjectItem` elemento. Questi valori di attributo non sono necessari perché i livelli di attendibilità e gli ambiti di distribuzione sono specificati nella `SiteColumnProjectItemTypeProvider` classe nel progetto ProjectItemTypeDefinition.

     Per ulteriori informazioni sul contenuto dei file con *estensione spdata* , vedere [riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-feature1feature-file"></a>Per modificare il file Feature1. feature

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Feature1. feature* con il codice XML seguente.

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

    Il nuovo codice XML apporta le seguenti modifiche al file:

   - Modifica i valori degli `Id` attributi e `featureId` dell' `feature` elemento in `$guid4$` .

   - Modifica i valori dell' `itemId` attributo dell' `projectItemReference` elemento in `$guid2$` .

     Per ulteriori informazioni sui file con *estensione feature* , vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-packagepackage-file"></a>Per modificare il file Package. Package

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Package. Package* con il codice XML seguente.

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

    Il nuovo codice XML apporta le seguenti modifiche al file:

   - Modifica i valori degli `Id` attributi e `solutionId` dell' `package` elemento in `$guid3$` .

   - Modifica i valori dell' `itemId` attributo dell' `featureReference` elemento in `$guid4$` .

     Per ulteriori informazioni sui file con *estensione package* , vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Per modificare il file SiteColumnProjectTemplate. vstemplate

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file SiteColumnProjectTemplate. vstemplate con una delle sezioni seguenti di XML.

   - Se si sta creando un modello di progetto di Visual C#, usare il codice XML seguente.

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

   - Se si sta creando un modello di progetto Visual Basic, usare il codice XML seguente.

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

    Il nuovo codice XML apporta le seguenti modifiche al file:

   - Imposta l' `Name` elemento sulla colonna del **sito**del valore. Questo nome viene visualizzato nella finestra di dialogo **nuovo progetto** .

   - Aggiunge `ProjectItem` elementi per ogni file, incluso in ogni istanza del progetto.

   - USA lo spazio dei nomi `http://schemas.microsoft.com/developer/vstemplate/2005` . Altri file di progetto in questa soluzione usano lo `http://schemas.microsoft.com/developer/msbuild/2003` spazio dei nomi. Di conseguenza, verranno generati XML Schema messaggi di avviso, ma è possibile ignorarli in questa procedura dettagliata.

     Per ulteriori informazioni sul contenuto dei file con *estensione vstemplate* , vedere [riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Per modificare il file ProjectTemplate. csproj o ProjectTemplate. vbproj

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *ProjectTemplate. csproj* o *ProjectTemplate. vbproj* con una delle sezioni seguenti di XML.

    - Se si sta creando un modello di progetto di Visual C#, usare il codice XML seguente.

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

    1. Se si sta creando un modello di progetto Visual Basic, usare il codice XML seguente.

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

     Il nuovo codice XML apporta le seguenti modifiche al file:

    - Usa l' `TargetFrameworkVersion` elemento per specificare il .NET Framework 3,5, non 4,5.

    - Aggiunge `SignAssembly` `AssemblyOriginatorKeyFile` elementi e per firmare l'output del progetto.

    - Aggiunge `Reference` elementi per i riferimenti ad assembly utilizzati dai progetti SharePoint.

    - Aggiunge elementi per ogni file predefinito nel progetto, ad esempio *Elements.xml* e *SharePointProjectItem. spdata*.

2. Salvare e chiudere il file.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Creare un pacchetto VSIX per distribuire il modello di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione **SiteColumnProjectItem** per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto **SiteColumnProjectItem** , aprire il file source. Extension. vsixmanifest nell'editor manifesto.

     Il file source. Extension. vsixmanifest è la base per il file Extension. vsixmanifest che tutti i pacchetti VSIX richiedono. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nella casella **nome prodotto** immettere **colonna sito**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **un progetto SharePoint per la creazione di colonne del sito**.

5. Scegliere la scheda **Asset** , quindi scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. ProjectTemplate**.

    > [!NOTE]
    > Questo valore corrisponde all' `ProjectTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di progetto. Per altre informazioni, vedere [elemento ProjectTemplate (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** , scegliere **SiteColumnProjectTemplate**, quindi scegliere il pulsante **OK** .

9. Scegliere di nuovo il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

10. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

12. Nell'elenco **progetto** scegliere **ProjectItemTypeDefinition**, quindi scegliere il pulsante **OK** .

13. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.

## <a name="test-the-project-template"></a>Testare il modello di progetto
 A questo punto è possibile eseguire il test del modello di progetto. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi il progetto della **colonna del sito** nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto SharePoint per verificare che la colonna del sito funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione SiteColumnProjectItem.

2. Nel file di codice SiteColumnProjectItemTypeProvider aggiungere un punto di interruzione alla prima riga di codice nel `InitializeType` metodo, quindi premere il tasto **F5** per avviare il debug.

     Visual Studio installa l'estensione in%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Per testare il progetto in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Espandere il nodo **Visual C#** o **Visual Basic** (a seconda della lingua supportata dal modello di progetto), espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nell'elenco dei modelli di progetto scegliere il modello **colonna sito** .

4. Nella casella **nome** immettere **SiteColumnTest** , quindi scegliere il pulsante **OK** .

     In **Esplora soluzioni**, viene visualizzato un nuovo progetto con un elemento del progetto denominato **Field1**.

5. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `InitializeType` metodo, quindi premere il tasto **F5** per continuare a eseguire il debug del progetto.

6. In **Esplora soluzioni**scegliere il nodo **Field1** , quindi premere il tasto **F4** .

     Si aprirà la finestra **Proprietà**.

7. Nell'elenco proprietà verificare che la proprietà **esempio** di proprietà sia visualizzata.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint

1. In **Esplora soluzioni**scegliere il nodo **SiteColumnTest** .

2. Nella finestra **Proprietà** , nella casella di testo accanto alla proprietà **URL sito** , immettere **http://localhost** .

     In questo passaggio viene specificato il sito di SharePoint locale nel computer di sviluppo che si desidera utilizzare per il debug.

    > [!NOTE]
    > Per impostazione predefinita, la proprietà **URL sito** è vuota perché il modello di progetto colonna del sito non fornisce una procedura guidata per la raccolta di questo valore quando viene creato il progetto. Per informazioni su come aggiungere una procedura guidata che chiede allo sviluppatore il valore e quindi configura questa proprietà nel nuovo progetto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Premere **F5**.

     La colonna del sito viene assemblata e distribuita nel sito di SharePoint specificato nella proprietà **URL sito** del progetto. Il Web browser si apre alla pagina predefinita del sito.

    > [!NOTE]
    > Se viene visualizzata la finestra di dialogo **debug script disabilitato** , scegliere il pulsante **Sì** per continuare a eseguire il debug del progetto.

4. Scegliere **Impostazioni sito**dal menu **Azioni sito** .

5. Nell'elenco **raccolte** della pagina **Impostazioni sito** scegliere il collegamento **colonne sito** .

6. Nell'elenco delle colonne del sito verificare che un gruppo di **colonne personalizzato** contenga una colonna denominata **SiteColumnTest**.

7. Chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere l'estensione della **colonna del sito** , quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si vuole disinstallare l'estensione.

4. Scegliere il pulsante **Chiudi** per completare la disinstallazione.

5. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui è aperta la soluzione SiteColumnProjectItem).

## <a name="next-steps"></a>Passaggi successivi
 Al termine di questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di progetto. Quando un utente crea un progetto di colonna del sito, la procedura guidata chiede all'utente l'URL del sito da usare per il debug e indica se la nuova soluzione è in modalità sandbox e la procedura guidata Configura il nuovo progetto con queste informazioni. La procedura guidata raccoglie inoltre informazioni sulla colonna, ad esempio il tipo di base e il gruppo in cui elencare la colonna nella raccolta di colonne del sito, e aggiunge tali informazioni al file *Elements.xml* nel nuovo progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Salvare i dati nelle estensioni del sistema di progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)