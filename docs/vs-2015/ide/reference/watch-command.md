---
title: Comando Espressioni di controllo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 537b3f45dcf22dcc766b9902d20bf97af24b3c9d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675504"
---
# <a name="watch-command"></a>Comando Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.  
  
## <a name="remarks"></a>Osservazioni  
 `index` deve essere di tipo Integer. I valori validi sono 1, 2, 3 e 4.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre Auto e Variabili locali](../../debugger/autos-and-locals-windows.md)   
 [Procedura: modificare un valore in una finestra variabili](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Procedura: usare la finestra di dialogo Controllo immediato](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
