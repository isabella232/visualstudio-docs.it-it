---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159283"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica la versione minima del sistema operativo necessaria per il corretto funzionamento del modello di progetto. Questo elemento viene usato per i modelli di progetto per la creazione di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app.  
  
 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se `RequiredPlatformVersion` è superiore alla versione del sistema operativo, il modello non viene visualizzato nella finestra di dialogo **nuovo progetto** . Per specificare un modello per [!INCLUDE[win8](../includes/win8-md.md)] o versione successiva, impostare `RequiredPlatformVersion` su 6.2.0. Per specificare un modello per [!INCLUDE[win81](../includes/win81-md.md)] o versione successiva, impostare RequiredPlatformVersion su 6.3.0.  
  
 I modelli che specificano `RequiredPlatformVersion` = 8 sono compatibili con i modelli di cliente precedenti [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
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
  
## <a name="remarks"></a>Osservazioni  
 Questo testo specifica la versione minima del sistema operativo richiesta dal modello.  
  
## <a name="example"></a>Esempio  
 Questo esempio specifica che il modello di progetto è destinato a [!INCLUDE[win8](../includes/win8-md.md)] o versioni successive.  
  
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
