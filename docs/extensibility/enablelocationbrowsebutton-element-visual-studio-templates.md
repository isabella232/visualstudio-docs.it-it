---
title: Elemento EnableLocationBrowseButton (modelli di Visual Studio)
description: Informazioni sull'elemento EnableLocationBrowseButton e su come specifica se il pulsante Sfoglia è disponibile nella finestra di dialogo Project nuova pagina.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6f25154015790919577d7fc32daffe21c0e69d90c10675c98dd2ad5d1314eed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388721"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Elemento EnableLocationBrowseButton (Visual Studio personalizzati)
Specifica se il **pulsante Sfoglia** è disponibile nella finestra di dialogo Nuovo **Project,** in modo che gli utenti possano modificare facilmente la directory predefinita in cui viene salvato un nuovo progetto.

 \<VSTemplate> \<TemplateData>
 \<EnableLocationBrowseButton>

## <a name="syntax"></a>Sintassi

```xml
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere o , che indica se visualizzare o meno il pulsante Sfoglia nella finestra Project `true` `false` nuova finestra di dialogo.  

## <a name="remarks"></a>Commenti
 `EnableLocationBrowseButton` è un elemento facoltativo. Il valore predefinito è `true` , che visualizza il **pulsante** Sfoglia nella finestra **di Project** finestra di dialogo.

 Nella finestra **di dialogo Project,** la casella di testo **Percorso** specifica la directory in cui viene salvato un nuovo progetto. Il pulsante **Sfoglia** consente di modificare questa directory visualizzando la finestra di dialogo Percorso Project , che consente di passare facilmente **a un'altra** directory disponibile nel computer e quindi di sceglierla come directory in cui viene salvato il nuovo progetto.

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metadati per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'Windows applicazione.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)
