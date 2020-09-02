---
title: Elemento SupportsLanguageDropDown (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53703d6178c81758650fdd00aada0a5952734caa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160482"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Elemento SupportsLanguageDropDown (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica se il modello di elemento Web è identico per più lingue e se l'opzione **lingua** è abilitata nella finestra di dialogo **Aggiungi nuovo elemento** .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsLanguageDropDown>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere `true` o `false` , che indica se l'opzione **lingua** è disponibile o meno nella finestra di dialogo **Aggiungi nuovo elemento** .  
  
## <a name="remarks"></a>Osservazioni  
 `SupportsLanguageDropDown` è un elemento facoltativo. Il valore predefinito è `false`.  
  
 L' `SupportsLanguageDropDown` elemento è disponibile solo per i modelli di elemento Web.  
  
 Se il valore di questo elemento è impostato su `true` , il modello di elemento è identico per tutti i linguaggi di programmazione e l'opzione **lingua** è abilitata nella finestra di dialogo **Aggiungi nuovo elemento** . Questa opzione consente di scegliere il linguaggio di programmazione del nuovo elemento che si desidera creare dal modello.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene specificato di visualizzare l'opzione di riepilogo della **lingua** .  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
