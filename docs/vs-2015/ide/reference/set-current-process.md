---
title: Imposta processo corrente | Microsoft Docs
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
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5281d1c0d926d8d6acdedf323649216c74a4cab9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527291"
---
# <a name="set-current-process"></a>Imposta processo corrente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Imposta processo corrente](https://docs.microsoft.com/visualstudio/ide/reference/set-current-process).  
  
  
Imposta il processo specificato come processo attivo nel debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. L'indice del processo.  
  
## <a name="remarks"></a>Note  
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



