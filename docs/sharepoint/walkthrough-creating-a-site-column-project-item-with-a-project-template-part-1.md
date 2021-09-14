---
title: Creare un elemento di progetto colonna del sito con il modello di progetto, parte 1
titleSuffix: ''
description: Definire un tipo di elemento di progetto per la creazione di una colonna del sito e quindi creare un modello di progetto da usare per creare un progetto SharePoint che contiene l'elemento di progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6ede65c0360a747c21d640e15b28c8b1dffe0583
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711403"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1
  SharePoint sono contenitori per uno o più SharePoint di progetto. È possibile estendere il SharePoint di progetto in Visual Studio creando tipi di elemento di progetto SharePoint personalizzati e quindi associandoli a un modello di progetto. In questa procedura dettagliata si definirà un tipo di elemento di progetto per la creazione di una colonna del sito e quindi si creerà un modello di progetto che può essere usato per creare un nuovo progetto che contiene un elemento di progetto colonna del sito.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di Visual Studio'estensione che definisce un nuovo tipo di SharePoint di progetto per una colonna del sito. Il tipo di elemento del progetto include una semplice proprietà personalizzata che viene visualizzata nella **finestra** Proprietà.

- Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto per l'elemento di progetto.

- Compilazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] un pacchetto di estensione (VSIX) per distribuire il modello di progetto e l'assembly dell'estensione.

- Debug e test dell'elemento di progetto.

  Questa è una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento del progetto aggiungendo una procedura guidata al modello di progetto. Per altre informazioni, vedere Procedura dettagliata: Creare un elemento di progetto colonna [del sito con un modello di progetto, parte 2.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)

