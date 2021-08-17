---
title: Elemento WizardData (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento WizardData e su come specifica un xml personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d51d9827c5edcbcf522eb206add4769a8583f34ac7aa72732b472523e197bb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400439"
---
# <a name="wizarddata-element-visual-studio-templates"></a>Elemento WizardData (modelli di Visual Studio)

Specifica xml personalizzato

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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, il modello di elemento o starter kit.|

## <a name="text-value"></a>Valore di testo

Il valore di testo è facoltativo.

Questo testo specifica il codice XML personalizzato da passare all'estensione personalizzata della procedura guidata specificata [nell'elemento WizardExtension.](../extensibility/wizardextension-element-visual-studio-templates.md)

## <a name="remarks"></a>Commenti

In questo elemento è possibile specificare qualsiasi codice XML. Il codice XML verrà passato come parametro all'estensione personalizzata della procedura guidata, consentendo all'estensione di utilizzare il contenuto di questo elemento. Non viene eseguita alcuna convalida su questi dati.

Il contenuto **dell'elemento WizardData** viene passato, senza modifiche, come parametro all'interno del dizionario di stringhe dei parametri nel `IWizard.RunStarted` metodo . La chiave del dizionario è denominata `$wizarddata$` .

## <a name="example"></a>Esempio

L'esempio seguente illustra i metadati per il modello di progetto standard per un'applicazione Windows C#.

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

## <a name="see-also"></a>Vedi anche

- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
