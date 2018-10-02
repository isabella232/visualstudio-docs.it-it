---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25697a792b0c48746a1d7840b8091ea718f5cdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525786"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [- ResetSettings (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetsettings-devenv-exe).  
  
  
Ripristina le impostazioni predefinite di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e avvia automaticamente l'IDE di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Facoltativamente, reimposta le impostazioni in un file con estensione vssettings specificato.  
  
 Le impostazioni predefinite sono determinate dal profilo selezionato quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è stato avviato per la prima volta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argomenti  
 `SettingsFile`  
 Il percorso completo e il nome del file con estensione vssettings da applicare a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Per ripristinare il profilo Impostazioni generali per lo sviluppo, usare `General`.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato `SettingsFile`, al successivo avvio di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verrà richiesto di selezionare una raccolta predefinita di impostazioni.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente applica le impostazioni memorizzate nel file `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



