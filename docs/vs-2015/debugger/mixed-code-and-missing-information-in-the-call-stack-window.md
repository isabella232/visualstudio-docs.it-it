---
title: Codice misto e informazioni mancanti nella finestra Stack di chiamate | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c91b2e49dc94057ab7929380ad1b819cd01731d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527840"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Codice misto e informazioni mancanti nella finestra Stack di chiamate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [codice misto e informazioni mancanti nella finestra Stack di chiamate](https://docs.microsoft.com/visualstudio/debugger/mixed-code-and-missing-information-in-the-call-stack-window).  
  
A causa delle differenze tra gli stack di chiamate per il codice gestito e il codice nativo, il debugger non è sempre in grado di visualizzare lo stack di chiamate completo in caso di tipi di codice misti. Quando il codice nativo chiama il codice gestito, è possibile notare le seguenti discrepanze nel **Stack di chiamate** finestra:  
  
-   Il frame nativo situato immediatamente di sopra del codice gestito potrebbe non includere il **Stack di chiamate** finestra. Per altre informazioni, vedere [procedura: uscire da codice gestito quando sono visualizzati frame nativi mancanti dalla finestra Stack di chiamate](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Per le applicazioni in modalità mista avviate all'esterno del debugger, il **Stack di chiamate** finestra potrebbe visualizzare solo il codice gestito e nessuno dei frame nativi saranno visibili.  
  
 Entrambi i casi sono piuttosto rari. Nella maggior parte delle chiamate native a codice gestito gli stack di chiamate verranno visualizzati in modo corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)




