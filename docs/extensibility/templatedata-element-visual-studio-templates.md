---
title: Elemento TemplateData (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento TemplateData e su come categorizzare il modello e definire come viene visualizzato nella finestra di dialogo nuovo progetto o Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 423bcc7b3d902488f268b2d0706cb5126125f37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895388"
---
# <a name="templatedata-element-visual-studio-templates"></a>Elemento TemplateData (modelli di Visual Studio)
Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Sintassi

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio

| Elemento | Descrizione |
| - | - |
| [Nome](../extensibility/name-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica il nome del modello visualizzato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** . |
| [Descrizione](../extensibility/description-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica la descrizione del modello come appare nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** . |
| [Icona](../extensibility/icon-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica il percorso e il nome del file di immagine che funge da icona, che viene visualizzata nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** per il modello. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Categorizza il modello di progetto in modo che venga visualizzato sotto il gruppo specificato nella finestra di dialogo **nuovo progetto** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Classifica il modello di progetto in modo che venga visualizzato sotto la sottocategoria specificata nella finestra di dialogo **nuovo progetto** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica l'ID del modello. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica l'ID del gruppo di modelli. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica un valore utilizzato per disporre il modello, tra gli altri modelli nella stessa categoria, così come viene visualizzato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** . |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se viene creata una cartella contenitore durante la creazione dell'istanza del progetto. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica il nome che verrà generato dal sistema di progetto di Visual Studio per il progetto o l'elemento al momento della creazione. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il sistema di progetto di Visual Studio genererà il nome predefinito per un progetto o un elemento al momento della creazione. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il progetto può essere creato come progetto temporaneo (solo Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il pulsante **Sfoglia** è disponibile nella finestra di dialogo **nuovo progetto** , in modo che gli utenti possano modificare facilmente la directory predefinita in cui viene salvato un nuovo progetto. |
| [Hidden](../extensibility/hidden-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello viene visualizzato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** . |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **nuovo progetto** . |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Elemento facoltativo. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Elemento facoltativo.<br /><br /> Specifica se la casella di testo **percorso** nella finestra di dialogo **nuovo progetto** è abilitata, disabilitata o nascosta per il modello di progetto. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Utilizzare questo elemento se il modello supporta solo una versione minima specifica e versioni successive del .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello supporta una pagina master per i progetti Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello supporta la separazione del codice o il modello di pagina code-behind per i progetti Web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello è identico per più lingue e se l'opzione **lingua** è disponibile nella finestra di dialogo **nuovo progetto** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica la piattaforma a cui è destinato il modello di progetto. Questo elemento specifica che viene usato un modello di progetto per creare [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app. |

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, il modello di elemento o starter kit.|

## <a name="remarks"></a>Commenti
 `TemplateData` è un elemento obbligatorio.

 Se non si include un elemento facoltativo, viene utilizzato il valore predefinito di tale elemento.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
