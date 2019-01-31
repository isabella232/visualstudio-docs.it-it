---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 59bde318995ed8b66637a2220ae1817db2a1e800
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834678"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Cancella tutte le opzioni per ignorare il caricamento aggiunte ai pacchetti VSPackage dagli utenti che vogliono evitare di caricare i pacchetti problematici, quindi avvia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Note  
 La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag riabilita il caricamento del pacchetto VSPackage.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono cancellati tutti i tag SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
