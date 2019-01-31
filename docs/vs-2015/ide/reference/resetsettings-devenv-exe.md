---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 60e0dd272bd22cce2367e59b16fdea7965cb50e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761589"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
