---
title: Elemento WizardData (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6b61c62e8a3b69963bd56129fd3e7168271fc07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951221"
---
# <a name="wizarddata-element-visual-studio-templates"></a>Elemento WizardData (modelli di Visual Studio)

Specifica il formato XML personalizzate

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Sintassi

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, un modello di elemento o lo starter kit.|

## <a name="text-value"></a>Valore di testo

Il valore di testo è facoltativo.

Tale testo specifica il codice XML personalizzato da passare per l'estensione della creazione guidata personalizzata specificata nel [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) elemento.

## <a name="remarks"></a>Note

Qualsiasi XML può essere specificato in questo elemento. Il codice XML verrà passato come parametro per l'estensione della creazione guidata personalizzata, che consente l'estensione da utilizzare il contenuto di questo elemento. In merito ai dati viene eseguita alcuna convalida.

Il contenuto del **WizardData** l'elemento viene passato, senza variazioni, come un parametro all'interno di dizionario di stringhe dei parametri in di `IWizard.RunStarted` (metodo). La chiave del dizionario è denominata `$wizarddata$`.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati per il modello di progetto standard per un C# applicazione di Windows.

```xml
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
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)