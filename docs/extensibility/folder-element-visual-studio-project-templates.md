---
title: Elemento Folder (modelli Visual Studio Project) | Microsoft Docs
description: Informazioni sull'elemento Folder e su come specifica una cartella che verrà aggiunta al progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f06f0a5323073304bda5126351ad07373be66ae39a3947e5fb95c553f827b674
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432631"
---
# <a name="folder-element-visual-studio-project-templates"></a>Elemento Folder (Visual Studio di progetto)
Specifica una cartella che verrà aggiunta al progetto.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

## <a name="syntax"></a>Sintassi

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome della cartella del progetto.|
|`TargetFolderName`|Attributo facoltativo.<br /><br /> Specifica il nome da assegnare alla cartella quando viene creato un progetto dal modello. Questo attributo è utile per usare la sostituzione dei parametri per creare un nome di cartella o denominare una cartella con una stringa internazionale che non può essere usata direttamente nel file *.zip.*|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|`Folder`|Specifica una cartella da aggiungere al progetto. `Folder` Gli elementi possono contenere elementi `Folder` figlio.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Specifica un file da aggiungere al progetto.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Elemento figlio facoltativo di [TemplateContent.](../extensibility/templatecontent-element-visual-studio-templates.md)|

## <a name="remarks"></a>Commenti
 `Folder` è un elemento figlio facoltativo di `Project` .

 È possibile usare uno dei metodi seguenti per organizzare gli elementi di progetto in cartelle in un modello:

- Includere le cartelle nel file *.zip* modello e aggiungerle al progetto nel file con estensione *vstemplate* specificando il percorso del file negli elementi , senza `ProjectItem` elementi `Folder` . Questo è il metodo consigliato. Esempio:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Includere le cartelle nel file *.zip* modello e aggiungerle al progetto nel file con estensione *vstemplate* con `Folder` elementi . Esempio:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Non includere cartelle nel file *.zip* modello, ma aggiungere cartelle usando `TargetFileName` l'attributo `ProjectItem` dell'elemento . Esempio:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metadati per un modello di progetto per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'Windows applicazione.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
