---
title: Elemento ProjectItem (modelli Visual Studio Item) | Microsoft Docs
description: Informazioni sull'elemento ProjectItem per i modelli di elemento e su come accetta attributi diversi a seconda che il modello sia per un progetto o un elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 460f5ea31913e57dd095f7cbdf6677e24acb3a12a2fa70f80abb0acb67a34f8a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447805"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Elemento ProjectItem (modelli di elemento di Visual Studio)
Specifica un file incluso nel modello di elemento.

> [!NOTE]
> `ProjectItem`L'elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento viene illustrato `ProjectItem` l'elemento per item. Per una spiegazione `ProjectItem` dell'elemento per i modelli di progetto, vedere Elemento [ProjectItem (Visual Studio di progetto).](../extensibility/projectitem-element-visual-studio-project-templates.md)

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Sintassi

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

| Attributo | Descrizione |
|---------------------| - |
| `SubType` | Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento a più file. Questo valore viene utilizzato per determinare l'editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che userà per aprire l'elemento. |
| `CustomTool` | Attributo facoltativo.<br /><br /> Imposta CustomTool per l'elemento nel file di progetto. |
| `ItemType` | Attributo facoltativo.<br /><br /> Imposta ItemType per l'elemento nel file di progetto. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento dispone di valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento creato dal modello. Questo attributo è utile per usare la sostituzione dei parametri per creare un nome di elemento. |

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `string` che rappresenta il nome di un file nel modello *.zip* file.

## <a name="remarks"></a>Commenti
 `ProjectItem` è un elemento figlio facoltativo di `TemplateContent` .

 `TargetFileName`L'attributo può essere usato per rinominare i file con parametri. Ad esempio, se il file *MyFile.vb* è presente nella directory radice del file *.zip* modello, ma si vuole assegnare  un nome al file in base al nome file fornito dall'utente nella finestra di dialogo Aggiungi nuovo elemento , si userà il codice XML seguente:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Quando viene creato un elemento da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra **di** dialogo Aggiungi nuovo elemento. Ciò è utile quando si creano modelli di elementi a più file. Per altre informazioni, vedere [Procedura: Creare modelli di](../ide/how-to-create-multi-file-item-templates.md) elementi a più file e [Parametri del modello.](../ide/template-parameters.md)

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per il modello di elemento standard per una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio sullo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
