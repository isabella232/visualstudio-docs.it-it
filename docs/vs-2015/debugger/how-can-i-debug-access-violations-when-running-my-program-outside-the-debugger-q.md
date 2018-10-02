---
title: Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1525061210c6ef7cdda32c6204648c3944f4b889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518364"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [come è possibile eseguire il Debug accesso violazioni quando in esecuzione risorse del programma di fuori del Debugger?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q).  
  
Descrizione del problema  
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso. Come è possibile effettuare il debug di questo problema?  
  
## <a name="solution"></a>Soluzione  
 Impostare il [Just-in-time debug](../debugger/just-in-time-debugging-in-visual-studio.md) opzione ed eseguire il programma autonomamente finché non si verifica la violazione di accesso. Quindi, nella **violazione di accesso** della finestra di dialogo è possibile fare clic su **Annulla** per avviare il debugger.  
  
 Vedere inoltre l'articolo Q133174 di Knowledge Base "How to Locate Where a General Protection (GP) Fault Occurs". È possibile trovare articoli della Knowledge Base nel CD di MSDN Library o cercando [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



