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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702365"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Elemento NumberOfParentCategoriesToRollUp (modelli di Visual Studio)
Specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **nuovo progetto** .

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Sintassi

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
 `integer`È necessario specificare un valore.

 Questo valore specifica il numero di categorie padre che visualizzeranno il modello nella finestra di dialogo **nuovo progetto** .

## <a name="remarks"></a>Osservazioni
 `NumberOfParentCategoriesToRollUp` è un elemento facoltativo.

## <a name="example"></a>Esempio
 In questo esempio vengono illustrati i metadati per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows. Se un modello con questi metadati viene inserito a due livelli di cartella al di sotto del nodo di primo livello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , il modello verrà visualizzato nel nodo di primo livello della finestra di dialogo **nuovo progetto** . Se `NumberOfParentCategoriesToRollUp` non è impostato, il modello viene visualizzato solo nel nodo in cui si trova fisicamente.

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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
