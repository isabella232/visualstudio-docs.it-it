---
title: Elemento FullClassName (estensione della creazione guidata modello di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f185d791010c545dd56326505d871fb964a71b66
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943739"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Elemento FullClassName (estensione della creazione guidata modello di Visual Studio)
Il nome completo della classe che implementa il `IWizard` interfaccia.  
  
 \<VSTemplate >  
 \<WizardExtension >  
 ...  
 \<FullClassName >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<FullClassName>ClassName</FullClassName>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene gli elementi di registrazione per la creazione guidata modello di personalizzazione.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Tale testo specifica la classe che implementa il `IWizard` interfaccia. La classe specificata deve esistere nell'assembly specificato per il [Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) elemento.  
  
## <a name="remarks"></a>Note  
 `FullClassName` è un elemento figlio obbligatorio di `WizardExtension`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per il modello di progetto standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creare modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)   
 [Procedura: Usare le procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)