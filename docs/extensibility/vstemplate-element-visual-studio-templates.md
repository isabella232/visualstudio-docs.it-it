---
title: Elemento VSTemplate (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2ea57e16876d550694fb378a853b10d8f0af29
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069317"
---
# <a name="vstemplate-element-visual-studio-templates"></a>Elemento VSTemplate (modelli di Visual Studio)
Contiene tutti i metadati sul modello di progetto, modello di elemento o lo starter kit.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
| Attributo | Descrizione |
|-----------| - |
| `Type` | Identifica il modello come un modello di progetto o un modello di elemento. Questo attributo può avere un valore pari `Project` o `Item`. |
| `Version` | Specifica un numero di versione per il modello. I modelli in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] hanno una `Version` valore dell'attributo `3.0.0`. |
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica i dati che classificano il modello e definisce la modalità di visualizzazione per il **nuovo progetto** oppure **Aggiungi nuovo elemento** nella finestra di dialogo.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il contenuto del modello.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Elemento facoltativo.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Elemento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
 Nessuno.  
  
## <a name="remarks"></a>Note  
 Il `VSTemplate` elemento è l'elemento radice del *vstemplate* file.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dell'applicazione.  
  
```xml  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)