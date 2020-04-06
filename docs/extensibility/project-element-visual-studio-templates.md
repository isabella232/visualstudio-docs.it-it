---
title: Elemento Project (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701995"
---
# <a name="project-element-visual-studio-templates"></a>Elemento Project (modelli di Visual Studio)
Specifica i file o le directory da aggiungere al progetto.

 \<> vsTemplate \<> \<TemplateContent> Project

## <a name="syntax"></a>Sintassi

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`File`|Attributo obbligatorio.<br /><br /> Specifica il nome del file di progetto nel file *.zip* del modello.|
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se il file di progetto dispone di valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome del file di progetto quando viene creato un progetto dal modello.|
|`IgnoreProjectParameter`|Attributo facoltativo.<br /><br /> Specifica se il progetto deve essere aggiunto alla soluzione corrente. Se nel file di sostituzione dei parametri è presente il valore del parametro personalizzato, ovvero *""myCustomParameter""*, il progetto viene creato ma non aggiunto come parte della soluzione attualmente aperta.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Cartella](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica una cartella da aggiungere al progetto.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica un file da aggiungere a un progetto.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.|

## <a name="remarks"></a>Osservazioni
 `Project` è un elemento figlio facoltativo di `TemplateContent`.

 L'elemento `Project` viene utilizzato per specificare un progetto e pertanto è valido solo nei modelli di progetto.

 `Project`gli elementi possono avere elementi figlio [Folder](../extensibility/folder-element-visual-studio-project-templates.md) o elementi `Folder` figlio `ProjectItem` [ProjectItem,](../extensibility/projectitem-element-visual-studio-project-templates.md) ma non una combinazione di elementi sia figlio che elementi .

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Rinomina automaticamente il nome del file di progetto in base al nome immesso dall'utente nella finestra di dialogo **Nuovo progetto.** Utilizzare `TargetFileName` l'attributo se si desidera fornire un nome di file alternativo per i file di progetto creati con il modello.

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
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (modelli di progetto Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Elemento Folder (modelli di progetto Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
