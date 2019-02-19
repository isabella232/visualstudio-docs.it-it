---
title: Comando Stampa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: c72f6668e6babab6bd62cfb0e9a6ca8632df2a84
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763570"
---
# <a name="print-command"></a>Comando Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Valuta un'espressione o visualizza il testo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Obbligatorio. Espressione da valutare o testo da visualizzare.  
  
## <a name="remarks"></a>Osservazioni  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
