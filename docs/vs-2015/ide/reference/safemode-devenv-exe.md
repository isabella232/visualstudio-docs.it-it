---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94e8e87f4440644f76906a70ea09a46282b109c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163370"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avvia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Osservazioni  
 Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] assicurando un'esecuzione stabile.  
  
## <a name="description"></a>DESCRIZIONE  
 Nell'esempio seguente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene avviato in modalità sicura.  
  
## <a name="code"></a>Codice  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
