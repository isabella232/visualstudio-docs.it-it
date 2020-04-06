---
title: Elemento TemplateData (modelli di Visual Studio) Documenti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699188"
---
# <a name="templatedata-element-visual-studio-templates"></a>Elemento TemplateData (modelli di Visual Studio)
Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .

 \<> di \<VSTemplate> TemplateData

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
 No.

### <a name="child-elements"></a>Elementi figlio

| Elemento | Descrizione |
| - | - |
| [Nome](../extensibility/name-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica il nome del modello visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.** |
| [Descrizione](../extensibility/description-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica la descrizione del modello così come viene visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.** |
| [Icona](../extensibility/icon-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Specifica il percorso e il nome del file di immagine che funge da icona, visualizzata nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento,** per il modello. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Elemento obbligatorio.<br /><br /> Categorizza il modello di progetto in modo che venga visualizzato sotto il gruppo specificato nella finestra di dialogo **Nuovo progetto.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Classifica il modello di progetto in modo che venga visualizzato nella sottocategoria specificata nella finestra di dialogo **Nuovo progetto.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica l'ID del modello. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica l'ID del gruppo di modelli. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica un valore utilizzato per disporre il modello, tra gli altri modelli della stessa categoria, come viene visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.** |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se una cartella contenitore viene creata al momento della creazione di un'istanza del progetto. |
| [Nomepredefinito](../extensibility/defaultname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica il nome che il sistema del progetto di Visual Studio genererà per il progetto o l'elemento al momento della creazione. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il sistema di progetto di Visual Studio genererà il nome predefinito per un progetto o un elemento quando viene creato. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il progetto può essere creato come progetto temporaneo (solo Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il pulsante **Sfoglia** è disponibile nella finestra di dialogo **Nuovo progetto,** in modo che gli utenti possano modificare facilmente la directory predefinita in cui viene salvato un nuovo progetto. |
| [Nascosto](../extensibility/hidden-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello viene visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **Nuovo progetto.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Elemento facoltativo. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Elemento facoltativo.<br /><br /> Specifica se la casella di testo **Percorso** nella finestra di dialogo **Nuovo progetto** è abilitata, disabilitata o nascosta per il modello di progetto. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Utilizzare questo elemento se il modello supporta solo una versione minima specifica e versioni successive, se presente, di .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello supporta una pagina master per i progetti Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello supporta la separazione del codice o il modello di pagina code-behind per i progetti Web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica se il modello è identico per più lingue e se l'opzione **Lingua** è disponibile nella finestra di dialogo **Nuovo progetto.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Elemento facoltativo.<br /><br /> Specifica la piattaforma a cui è destinato il modello di progetto. Questo elemento specifica che un modello [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] di progetto viene usato per creare app. |

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, il modello di elemento o lo starter kit.|

## <a name="remarks"></a>Osservazioni
 `TemplateData`è un elemento obbligatorio.

 Se non si include un elemento facoltativo, viene utilizzato il valore predefinito per tale elemento.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadati per un modello di progetto per un'applicazione.

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
