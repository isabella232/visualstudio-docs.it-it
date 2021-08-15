---
title: Elemento SolutionFolder (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento SolutionFolder e sul modo in cui raggruppa i progetti in modelli multi-progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c8865456b5b25b2f65a839bd947f558e803803533c7aa58f51f6bf01aa0a679
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273604"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>Elemento SolutionFolder (modelli di Visual Studio)
Raggruppa i progetti in modelli multiprogetto.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>

## <a name="syntax"></a>Sintassi

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome della cartella della soluzione.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.|
|`SolutionFolder`|Elemento facoltativo.<br /><br /> Raggruppa i progetti in modelli multiprogetto.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|
|`SolutionFolder`|Raggruppa i progetti in modelli multiprogetto.|

## <a name="remarks"></a>Commenti
 I modelli multiprogetto fungono da contenitori per due o più progetti. L'elemento `SolutionFolder` viene usato per organizzare i progetti in gruppi all'interno del modello. Le cartelle specificate dagli elementi `SolutionFolder` vengono create come cartelle della soluzione nel progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni sui modelli multi-progetto, vedere Procedura: Creare modelli [multi-Project multi-progetto](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Esempio
 Questo esempio usa l'elemento `SolutionFolder` per dividere il modello multiprogetto in due gruppi, `Math Classes` e `Graphics Classes`. Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md)
