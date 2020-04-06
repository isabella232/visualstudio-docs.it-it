---
title: Elemento ProjectItem (modelli di elemento di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701870"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Elemento ProjectItem (modelli di elemento di Visual Studio)
Specifica un file incluso nel modello di elemento.

> [!NOTE]
> L'elemento `ProjectItem` accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento `ProjectItem` viene illustrato l'elemento per l'elemento. Per una spiegazione dell'elemento per i `ProjectItem` modelli di progetto, vedere Elemento ProjectItem (modelli di progetto di Visual [Studio).](../extensibility/projectitem-element-visual-studio-project-templates.md)

 \<VSTemplate \<> TemplateContent> \<ProjectItem>

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
| `SubType` | Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento su più file. Questo valore viene utilizzato per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] determinare l'editor che verrà utilizzato per aprire l'elemento. |
| `CustomTool` | Attributo facoltativo.<br /><br /> Imposta il CustomTool per l'elemento nel file di progetto. |
| `ItemType` | Attributo facoltativo.<br /><br /> Imposta il ItemType per l'elemento nel file di progetto. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento dispone di valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento creato dal modello. Questo attributo è utile per utilizzare la sostituzione dei parametri per creare un nome di elemento. |

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `string` che rappresenta il nome di un file nel file *.zip* del modello.

## <a name="remarks"></a>Osservazioni
 `ProjectItem`è un elemento `TemplateContent`figlio facoltativo di .

 L'attributo `TargetFileName` può essere utilizzato per rinominare i file con parametri. Ad esempio, se il file *MyFile.vb* è presente nella directory radice del file *.zip* del modello, ma si desidera che il file venga denominato in base al nome file fornito dall'utente nella finestra di dialogo **Aggiungi nuovo elemento,** utilizzare il seguente codice XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Quando viene creato un elemento da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra di dialogo **Aggiungi nuovo elemento.** Ciò è utile quando si creano modelli di elemento a più file. Per ulteriori informazioni, vedere [Procedura: creare modelli](../ide/how-to-create-multi-file-item-templates.md) di elemento multifile e Parametri [modello](../ide/template-parameters.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] per il modello di elemento standard per una classe.

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

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
