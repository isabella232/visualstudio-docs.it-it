---
title: Elemento ProjectSubType (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento ProjectSubType e su come classificare il modello in una sottocategoria del valore specificato nell'elemento ProjectType.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02dd5573de12e4626c267fa014f6c7fc8f243b72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068676"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelli di Visual Studio)
Classifica il modello in una sottocategoria del valore specificato nell' `ProjectType` elemento.

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Sintassi

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo valore specifica la sottocategoria del modello.

## <a name="remarks"></a>Commenti
 `ProjectSubType` è un elemento figlio facoltativo di `TemplateData`.

 L' `ProjectSubType` elemento fornisce una sottocategoria all'elemento [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) . Questo valore può includere:

- `SmartDevice-NETCFv1`: Specifica che il modello è destinato alla [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 1,0.

- `SmartDevice-NETCFv2`: Specifica che il modello è destinato alla [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2,0.

  Se un modello contiene un `ProjectType` elemento con un valore `Web` , l' `ProjectSubType` elemento specifica il linguaggio di programmazione del modello. Questo elemento può avere i valori seguenti:

- `CSharp`: Specifica che il modello crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto Web o un elemento.

- `VisualBasic`: Specifica che il modello crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto Web o un elemento.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione del dispositivo destinata alla [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2,0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectType (modelli di Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