> [!NOTE]
> Per una serie di flussi di lavoro di esempio, vedere SharePoint [di flusso di lavoro.](/sharepoint/dev/general-development/sharepoint-workflow-samples)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Microsoft Windows, SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Oggetto [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza del concetto seguente è utile, ma non necessaria, per completare la procedura dettagliata:

- Colonne del sito in SharePoint. Per altre informazioni, vedere [Colonne.](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

- Project modelli in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'elemento di progetto colonna del sito e il modello di progetto.

- Un progetto di modello di progetto. Questo progetto crea un modello di progetto che può essere usato per creare un nuovo SharePoint che contiene l'elemento di progetto colonna del sito.

- Un progetto di libreria di classi. Progetto che implementa un'estensione Visual Studio che definisce il comportamento dell'elemento di progetto colonna del sito.

  Iniziare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

3. Nella parte superiore della finestra **di dialogo Nuovo** Project verificare che sia selezionata la versione .NET Framework **4.5** nell'elenco delle versioni del .NET Framework.

4. Espandere i **Visual Basic** o **Visual C#** e quindi scegliere il nodo **Extensibility.**

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

5. Nell'elenco dei modelli di progetto scegliere **VSIX Project**.

6. Nella casella **Nome** immettere **SiteColumnProjectItem** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto SiteColumnProjectItem** **Esplora soluzioni**.

#### <a name="to-create-the-project-template-project"></a>Per creare il progetto modello di progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

2. Nella parte superiore della finestra **di dialogo Nuovo** Project verificare che sia selezionata la versione .NET Framework **4.5** nell'elenco delle versioni del .NET Framework.

3. Espandere il **nodo Visual C#** **Visual Basic** e quindi scegliere il **nodo Extensibility.**

4. Nell'elenco dei modelli di progetto scegliere il modello **di Project C#** **o Visual Basic Project modello.**

5. Nella casella **Nome** immettere **SiteColumnProjectTemplate** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto SiteColumnProjectTemplate** alla soluzione.

6. Eliminare il file di codice Class1 dal progetto.

7. Se è stato creato Visual Basic progetto, eliminare anche i file seguenti dal progetto:

    - *MyApplication.Designer.vb*

    - MyApplication.myapp

    - *Resources.Designer.vb*

    - *Resources.resx*

    - *Impostazioni. Designer.vb*

    - Impostazioni.settings

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

2. Nella parte superiore della finestra **di dialogo Nuovo** Project verificare che sia selezionata la versione .NET Framework **4.5** nell'elenco delle versioni del .NET Framework.

3. Espandere i **nodi visual c#** **o Visual Basic,** scegliere il nodo **Windows** e quindi scegliere il modello **Libreria di** classi.

4. Nella casella **Nome** immettere **ProjectItemTypeDefinition** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ProjectItemTypeDefinition** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Aggiungere file di codice e riferimenti ad assembly per configurare il progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto ProjectItemTypeDefinition aggiungere un file di codice denominato **SiteColumnProjectItemTypeProvider.**

2. Sulla barra dei menu scegliere **Project**  >  **Aggiungi riferimento**.

3. Nella finestra di dialogo Gestione riferimenti **- ProjectItemTypeDefinition** espandere il nodo **Assembly,** scegliere il nodo **Framework** e quindi selezionare la casella di controllo System.ComponentModel.Composition .

4. Scegliere il **nodo** Estensioni e selezionare la casella di controllo accanto a Microsoft.VisualStudio. SharePoint assembly e quindi scegliere **il pulsante OK.**

## <a name="define-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo SharePoint di elemento di progetto
 Creare una classe che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di elemento di progetto.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di SharePoint progetto

1. Nel file **di codice SiteColumnProjectItemTypeProvider** sostituire il codice predefinito con il codice seguente e quindi salvare il file.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb" id="Snippet1":::

## <a name="create-a-visual-studio-project-template"></a>Creare un modello Visual Studio progetto
 Creando un modello di progetto, si consente ad altri sviluppatori di creare SharePoint che contengono elementi di progetto della colonna del sito. Un modello di progetto SharePoint include i file necessari per tutti i progetti in Visual Studio, ad esempio i file con estensione *csproj* o *vbproj* e *vstemplate,* e i file specifici di SharePoint progetto. Per altre informazioni, vedere [Creare modelli di elemento e modelli di progetto per SharePoint di progetto.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 In questa procedura viene creato un progetto SharePoint vuoto per generare i file specifici per SharePoint progetto. Questi file vengono quindi aggiunti al progetto SiteColumnProjectTemplate in modo che siano inclusi nel modello generato da questo progetto. È anche possibile configurare il file di progetto SiteColumnProjectTemplate per specificare dove viene visualizzato il modello di progetto nella finestra **di dialogo Project** nuovo progetto.

#### <a name="to-create-the-files-for-the-project-template"></a>Per creare i file per il modello di progetto

1. Avviare una seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative.

2. Creare un SharePoint 2010 denominato **BaseSharePointProject.**

   > [!IMPORTANT]
   > Nella **Personalizzazione guidata SharePoint** non selezionare il pulsante di opzione Distribuisci come **soluzione farm.**

3. Aggiungere un elemento Empty Element al progetto e quindi assegnare all'elemento il nome **Field1**.

4. Salvare il progetto e quindi chiudere la seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. Nell'istanza di in cui è aperta la soluzione SiteColumnProjectItem, in Esplora soluzioni aprire il menu di scelta rapida per il nodo del progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **SiteColumnProjectTemplate,** scegliere Aggiungi e quindi elemento **esistente.** 

6. Nella finestra **di dialogo Aggiungi elemento** esistente aprire l'elenco delle estensioni di file e quindi scegliere Tutti i file ( . **\* \* )**.

7. Nella directory che contiene il progetto BaseSharePointProject selezionare il file key.snk e quindi scegliere il **pulsante** Aggiungi.

   > [!NOTE]
   > In questa procedura dettagliata il modello di progetto creato usa lo stesso file key.snk per firmare ogni progetto creato usando il modello. Per informazioni su come espandere questo esempio per creare un file key.snk diverso per ogni istanza del progetto, vedere Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di [progetto, parte 2.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)

8. Ripetere i passaggi da 5 a 8 per aggiungere i file seguenti dalle sottocartelle specificate nella directory BaseSharePointProject:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Aggiungere questi file direttamente al progetto SiteColumnProjectTemplate. non ricreare le sottocartelle Field1, Features o Package nel progetto. Per altre informazioni su questi file, vedere [Creare modelli di elemento](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)e modelli di progetto per SharePoint di progetto .

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Per configurare il modo in cui gli sviluppatori individuano il modello di progetto nella finestra di dialogo Project progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto **SiteColumnProjectTemplate** e quindi scegliere **Scarica** Project . Se viene richiesto di salvare le modifiche apportate a qualsiasi file, scegliere **il pulsante** Sì.

2. Aprire di nuovo il menu di scelta rapida per il nodo **SiteColumnProjectTemplate** e quindi scegliere **Modifica SiteColumnProjectTemplate.csproj** o **Modifica SiteColumnProjectTemplate.vbproj.**

3. Nel file di progetto individuare l'elemento `VSTemplate` seguente.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Sostituisci l'elemento con il codice XML seguente.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L'elemento specifica cartelle aggiuntive nel percorso in cui viene creato il modello `OutputSubPath` di progetto quando si compila il progetto. Le cartelle specificate qui garantiscono che il modello di progetto sia disponibile solo quando i clienti aprono la finestra di dialogo Nuovo **Project,** espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

5. Salvare e chiudere il file.

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto SiteColumnProjectTemplate** e quindi scegliere **Ricarica** Project .

## <a name="edit-the-project-template-files"></a>Modificare i file del modello di progetto
 Nel progetto SiteColumnProjectTemplate modificare i file seguenti per definire il comportamento del modello di progetto:

- *AssemblyInfo.cs o* *AssemblyInfo.vb*

- *Elements.xml*

- *SharePointProjectItem.spdata*

- *Feature1.feature*

- *Package.package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate.csproj* o *ProjectTemplate.vbproj*

  Nelle procedure seguenti si aggiungeranno parametri sostituibili ad alcuni di questi file. Un parametro sostituibile è un token che inizia e termina con il simbolo del dollaro ($). Quando un utente usa questo modello di progetto per creare un progetto, Visual Studio automaticamente questi parametri nel nuovo progetto con valori specifici. Per altre informazioni, vedere [Parametri sostituibili.](../sharepoint/replaceable-parameters.md)

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Per modificare il file AssemblyInfo.cs o AssemblyInfo.vb

1. Nel progetto SiteColumnProjectTemplate aprire il file *AssemblyInfo.cs* o *AssemblyInfo.vb* e quindi aggiungere l'istruzione seguente all'inizio:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Quando la **proprietà Sandboxed Solution** di un progetto SharePoint è impostata su **True,** Visual Studio aggiunge al file di codice <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo. Tuttavia, il file di codice AssemblyInfo nel modello di progetto non importa lo spazio dei <xref:System.Security> nomi per impostazione predefinita. È necessario aggiungere questa istruzione **using** o **Imports** per evitare errori di compilazione.

2. Salvare e chiudere il file.

#### <a name="to-edit-the-elementsxml-file"></a>Per modificare il file Elements.xml

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Elements.xml* con il codice XML seguente.

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

     Il nuovo codice XML aggiunge un elemento che definisce il nome della colonna del sito, il relativo tipo di base e il gruppo in cui elencare la `Field` colonna del sito nella raccolta. Per altre informazioni sul contenuto di questo file, vedere [Field Definition Schema](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Per modificare il file SharePointProjectItem.spdata

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *SharePointProjectItem.spdata* con il codice XML seguente.

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

   - Modifica l'attributo dell'elemento nella stessa stringa passata a nella definizione dell'elemento di progetto (la classe creata in precedenza `Type` `ProjectItem` in questa procedura <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> `SiteColumnProjectItemTypeProvider` dettagliata).

   - Rimuove gli `SupportedTrustLevels` attributi `SupportedDeploymentScopes` e `ProjectItem` dall'elemento . Questi valori di attributo non sono necessari perché i livelli di attendibilità e gli ambiti di distribuzione sono specificati nella `SiteColumnProjectItemTypeProvider` classe nel progetto ProjectItemTypeDefinition.

     Per altre informazioni sul contenuto dei file *con estensione spdata,* vedere informazioni di riferimento sullo schema SharePoint [elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-feature1feature-file"></a>Per modificare il file Feature1.feature

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Feature1.feature* con il codice XML seguente.

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

   - Modifica i valori degli `Id` attributi `featureId` e `feature` dell'elemento in `$guid4$` .

   - Modifica i valori `itemId` dell'attributo `projectItemReference` dell'elemento in `$guid2$` .

     Per altre informazioni sui *file con estensione feature,* vedere Creare modelli di elemento e modelli di [progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-packagepackage-file"></a>Per modificare il file Package.package

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Package.package* con il codice XML seguente.

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

   - Modifica i valori degli `Id` attributi `solutionId` e `package` dell'elemento in `$guid3$` .

   - Modifica i valori `itemId` dell'attributo `featureReference` dell'elemento in `$guid4$` .

     Per altre informazioni sui *file con estensione package,* vedere [Creare modelli di elemento](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)e modelli di progetto per SharePoint di progetto .

2. Salvare e chiudere il file.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Per modificare il file sitecolumnprojecttemplate.vstemplate

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file SiteColumnProjectTemplate.vstemplate con una delle sezioni seguenti di XML.

   - Se si crea un modello di progetto Visual C#, usare il codice XML seguente.

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

   - Se si crea un modello di Visual Basic progetto, usare il codice XML seguente.

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

   - Imposta `Name` l'elemento sul valore **Site Column**. Questo nome viene visualizzato nella **finestra di dialogo Nuovo Project.**

   - Aggiunge `ProjectItem` elementi per ogni file incluso in ogni istanza del progetto.

   - Usa lo spazio dei nomi `http://schemas.microsoft.com/developer/vstemplate/2005` . Altri file di progetto in questa soluzione usano lo spazio dei `http://schemas.microsoft.com/developer/msbuild/2003` nomi . Verranno pertanto generati messaggi di avviso di XML Schema, ma è possibile ignorarli in questa procedura dettagliata.

     Per altre informazioni sul contenuto dei file con estensione *vstemplate,* vedere riferimento Visual Studio [schema del modello](../extensibility/visual-studio-template-schema-reference.md).

2. Salvare e chiudere il file.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Per modificare il file projecttemplate.csproj o projecttemplate.vbproj

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *ProjectTemplate.csproj* o *ProjectTemplate.vbproj* con una delle sezioni seguenti di XML.

    - Se si crea un modello di progetto Visual C#, usare il codice XML seguente.

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

    1. Se si crea un modello di Visual Basic progetto, usare il codice XML seguente.

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

    - Usa `TargetFrameworkVersion` l'elemento per specificare il .NET Framework 3.5, non 4.5.

    - Aggiunge `SignAssembly` gli elementi e per firmare `AssemblyOriginatorKeyFile` l'output del progetto.

    - Aggiunge `Reference` elementi per i riferimenti all'assembly SharePoint i progetti.

    - Aggiunge elementi per ogni file predefinito nel progetto, ad esempio *Elements.xml* *e SharePointProjectItem.spdata*.

2. Salvare e chiudere il file.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Creare un pacchetto VSIX per distribuire il modello di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella **soluzione SiteColumnProjectItem** per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** nel progetto **SiteColumnProjectItem** aprire il file source.extension.vsixmanifest nell'editor manifesto.

     Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere **Site Column (Colonna sito).**

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **un progetto SharePoint per la creazione di colonne del sito.**

5. Scegliere la **scheda Asset** e quindi fare clic **sul pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.ProjectTemplate**.

    > [!NOTE]
    > Questo valore corrisponde `ProjectTemplate` all'elemento nel file extension.vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di progetto. Per altre informazioni, vedere [Elemento ProjectTemplate (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\))

7. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

8. **Nell'Project** e scegliere **SiteColumnProjectTemplate** e quindi fare clic sul **pulsante OK.**

9. Scegliere di **nuovo il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

10. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

11. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

12. **Nell'Project** scegliere **ProjectItemTypeDefinition** e quindi fare clic sul **pulsante OK.**

13. Sulla barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che  >  il progetto venga compilato senza errori.

## <a name="test-the-project-template"></a>Testare il modello di progetto
 A questo punto è possibile testare il modello di progetto. Avviare prima di tutto il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi il **progetto Site Column** nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il SharePoint per verificare che la colonna del sito funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.

2. Nel file di codice SiteColumnProjectItemTypeProvider aggiungere un punto di interruzione alla prima riga di codice nel metodo e quindi premere F5 per avviare `InitializeType` il debug. 

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. L'elemento di progetto verrà testato in questa istanza di Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Per testare il progetto in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **File**  >  **nuovo**  >  **Project**.

2. Espandere il nodo **Visual C#** **o Visual Basic** (a seconda del linguaggio che supporta il modello di progetto), espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

3. Nell'elenco dei modelli di progetto scegliere il **modello Colonna** sito.

4. Nella casella **Nome** immettere **SiteColumnTest** e quindi scegliere **il pulsante OK.**

     In **Esplora soluzioni** viene visualizzato un nuovo progetto con un elemento di progetto denominato **Field1.**

5. Verificare che il codice nell'altra istanza di Visual Studio si arresti nel punto di interruzione impostato in precedenza nel metodo e quindi scegliere F5 per continuare a eseguire il `InitializeType` debug del progetto. 

6. In **Esplora soluzioni** scegliere il **nodo Field1** e quindi premere **F4.**

     Si aprirà la finestra **Proprietà**.

7. Nell'elenco delle proprietà verificare che sia visualizzata la proprietà **Example Property.**

#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint

1. In **Esplora soluzioni** scegliere il **nodo SiteColumnTest.**

2. Nella casella **di** testo accanto alla proprietà **URL** sito della finestra Proprietà immettere **http://localhost** .

     Questo passaggio specifica il sito SharePoint locale nel computer di sviluppo che si vuole usare per il debug.

    > [!NOTE]
    > La **proprietà URL sito** è vuota per impostazione predefinita perché il modello di progetto Colonna sito non fornisce una procedura guidata per raccogliere questo valore quando viene creato il progetto. Per informazioni su come aggiungere una procedura guidata che richiede questo valore allo sviluppatore e quindi configura questa proprietà nel nuovo progetto, vedere Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di [progetto, parte 2.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)

3. Premere **F5**.

     La colonna del sito viene in pacchetto e distribuita nel SharePoint specificato nella proprietà **URL** sito del progetto. Il Web browser si apre alla pagina predefinita di questo sito.

    > [!NOTE]
    > Se viene **visualizzata la finestra di** dialogo Debug script disabilitato , scegliere il **pulsante** Sì per continuare a eseguire il debug del progetto.

4. Nel menu **Azioni sito** scegliere Sito **Impostazioni**.

5. Nella pagina **Impostazioni** sito scegliere il collegamento Colonne sito **nell'elenco** **Raccolte.**

6. Nell'elenco delle colonne del sito verificare che un **gruppo Colonne** personalizzate contenga una colonna denominata **SiteColumnTest**.

7. Chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il test del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Estensioni**  >  **e aggiornamenti degli strumenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **l'estensione Colonna** del sito e quindi scegliere il **pulsante Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere **il** pulsante Sì per confermare la disinstallazione dell'estensione.

4. Scegliere il **pulsante** Chiudi per completare la disinstallazione.

5. Chiudere entrambe le istanze di Visual Studio (istanza sperimentale e istanza di Visual Studio in cui è aperta la soluzione SiteColumnProjectItem).

## <a name="next-steps"></a>Passaggi successivi
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di progetto. Quando un utente crea un progetto colonna del sito, la procedura guidata chiede all'utente l'URL del sito da usare per il debug e se la nuova soluzione è in modalità sandbox e la procedura guidata configura il nuovo progetto con queste informazioni. La procedura guidata raccoglie anche informazioni sulla colonna, ad esempio il tipo di base e il gruppo in cui elencare la colonna nella raccolta colonne del sito, e aggiunge queste informazioni al file *Elements.xml* nel nuovo progetto. Per altre informazioni, vedere Procedura dettagliata: Creare un elemento di progetto di colonna [del sito con un modello di progetto, parte 2.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Salvare i dati nelle estensioni del sistema SharePoint progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associare dati personalizzati ad SharePoint tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)