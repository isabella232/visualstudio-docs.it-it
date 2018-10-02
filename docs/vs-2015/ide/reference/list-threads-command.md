---
title: Comando Elenca thread | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd8e9f96e0f477ba0b83419274d9b2ed0a101195
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530228"
---
# <a name="list-threads-command"></a>Comando Elenca thread
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [comando Elenca thread](https://docs.microsoft.com/visualstudio/ide/reference/list-threads-command).  
  
  
Visualizza un elenco dei thread del programma corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.  
  
## <a name="remarks"></a>Note  
 Quando specificato, l'argomento `index` contrassegna il thread indicato come thread corrente. Nell'elenco viene visualizzato un asterisco (*) accanto al thread corrente.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



