---
title: Finestre degli strumenti nel registro di sistema | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186377"
---
# <a name="tool-windows-in-the-registry"></a>Finestre degli strumenti nel Registro di sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I pacchetti VSPackage che forniscono le finestre degli strumenti devono registrarsi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] come provider della finestra degli strumenti. Per impostazione predefinita, le finestre degli strumenti create con il modello di pacchetto di Visual Studio eseguono questa operazione. I provider della finestra degli strumenti hanno chiavi del registro di sistema che specificano gli attributi di visibilità, ad esempio le dimensioni e la posizione della finestra degli strumenti predefinita, il GUID della finestra che funge da riquadro della finestra degli strumenti e lo stile di ancoraggio.  
  
 Durante lo sviluppo, i provider della finestra degli strumenti gestiti registrano le finestre degli strumenti aggiungendo attributi al codice sorgente e quindi eseguendo l'utilità di RegPkg.exe nell'assembly risultante. Per ulteriori informazioni, vedere la pagina relativa alla [registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrazione di provider di finestre degli strumenti non gestiti  
 I provider della finestra degli strumenti non gestiti devono registrarsi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nella sezione ToolWindows del registro di sistema. Il frammento di file reg seguente mostra come potrebbe essere registrata una finestra degli strumenti dinamica:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Nella prima chiave dell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ad esempio 7,1 o 8,0, la sottochiave {f0e1e9a1-9860-484d-AD5D-367d79aabf55} è il GUID del riquadro della finestra degli strumenti (DynamicWindowPane) e il valore predefinito {01069CDD-95CE-4620-AC21-DDFF6C57F012} è il GUID del pacchetto VSPackage che fornisce la finestra degli strumenti. Per una spiegazione delle sottochiavi float e DontForceCreate, vedere [configurazione dello schermo della finestra degli strumenti](../extensibility/tool-window-display-configuration.md).  
  
 La seconda chiave facoltativa, ToolWindows\Visibility, specifica i GUID dei comandi che richiedono che la finestra degli strumenti venga resa visibile. In questo caso, non è stato specificato alcun comando. Per ulteriori informazioni, vedere [configurazione dello schermo della finestra degli strumenti](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di base sui VSPackage](../misc/vspackage-essentials.md)
