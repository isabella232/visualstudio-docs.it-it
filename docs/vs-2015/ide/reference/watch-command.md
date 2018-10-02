---
title: Comando Espressioni di controllo | Microsoft Docs
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d06e15f23a8f75e4a771b9db1991f5aba2ffc0d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528929"
---
# <a name="watch-command"></a>Comando Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Watch comando](https://docs.microsoft.com/visualstudio/ide/reference/watch-command).  
  
  
Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.  
  
## <a name="remarks"></a>Note  
 `index` deve essere di tipo Integer. I valori validi sono 1, 2, 3 e 4.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre Auto e Variabili locali](../../debugger/autos-and-locals-windows.md)   
 [Procedura: modificare un valore in una finestra delle variabili](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Procedura: usare la finestra di dialogo Controllo immediato](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



