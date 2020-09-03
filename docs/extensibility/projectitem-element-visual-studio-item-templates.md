---
title: Elemento ProjectItem (modelli di elemento di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: 885d0fbb50204f23a30fa43c1ffad45c9d67f829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770727"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Elemento ProjectItem (modelli di elemento di Visual Studio)
Specifica un file incluso nel modello di elemento.

> [!NOTE]
> L' `ProjectItem` elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. In questo argomento viene illustrato l' `ProjectItem` elemento per l'elemento. Per una spiegazione dell' `ProjectItem` elemento per i modelli di progetto, vedere [elemento ProjectItem (modelli di progetto di Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

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

### <a name="attributes"></a>Attributes

| Attributo | Descrizione |
|---------------------| - |
| `SubType` | Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento a più file. Questo valore viene utilizzato per determinare l'editor che utilizzerà [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per aprire l'elemento. |
| `CustomTool` | Attributo facoltativo.<br /><br /> Imposta CustomTool per l'elemento nel file di progetto. |
| `ItemType` | Attributo facoltativo.<br /><br /> Imposta ItemType per l'elemento nel file di progetto. |
| `ReplaceParameters` | Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento contiene valori di parametro che devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`. |
| `TargetFileName` | Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento creato dal modello. Questo attributo è utile per l'utilizzo della sostituzione dei parametri per creare un nome di elemento. |

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Oggetto `string` che rappresenta il nome di un file nel file con *estensione zip* del modello.

## <a name="remarks"></a>Osservazioni
 `ProjectItem` è un elemento figlio facoltativo di `TemplateContent` .

 L' `TargetFileName` attributo può essere utilizzato per rinominare i file con parametri. Se, ad esempio, il file MyFile *. vb* è presente nella directory radice del file con estensione *zip* del modello, ma si vuole che il file venga denominato in base al nome file specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento** , usare il codice XML seguente:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Quando viene creato un elemento da questo modello, il nome del file sarà basato sul nome immesso dall'utente nella finestra di dialogo **Aggiungi nuovo elemento** . Questa operazione è utile quando si creano modelli di elementi a più file. Per altre informazioni, vedere [procedura: creare modelli di elementi](../ide/how-to-create-multi-file-item-templates.md) a più file e [parametri di modello](../ide/template-parameters.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per il modello di elemento standard per una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.

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
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
