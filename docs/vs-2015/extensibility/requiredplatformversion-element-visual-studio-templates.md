---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fb35bfefeb7722c3ec488a1f9caf63cd49202dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528486"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento RequiredPlatformVersion (modelli di Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/requiredplatformversion-element-visual-studio-templates).  
  
Specifica la versione minima del sistema operativo il modello di progetto necessaria per funzionare correttamente. Questo elemento viene usato per modelli di progetto che creano [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app.  
  
 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se il `RequiredPlatformVersion` è superiore alla versione del sistema operativo, il modello non viene visualizzato nei **nuovo progetto** nella finestra di dialogo. Per specificare un modello per [!INCLUDE[win8](../includes/win8-md.md)] o versione successiva, impostare `RequiredPlatformVersion` a 6.2.0. Per specificare un modello per [!INCLUDE[win81](../includes/win81-md.md)] o versione successiva, impostare RequiredPlatformVersion alla versione 6.3.0.  
  
 I modelli che specificano `RequiredPlatformVersion`= 8 compatibili con il cliente precedente [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] modelli.  
  
 VSTemplate  
TemplateData  
... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nessuno.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
## <a name="remarks"></a>Note  
 Questo testo specifica la versione minima del sistema operativo richiesta dal modello.  
  
## <a name="example"></a>Esempio  
 In questo esempio specifica che il progetto è destinato a modello [!INCLUDE[win8](../includes/win8-md.md)] o versione successiva.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento TargetPlatformName (modelli di Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

