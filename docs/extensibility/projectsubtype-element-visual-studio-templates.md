---
title: Elemento ProjectSubType (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701836"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelli di Visual Studio)
Classifica il modello in una sottocategoria del `ProjectType` valore specificato nell'elemento.

 \<Template> \<TemplateData \<> ProjectSubType>

## <a name="syntax"></a>Sintassi

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo valore specifica la sottocategoria del modello.

## <a name="remarks"></a>Osservazioni
 `ProjectSubType` è un elemento figlio facoltativo di `TemplateData`.

 L'elemento `ProjectSubType` fornisce una sottocategoria per il [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Questo valore può includere:

- `SmartDevice-NETCFv1`: specifica che il [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] modello è destinato alla versione 1.0.

- `SmartDevice-NETCFv2`: specifica che il [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] modello è destinato alla versione 2.0.

  Se un modello `ProjectType` contiene un `Web`elemento `ProjectSubType` con un valore pari a , l'elemento specifica il linguaggio di programmazione del modello. Questo elemento può avere i seguenti valori:

- `CSharp`: specifica che il [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello crea un progetto Web o un elemento.

- `VisualBasic`: specifica che il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] modello crea un progetto Web o un elemento.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadati per [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] un modello di progetto per un'applicazione per dispositivi destinata alla versione 2.0.The following example shows the metadata for a project template for a device application targeting the version 2.0.

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectType (modelli di Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
