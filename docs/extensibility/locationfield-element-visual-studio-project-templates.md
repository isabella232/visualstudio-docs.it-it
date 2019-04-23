---
title: Elemento LocationField (modelli di progetto di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f55c67fbad80b05431ed13439584d3a94fa88c65
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078304"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (modelli di progetto di Visual Studio)
Specifica o meno il **posizione** casella di testo il **nuovo progetto** nella finestra di dialogo è abilitata, disabilitata o nascosta per il modello di progetto.

 \<VSTemplate > \<TemplateData > \<LocationField >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce la modalità di visualizzazione per il **nuovo progetto**.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 I valori di testo validi sono:

- `Enabled`, che consente di specificare che il **posizione** finestra di **nuovo progetto** è abilitata nella finestra di dialogo.

- `Disabled`, che consente di specificare che il **posizione** finestra di **nuovo progetto** è disabilitata nella finestra di dialogo.

- `Hidden`, che consente di specificare che il **posizione** finestra di **nuovo progetto** è nascosta la finestra di dialogo.

## <a name="remarks"></a>Note
 Il valore predefinito è `Enabled`.

 Il **posizione** casella di testo il **nuovo progetto** nella finestra di dialogo consente agli utenti di modificare la directory predefinita in cui vengono salvati i nuovi progetti.

 Il valore specificato nella `Location` elemento viene accettato dalla finestra di dialogo solo se il sistema di progetto sottostante lo supporta.

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)