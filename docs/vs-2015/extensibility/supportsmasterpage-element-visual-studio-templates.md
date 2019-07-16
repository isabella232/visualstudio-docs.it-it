---
title: Elemento SupportsMasterPage (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 051bde61132d286c3941a12c2e970aa2019fc0b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160469"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Elemento SupportsMasterPage (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica se la non la **Seleziona pagina Master** casella di controllo è abilitato nel **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsMasterPage >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica i dati che classificano il modello e definisce la modalità di visualizzazione per il **nuovo progetto** oppure **nuovo elemento** nella finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere `true` oppure `false`, che indica o meno la **Seleziona pagina Master** casella di controllo è abilitato nel **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `SupportsMasterPage` è un elemento facoltativo. Il valore predefinito è `false`.  
  
 Il `SupportsMasterPage` elemento è disponibile solo per i modelli di elemento di Web.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un progetto Web che include il supporto per una pagina master.  
  
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
        <SupportsMasterPage>true</SupportsMasterPage>  
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
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
