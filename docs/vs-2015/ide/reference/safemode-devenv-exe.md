---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 308dd7e81a35604bcd0f6f5eba517b850ace17ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528533"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [- SafeMode (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/safemode-devenv-exe).  
  
  
Avvia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Note  
 Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] assicurando un'esecuzione stabile.  
  
## <a name="description"></a>Descrizione  
 Nell'esempio seguente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene avviato in modalità sicura.  
  
## <a name="code"></a>Codice  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



