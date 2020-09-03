---
title: Elemento LocationField (modelli di progetto di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b28fe0e696b23724758bd877b6031287290f879e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194457"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (modelli di progetto Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica se la casella di testo **percorso** nella finestra di dialogo **nuovo progetto** è abilitata, disabilitata o nascosta per il modello di progetto.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e ne definisce la modalità di visualizzazione nel **nuovo progetto**.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 I valori di testo validi sono:  
  
- `Enabled`, che specifica che la casella **percorso** della finestra di dialogo **nuovo progetto** è abilitata.  
  
- `Disabled`, che indica che la casella **percorso** della finestra di dialogo **nuovo progetto** è disabilitata.  
  
- `Hidden`, che indica che la casella **percorso** della finestra di dialogo **nuovo progetto** è nascosta.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore predefinito è `Enabled`.  
  
 La casella di testo **percorso** nella finestra di dialogo **nuovo progetto** consente agli utenti di modificare la directory predefinita in cui vengono salvati i nuovi progetti.  
  
 Il valore specificato nell' `Location` elemento viene rispettato solo dalla finestra di dialogo se il sistema del progetto sottostante lo supporta.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un modello [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
