---
title: Elemento LocationField (modelli di progetto Visual Studio)
titleSuffix: ''
description: Informazioni sull'elemento LocationField e su come specifica se la casella di testo Percorso della finestra di dialogo Nuovo Project è abilitata, disabilitata o nascosta per il modello di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0610ab1e24b4f6de2052b45d52882ff7c9e88c2a402d1b7c96e5e0f4a5e4afe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121290921"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (Visual Studio di progetto)
Specifica se la casella **di** testo Percorso nella finestra di dialogo **Project** è abilitata, disabilitata o nascosta per il modello di progetto.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Sintassi

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e ne definisce la modalità di visualizzazione nella finestra **di dialogo Project**.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 I valori di testo validi sono:

- `Enabled`, che specifica che la **casella Percorso** della finestra di **dialogo Project** predefinita è abilitata.

- `Disabled`, che specifica che la **casella Percorso** della finestra di **dialogo Project** predefinita è disabilitata.

- `Hidden`, che specifica che la **casella Percorso** della finestra di **dialogo Project** proprietà è nascosta.

## <a name="remarks"></a>Commenti
 Il valore predefinito è `Enabled`.

 La **casella** di testo Percorso nella **finestra di dialogo Project** nuovo progetto consente agli utenti di modificare la directory predefinita in cui vengono salvati i nuovi progetti.

 Il valore specificato nell'elemento viene rispettato dalla finestra di dialogo solo se il `Location` sistema di progetto sottostante lo supporta.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
