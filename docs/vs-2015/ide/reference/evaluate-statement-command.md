---
title: Comando Valuta istruzione | Microsoft Docs
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
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d569033193997135d9d0bc990ab7b9a9ef815f8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525807"
---
# <a name="evaluate-statement-command"></a>Comando Valuta istruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [valuta istruzione (comando)](https://docs.microsoft.com/visualstudio/ide/reference/evaluate-statement-command).  
  
  
Valuta e visualizza l'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Obbligatorio. Istruzione da valutare.  
  
## <a name="remarks"></a>Note  
 La finestra usata per immettere il comando **EvaluateStatement** determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.  
  
 Nella finestra **Comando** il segno di uguale (=) viene interpretato come operatore di confronto. Pertanto, se ad esempio i valori delle variabili `a` e `b` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 restituisce il valore `false`.  
  
 Al contrario, nella finestra **Controllo immediato** il segno di uguale (=) viene interpretato come operatore di assegnazione. Il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 assegna ad esempio alla variabile `a` il valore della variabile `b`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Stampa](../../ide/reference/print-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



