---
title: Elemento BuildProjectOnload (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento BuildProjectOnload e su come vengono compilati solo i nuovi progetti durante la creazione e l'aggiunta a una soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ca65dee11938f4152a30dedd25a3b4f3e566dd3b88e9e54da46579e30fa3243
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308363"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Elemento BuildProjectOnload (Visual Studio personalizzati)
Compila solo i nuovi progetti durante la creazione e l'aggiunta a una soluzione. L'intera soluzione non viene compilata.

Gerarchia degli elementi:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Sintassi

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
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
|`TemplateData`|Classifica il modello e ne definisce la modalità di utilizzo nelle finestre di **dialogo Project** e Aggiungi **nuovo** elemento.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere o per indicare se compilare solo il nuovo progetto quando `true` `false` viene creato dal modello.

## <a name="remarks"></a>Commenti
 `BuildProjectOnLoad` è un elemento facoltativo. Il valore predefinito è `false`.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [Attributo ed elemento BuildOnLoad](buildonload-visual-studio-templates.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
