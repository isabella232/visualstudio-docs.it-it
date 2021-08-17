---
title: Elemento NumberOfParentCategoriesToRollUp (modelli)
description: Informazioni sull'elemento NumberOfParentCategoriesToRollUp e su come specifica il numero di categorie padre che visualizzano il modello nella finestra di dialogo Project nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 899e5e991c998f26c46749875f3c10a7555136f89b95dc8d9c0351a734c0d722
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431669"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Elemento NumberOfParentCategoriesToRollUp (Visual Studio personalizzati)
Specifica il numero di categorie padre che visualizzano il modello nella finestra **di dialogo Project** nuovo elemento.

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
 È `integer` necessario un valore.

 Questo valore specifica il numero di categorie padre che visualizzano il modello nella finestra **di dialogo Project** nuovo elemento.

## <a name="remarks"></a>Commenti
 `NumberOfParentCategoriesToRollUp` è un elemento facoltativo.

## <a name="example"></a>Esempio
 Questo esempio illustra i metadati per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'Windows applicazione. Se un modello con questi metadati viene posizionato due livelli di cartella sotto il nodo di primo livello, il modello verrà visualizzato nel nodo di primo livello nella finestra [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] **di dialogo Project** nuovo nodo. Se non `NumberOfParentCategoriesToRollUp` è impostato, il modello viene visualizzato solo nel nodo in cui si trova fisicamente.

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

## <a name="see-also"></a>Vedi anche
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
