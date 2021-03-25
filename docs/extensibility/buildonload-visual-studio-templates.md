---
title: Attributo ed elemento di BuildOnLoad (modelli di Visual Studio)
titleSuffix: ''
description: Informazioni sull'elemento e sull'attributo BuildOnLoad e su come viene specificato se compilare il progetto immediatamente dopo la creazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8eb563e765c3d50950f61a0ca49e5349a0e7249a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068180"
---
# <a name="buildonload-attribute-and-element"></a>Attributo ed elemento di BuildOnLoad

Specifica se compilare il progetto immediatamente dopo la creazione. **BuildOnLoad** è un attributo e un elemento.

Gerarchia elementi:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Sintassi degli elementi

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo

Per l'elemento **BuildOnLoad** è necessario un valore di testo. Il testo deve essere `true` o `false` , che indica se compilare il progetto immediatamente dopo che è stato creato.

## <a name="remarks"></a>Commenti

**BuildOnLoad** è un attributo facoltativo. Il valore predefinito è `false`.

## <a name="example"></a>Esempio

L'esempio seguente illustra i metadati per un modello C# quando **BuildOnLoad** viene usato come elemento:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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

- [Elemento BuildProjectOnload](buildprojectonload-element-visual-studio-templates.md)
- [Elemento TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
