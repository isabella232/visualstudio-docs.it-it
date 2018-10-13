---
title: Imposta processo corrente | Microsoft Docs
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
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246662"
---
# <a name="set-current-process"></a>Imposta processo corrente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



