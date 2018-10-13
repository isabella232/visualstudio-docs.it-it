---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: b785a3e43726522f6e6cc6ce99dec4bf3815c81d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230080"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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



