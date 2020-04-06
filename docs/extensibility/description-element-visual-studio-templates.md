---
title: Elemento Description (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea10b43662d2818792dbc57aeac09a056cb63ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712252"
---
# <a name="description-element-visual-studio-templates"></a>Elemento Description (modelli di Visual Studio)
Specifica la descrizione del modello così come viene visualizzato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**

 \<VSTemplate \<> descrizione \<del>> modello

## <a name="syntax"></a>Sintassi

```
<Description>
    Template Description
</Description>
```

```
<Description Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Package`|Attributo facoltativo, per scenari utente avanzati.<br /><br /> GUID che specifica l'ID del pacchetto di Visual Studio.|
|`ID`|Attributo facoltativo, per scenari utente avanzati.<br /><br /> Specifica l'ID di risorsa di Visual Studio.|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario un valore di testo, a meno che non si usino gli attributi `Package` e `ID`.

 Il testo fornisce una descrizione del modello.

## <a name="remarks"></a>Osservazioni
 `Description`è un elemento figlio `TemplateData` obbligatorio dell'elemento.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadati per un modello di progetto per un'applicazione.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
