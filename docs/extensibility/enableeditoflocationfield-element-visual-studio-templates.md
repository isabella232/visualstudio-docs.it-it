---
title: EnableEditOfLocationField (elemento) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e15e2f5c070b8a8c565497c6ba3fc6490b87591
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711998"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>EnableEditOfLocationField (elemento) (modelli di Visual Studio)
Specifica se l'utente può modificare il campo della posizione.

 \<VSTemplate \<> TemplateData> \<> EnableEditOfLocationField

## <a name="syntax"></a>Sintassi

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 nessuno

### <a name="child-elements"></a>Elementi figlio
 nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve `true` `false`essere o , che indica se l'utente può modificare o meno la casella di testo **Percorso** nella finestra di dialogo **Nuovo progetto** .

## <a name="remarks"></a>Osservazioni
 `EnableEditOfLocationField` è un elemento facoltativo. Il valore `true`predefinito è , che consente all'utente di modificare il valore nella casella di testo **Percorso** della finestra di dialogo **Nuovo progetto** .

 Nella finestra di dialogo **Nuovo progetto,** la casella di testo **Percorso** specifica la directory in cui viene salvato un nuovo progetto.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] i metadati per un'applicazione Windows.The following example illustrates the metadata for a Windows application.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
