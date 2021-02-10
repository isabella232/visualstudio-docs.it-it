---
title: Elemento Project (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento Project e sul modo in cui specifica i file o le directory da aggiungere al progetto.
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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8373501f324882c541784c6786b6b9f04a76069
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959454"
---
# <a name="project-element-visual-studio-templates"></a>Elemento Project (modelli di Visual Studio)
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
|`File`|Attributo obbligatorio.<br /><br /> Specifica il nome del file di progetto nel file con *estensione zip* del modello.|
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se il file di progetto contiene valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome del file di progetto quando viene creato un progetto dal modello.|
|`IgnoreProjectParameter`|Attributo facoltativo.<br /><br /> Specifica se il progetto deve essere aggiunto alla soluzione corrente. Se il valore del parametro personalizzato "$*myCustomParameter*$" è presente nel file di sostituzione dei parametri, il progetto viene creato ma non aggiunto come parte della soluzione attualmente aperta.|

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

 L' `Project` elemento viene usato per specificare un progetto e pertanto è valido solo nei modelli di progetto.

 `Project` gli elementi possono contenere elementi figlio della [cartella](../extensibility/folder-element-visual-studio-project-templates.md) o elementi figlio [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) , ma non una combinazione `Folder` di `ProjectItem` elementi figlio e.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Rinomina automaticamente il nome del file di progetto in base al nome immesso dall'utente nella finestra di dialogo **nuovo progetto** . Utilizzare l' `TargetFileName` attributo se si desidera fornire un nome file alternativo per i file di progetto creati con il modello.

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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (modelli di progetto di Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Elemento Folder (modelli di progetto di Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
