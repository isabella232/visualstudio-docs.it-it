---
title: Elemento ProjectItem (modelli di elemento di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0fa0e7899e2f6e52536e2296519a1697e27a3643
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637068"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Elemento ProjectItem (modelli di elemento di Visual Studio)
Specifica un file che viene incluso nel modello di elemento.  
  
> [!NOTE]
>  Il `ProjectItem` elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. Questo argomento viene illustrato il `ProjectItem` elemento per elemento. Per una spiegazione delle `ProjectItem` (elemento) per i modelli di progetto, vedere [elemento ProjectItem (modelli di progetto di Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectItem >  
  
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
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`SubType`|Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento a più file. Questo valore viene utilizzato per determinare l'editor che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] userà per aprire l'elemento.|  
|`CustomTool`|Attributo facoltativo.<br /><br /> Imposta il CustomTool per l'elemento nel file di progetto.|  
|`ItemType`|Attributo facoltativo.<br /><br /> Imposta il tipo di elemento per l'elemento nel file di progetto.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento contiene i valori dei parametri devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento che viene creato dal modello. Questo attributo è utile per l'uso di sostituzione dei parametri per creare un nome di elemento.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Oggetto `string` che rappresenta il nome di un file nel modello *zip* file.  
  
## <a name="remarks"></a>Note  
 `ProjectItem` è un elemento figlio facoltativo di `TemplateContent`.  
  
 Il `TargetFileName` attributo può essere utilizzato per rinominare i file con i parametri. Ad esempio, se il file *MyFile. vb* presente nella directory radice del modello *zip* file, ma si desidera che il file sia denominato in base al nome di file fornito dall'utente nel **Aggiungi nuovo elemento**  nella finestra di dialogo si utilizzerebbe il codice XML seguente:  
  
```xml  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Quando viene creato un elemento da questo modello, il nome del file si baseranno sul nome utente specificato nella **Aggiungi nuovo elemento** nella finestra di dialogo. Ciò è utile durante la creazione di modelli di elementi a più file. Per altre informazioni, vedere [procedura: creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md) e [i parametri del modello](../ide/template-parameters.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per il modello di elementi standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.  
  
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
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)