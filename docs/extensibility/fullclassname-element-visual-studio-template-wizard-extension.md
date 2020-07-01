---
title: Elemento FullClassName (estensione della creazione guidata modelli VS)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed9ceb57f49d8c08b75aa140e45a0f4268f4336c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769595"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Elemento FullClassName (estensione della creazione guidata modelli di Visual Studio)
Nome completo della classe che implementa l' `IWizard` interfaccia.

 \<VSTemplate> \<WizardExtension>
... \<FullClassName>

## <a name="syntax"></a>Sintassi

```xml
<FullClassName>ClassName</FullClassName>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene gli elementi di registrazione per personalizzare la creazione guidata modello.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo testo specifica la classe che implementa l' `IWizard` interfaccia. La classe specificata deve esistere nell'assembly specificato dall'elemento [assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) .

## <a name="remarks"></a>Osservazioni
 `FullClassName` è un elemento figlio obbligatorio di `WizardExtension`.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per il modello di progetto standard per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.

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

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
