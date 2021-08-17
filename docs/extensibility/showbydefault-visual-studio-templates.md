---
title: Elemento ShowByDefault (Visual Studio personalizzati)
description: Informazioni sull'elemento ShowByDefault e su come, se impostato su false, specifica che il modello verrà visualizzato solo con il TemplateGroupID specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ceef636c722d950a96e522286714a50ddfd7e7422335c8934affd928357c234a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400569"
---
# <a name="showbydefault-element-visual-studio-templates"></a>Elemento ShowByDefault (Visual Studio personalizzati)
Se `false` , specifica che il modello verrà visualizzato solo nel [templateGroupID specificato.](../extensibility/templategroupid-element-visual-studio-templates.md)

 \<VSTemplate> \<TemplateData>
 \<ShowByDefault>

## <a name="syntax"></a>Sintassi

```
<ShowByDefault> true/false </ShowByDefault>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo deve essere `true` o `false`. Se true, specifica che il modello verrà visualizzato per tutti i tipi di progetto. Se false, il modello verrà visualizzato solo nel `TemplateGroupID` specificato.

## <a name="remarks"></a>Commenti
 `ShowByDefault` è un elemento facoltativo. Il valore predefinito è `true`.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ShowByDefault>false</ShowByDefault>
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
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento TemplateGroupID (modelli di Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)
