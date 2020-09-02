---
title: Elemento FullClassName (estensione della creazione guidata modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6cd466a41c61da929e9acc1619f384a3621f9c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204341"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Elemento FullClassName (estensione della Creazione guidata modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nome completo della classe che implementa l' `IWizard` interfaccia.  
  
 \<VSTemplate>  
 \<WizardExtension>  
 ...  
 \<FullClassName>  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene gli elementi di registrazione per personalizzare la creazione guidata modello.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo specifica la classe che implementa l' `IWizard` interfaccia. La classe specificata deve esistere nell'assembly specificato dall'elemento [assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) .  
  
## <a name="remarks"></a>Osservazioni  
 `FullClassName` è un elemento figlio obbligatorio di `WizardExtension`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per il modello di progetto standard per un' [!INCLUDE[csprcs](../includes/csprcs-md.md)] applicazione Windows.  
  
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
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
