---
title: Comando Elenca thread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 627e361fca63522f47a1d472655573c14a44035a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54804608"
---
# <a name="list-threads-command"></a>Comando Elenca thread
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Visualizza un elenco dei thread del programma corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.  
  
## <a name="remarks"></a>Osservazioni  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
