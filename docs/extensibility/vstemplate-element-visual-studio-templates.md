---
title: Elemento VSTemplate (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento VSTemplate e su come contiene tutti i metadati relativi al modello di progetto, al modello di elemento o starter kit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f15b21ccb52cf7aa7c857c0b6b523c02fd65461
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905735"
---
# <a name="vstemplate-element-visual-studio-templates"></a>Elemento VSTemplate (modelli di Visual Studio)
Contiene tutti i metadati relativi al modello di progetto, al modello di elemento o starter kit.

## <a name="syntax"></a>Sintassi

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

| Attributo | Descrizione |
|-----------| - |
| `Type` | Identifica il modello come modello di progetto o modello di elemento. Questo attributo può avere un valore di `Project` o `Item` . |
| `Version` | Specifica un numero di versione per il modello. I modelli in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] hanno un `Version` valore di attributo pari a `3.0.0` . |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica i dati che categorizzano il modello e ne definisce la modalità di visualizzazione nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il contenuto del modello.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Elemento facoltativo.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Elemento facoltativo.|

### <a name="parent-elements"></a>Elementi padre
 No.

## <a name="remarks"></a>Osservazioni
 L' `VSTemplate` elemento è l'elemento radice dei file con *estensione vstemplate* .

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione.

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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
