---
title: Imposta processo corrente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed19c5b95351f8e9c34255a915fc6a446800f761
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669940"
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
  
## <a name="remarks"></a>Osservazioni  
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
