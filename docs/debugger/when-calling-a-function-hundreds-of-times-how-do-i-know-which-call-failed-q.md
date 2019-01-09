---
title: Trovare quale chiamata non riuscite quando si chiama una funzione molte volte | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f1d7c491b864fb8791a5fbd527859edafbd54b9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909138"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Quando vengono effettuate centinaia di chiamate di una funzione, come è possibile individuare la chiamata che ha avuto esito negativo?
## <a name="problem-description"></a>Descrizione del problema  
 Il programma si blocca in corrispondenza di una chiamata a una data funzione, `CnvtV`. Il programma probabilmente chiama tale funzione un paio di centinaia di volte prima di bloccarsi. Impostando un punto di interruzione di posizione su `CnvtV`, il programma si arresta a ciascuna chiamata a tale funzione e questo non è auspicabile. Non sapendo quali condizioni hanno causato l'esito negativo della funzione, non è possibile impostare un punto di interruzione condizionale. Come è possibile procedere?  
  
## <a name="solution"></a>Soluzione  
 È possibile impostare un punto di interruzione sulla funzione specificando nel campo **Passaggi** un valore così alto da non poter essere raggiunto. In questo caso, poiché si ritiene che la funzione `CnvtV` venga chiamata circa duecento volte, è possibile impostare **Passaggi** su 1000 o su un valore maggiore. Eseguire quindi il programma e attendere l'arresto della chiamata. A questo punto, aprire la finestra Punti di interruzione ed esaminare l'elenco dei punti di interruzione. Il punto di interruzione impostato per `CnvtV` è presente nell'elenco ed è seguito dal conteggio di passaggi e dal numero delle iterazioni rimanenti:  
  
```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 A questo punto la funzione con esito negativo risulta essere la chiamata 101. Se si reimposta il punto di interruzione con un conteggio di passaggi di 101 e si esegue nuovamente il programma, esso si arresterà in corrispondenza della chiamata a `CnvtV` che ha causato il blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Impostazione di punti di interruzione](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
