---
title: Comando Valuta istruzione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: d3e50b519b162201d741f2460a8e9dbbe675c16e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230321"
---
# <a name="evaluate-statement-command"></a>Comando Valuta istruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



