---
title: Elemento TemplateContent (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento TemplateContent e su come viene specificato il contenuto del modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a19ec1d5c615e31e62961707ad8f76f1386eb3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880658"
---
# <a name="templatecontent-element-visual-studio-templates"></a>Elemento TemplateContent (modelli di Visual Studio)

Specifica il contenuto del modello.

Gerarchia elementi:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Sintassi

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Specifica se compilare la soluzione quando viene creato un progetto dal modello.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica i file o le directory da aggiungere al progetto.|
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica i riferimenti ad assembly necessari per un modello di elemento.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Elemento facoltativo.<br /><br /> Specifica un file contenuto nel modello.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica i parametri personalizzati da usare quando un progetto o un elemento viene creato dal modello.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, il modello di elemento o starter kit.|

## <a name="remarks"></a>Commenti
 `TemplateContent` è un elemento obbligatorio.

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

- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
