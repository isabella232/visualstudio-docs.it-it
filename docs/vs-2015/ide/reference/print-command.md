---
title: Comando Stampa | Microsoft Docs
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525373"
---
# <a name="print-command"></a>Comando Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [comando Stampa](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
Valuta un'espressione o visualizza il testo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Obbligatorio. Espressione da valutare o testo da visualizzare.  
  
## <a name="remarks"></a>Note  
 È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando  
  
```  
>Debug.Print expA  
```  
  
 può anche essere scritto  
  
```  
>? expA  
```  
  
 Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



