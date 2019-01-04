---
title: Progetto elemento (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c74868621725d916177df73f648766f706b71d40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950329"
---
# <a name="project-element-visual-studio-templates"></a>Elemento Project (modelli di Visual Studio)
Specifica il file o directory da aggiungere al progetto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`File`|Attributo obbligatorio.<br /><br /> Specifica il nome del file di progetto nel modello *zip* file.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se il file di progetto contiene i valori dei parametri devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome del file di progetto quando viene creato un progetto dal modello.|  
|`IgnoreProjectParameter`|Attributo facoltativo.<br /><br /> Specifica se il progetto deve essere aggiunto alla soluzione corrente. Se il valore del parametro personalizzato, "$*myCustomParameter*$" è presente nel file di sostituzione dei parametri, il progetto viene creato ma non aggiunta come parte della soluzione attualmente aperta.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Cartella](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica una cartella da aggiungere al progetto.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Specifica un file da aggiungere a un progetto.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.|  
  
## <a name="remarks"></a>Note  
 `Project` è un elemento figlio facoltativo di `TemplateContent`.  
  
 Il `Project` elemento è utilizzato per specificare un progetto e di conseguenza, è valido solo nei modelli di progetto.  
  
 `Project` gli elementi possono presentare [cartella](../extensibility/folder-element-visual-studio-project-templates.md) gli elementi figlio oppure [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) gli elementi figlio, ma non una combinazione di entrambi `Folder` e `ProjectItem` gli elementi figlio.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Rinomina automaticamente il nome del file di progetto in base al nome immesso dall'utente nel **nuovo progetto** nella finestra di dialogo. Usare il `TargetFileName` attributo se si desidera fornire un nome file alternativo per i file di progetto creati con il modello.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dell'applicazione.  
  
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
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectItem (modelli di progetto di Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Elemento Folder (modelli di progetto di Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)