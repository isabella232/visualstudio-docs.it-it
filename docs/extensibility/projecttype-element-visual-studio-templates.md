---
title: Elemento ProjectType (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701799"
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (modelli di Visual Studio)
Categorizza il modello di progetto in modo che venga visualizzato sotto il gruppo specificato nella finestra di dialogo **Nuovo progetto** o Aggiungi **nuovo elemento.**

> [!WARNING]
> I modelli di progetto sono supportati per il linguaggio C, a partire da Visual Studio 2012. Non sono supportati per il linguaggio C, in Visual Studio 2010 e versioni precedenti.

 \<VSTemplate \<> TemplateData> \<ProjectType>

## <a name="syntax"></a>Sintassi

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo valore specifica il tipo di progetto che verrà creato dal modello e deve contenere uno dei valori seguenti:

- `CSharp`: specifica che il [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello crea un progetto o un elemento.

- `VisualBasic`: specifica che il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] modello crea un progetto o un elemento.

- `Web`: specifica che il modello crea un progetto Web o un elemento. Se `ProjectType` l'elemento contiene questo valore, il linguaggio del progetto o dell'elemento è definito [nell'elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Osservazioni
 `ProjectType` è un elemento figlio obbligatorio di `TemplateData`.

 Il valore `ProjectType` dell'elemento specifica la posizione del modello nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento.** Ad esempio, un `ProjectType` modello `CSharp` con un valore di viene visualizzato sotto il nodo **Visual C,** nella finestra di dialogo **Nuovo progetto** .

 È possibile specificare un sottotipo di modello utilizzando l'elemento [ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

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
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
