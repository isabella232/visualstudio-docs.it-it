---
title: Elemento ProjectCollection (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2631af8fa4d6ee34fb47b5094631d2d64c9ff73c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942607"
---
# <a name="projectcollection-element-visual-studio-templates"></a>Elemento ProjectCollection (modelli di Visual Studio)
Specifica l'organizzazione e i contenuti dei modelli multiprogetto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica un progetto in un modello multiprogetto.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Raggruppa i progetti in modelli multiprogetto.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il contenuto del modello.|  
  
## <a name="remarks"></a>Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti. Il `ProjectCollection` elemento viene usato per specificare i progetti da includere nel modello. Per altre informazioni sui modelli multiprogetto, vedere [come: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio mostra una radice multiprogetto semplice *vstemplate* file. In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`. L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto. Se il `ProjectName` attributo non esiste, il nome del *vstemplate* file viene usato come nome del progetto.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creare modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md)