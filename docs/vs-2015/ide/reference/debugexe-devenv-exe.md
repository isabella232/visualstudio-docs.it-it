---
title: -DebugExe (devenv.exe) | Microsoft Docs
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
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f58db37f353cddd7444e7ea185dc07c0ec6cd603
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517605"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [- DebugExe (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/debugexe-devenv-exe).  
  
  
Apre il file eseguibile specificato per il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argomenti  
 `ExecutableFile`  
 Obbligatorio. Percorso e nome di un file con estensione exe.  
  
 Se il file con estensione exe non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene avviato normalmente.  
  
## <a name="remarks"></a>Note  
 Le stringhe che seguono il parametro `ExecutableFile` vengono passate al file come argomenti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



