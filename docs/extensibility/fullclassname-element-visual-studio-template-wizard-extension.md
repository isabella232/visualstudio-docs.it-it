---
title: Elemento FullClassName (estensione della creazione guidata modello di Visual Studio)
description: Informazioni sull'elemento FullClassName e su come è il nome completo della classe che implementa l'interfaccia IWizard.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27b719e153d3545dca0c0c113c173a238bd5901e0a72b94e7740e1c7aed5bac0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360001"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Elemento FullClassName (estensione Visual Studio modello)
Nome completo della classe che implementa `IWizard` l'interfaccia .

 \<VSTemplate> \<WizardExtension>
... \<FullClassName>

## <a name="syntax"></a>Sintassi

```xml
<FullClassName>ClassName</FullClassName>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene gli elementi di registrazione per la personalizzazione della procedura guidata del modello.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica la classe che implementa `IWizard` l'interfaccia . La classe specificata deve esistere nell'assembly specificato [dall'elemento Assembly.](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)

## <a name="remarks"></a>Commenti
 `FullClassName` è un elemento figlio obbligatorio di `WizardExtension`.

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metadati per il modello di progetto standard per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un Windows applizione.

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
