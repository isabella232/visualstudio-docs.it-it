---
title: Elemento NumberOfParentCategoriesToRollUp (modelli)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b903b9d0bdab2c17dd2e489de01badad82c15473
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702365"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Elemento NumberOfParentCategoriesToRollUp (modelli di Visual Studio)
Specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **Nuovo progetto.**

 \<> di \<VSTemplate \<> Template>Data

## <a name="syntax"></a>Sintassi

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È `integer` necessario un valore.

 Questo valore specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **Nuovo progetto.**

## <a name="remarks"></a>Osservazioni
 `NumberOfParentCategoriesToRollUp` è un elemento facoltativo.

## <a name="example"></a>Esempio
 In questo esempio vengono [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] illustrati i metadati per un'applicazione Windows.This example illustrates the metadata for a Windows application. Se un modello con questi metadati viene [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] posizionato due livelli di cartella sotto il nodo di primo livello, il modello verrà visualizzato nel nodo di primo livello nella finestra di dialogo **Nuovo progetto.** Se `NumberOfParentCategoriesToRollUp` l'oggetto non è impostato, il modello viene visualizzato solo nel nodo in cui si trova fisicamente.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
