---
title: Elemento ProjectType (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento ProjectType e su come classifica il modello di progetto in modo che venga visualizzato nella finestra di dialogo Nuovo Project o Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92fa66c122d441ed50e4ab83a4e0bfcce5c2e411372e97b45f747663cfc457c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400933"
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (Visual Studio modelli)
Categorizza il modello di progetto in modo che venga visualizzato sotto il gruppo specificato nella finestra di dialogo Project **o** Aggiungi **nuovo** elemento.

> [!WARNING]
> Project sono supportati per C++ a partire da Visual Studio 2012. Non sono supportate per C++ in Visual Studio 2010 e versioni precedenti.

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Sintassi

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo valore specifica il tipo di progetto che verrà creato dal modello e deve contenere uno dei valori seguenti:

- `CSharp`: specifica che il modello crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto o un elemento.

- `VisualBasic`: specifica che il modello crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto o un elemento.

- `Web`: specifica che il modello crea un progetto Web o un elemento. Se l'elemento contiene questo valore, il linguaggio del progetto o dell'elemento viene definito `ProjectType` [nell'elemento ProjectSubType (Visual Studio Templates).](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="remarks"></a>Commenti
 `ProjectType` è un elemento figlio obbligatorio di `TemplateData`.

 Il valore dell'elemento specifica dove si trova il modello nella finestra di dialogo Nuovo Project o Aggiungi `ProjectType` nuovo elemento.   Ad esempio, un modello con un valore di viene visualizzato sotto il nodo Visual C# nella finestra di `ProjectType` `CSharp` **Project** di dialogo. 

 È possibile specificare un sottotipo di modello usando [l'elemento ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metadati per un modello di progetto per [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] un'applicazione.

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

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectSubType (Visual Studio modelli)](../extensibility/projectsubtype-element-visual-studio-templates.md)
