---
title: Project Elemento (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'Project e su come specifica i file o le directory da aggiungere al progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 260b52b23be9857cc3850824b3eda8fe795abb701c21788df7b487ae6f5e111c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388539"
---
# <a name="project-element-visual-studio-templates"></a>Project elemento (modelli Visual Studio)
Specifica i file o le directory da aggiungere al progetto.

 \<VSTemplate> \<TemplateContent>
 \<Project>

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
|`File`|Attributo obbligatorio.<br /><br /> Specifica il nome del file di progetto nel modello *.zip* file.|
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se il file di progetto ha valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome del file di progetto quando viene creato un progetto dal modello.|
|`IgnoreProjectParameter`|Attributo facoltativo.<br /><br /> Specifica se il progetto deve essere aggiunto alla soluzione corrente. Se il valore del parametro personalizzato "$*myCustomParameter*$" esiste nel file di sostituzione dei parametri, il progetto viene creato ma non aggiunto come parte della soluzione attualmente aperta.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Cartella](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica una cartella da aggiungere al progetto.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica un file da aggiungere a un progetto.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.|

## <a name="remarks"></a>Commenti
 `Project` è un elemento figlio facoltativo di `TemplateContent`.

 `Project`L'elemento viene usato per specificare un progetto e pertanto è valido solo nei modelli di progetto.

 `Project` Gli elementi possono avere [elementi figlio Folder](../extensibility/folder-element-visual-studio-project-templates.md) o elementi figlio [ProjectItem,](../extensibility/projectitem-element-visual-studio-project-templates.md) ma non una combinazione di elementi `Folder` figlio e `ProjectItem` .

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]rinomina automaticamente il nome del file di progetto in base al nome immesso dall'utente nella finestra **di dialogo Project** nuova cartella. Usare `TargetFileName` l'attributo se si vuole specificare un nome file alternativo per i file di progetto creati con il modello.

## <a name="example"></a>Esempio
 L'esempio seguente mostra i metadati per un modello di progetto per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'applicazione.

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
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (Visual Studio di progetto)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Elemento Folder (Visual Studio di progetto)](../extensibility/folder-element-visual-studio-project-templates.md)
