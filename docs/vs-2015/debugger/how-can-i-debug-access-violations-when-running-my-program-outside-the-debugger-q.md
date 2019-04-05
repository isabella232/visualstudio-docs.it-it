---
title: Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cfdf356d21558f2024cb83e00bdfc930284b1d8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969034"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrizione del problema  
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso. Come è possibile effettuare il debug di questo problema?  
  
## <a name="solution"></a>Soluzione  
 Impostare l'opzione [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) ed eseguire il programma autonomamente finché non si verifica la violazione di accesso. Nella finestra di dialogo **Violazione di accesso** sarà quindi possibile fare clic su **Annulla** per avviare il debugger.  
  
 Vedere inoltre l'articolo Q133174 di Knowledge Base "How to Locate Where a General Protection (GP) Fault Occurs". È possibile trovare articoli della Knowledge Base nel CD di MSDN Library o cercando [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
