---
title: Trovare l'errore di chiamata quando si chiama una funzione più volte
description: Vedere una tecnica per l'impostazione di un punto di interruzione in una funzione in modo che l'interruzione si verifichi solo nella chiamata per cui la funzione ha esito negativo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 702a9ea54164fa4fa3fd62749c7e9aae18596266
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074085"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Quando vengono effettuate centinaia di chiamate di una funzione, come è possibile individuare la chiamata che ha avuto esito negativo?
## <a name="problem-description"></a>Descrizione del problema
 Il programma si blocca in corrispondenza di una chiamata a una data funzione, `CnvtV`. Il programma probabilmente chiama tale funzione un paio di centinaia di volte prima di bloccarsi. Impostando un punto di interruzione di posizione su `CnvtV`, il programma si arresta a ciascuna chiamata a tale funzione e questo non è auspicabile. Non sapendo quali condizioni hanno causato l'esito negativo della funzione, non è possibile impostare un punto di interruzione condizionale. Come posso procedere?

## <a name="solution"></a>Soluzione
 È possibile impostare un punto di interruzione sulla funzione specificando nel campo **Passaggi** un valore così alto da non poter essere raggiunto. In questo caso, poiché si ritiene che la funzione `CnvtV` venga chiamata circa duecento volte, è possibile impostare **Passaggi** su 1000 o su un valore maggiore. Eseguire quindi il programma e attendere l'arresto della chiamata. A questo punto, aprire la finestra Punti di interruzione ed esaminare l'elenco dei punti di interruzione. Il punto di interruzione impostato per `CnvtV` è presente nell'elenco ed è seguito dal conteggio di passaggi e dal numero delle iterazioni rimanenti:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 A questo punto la funzione con esito negativo risulta essere la chiamata 101. Se si reimposta il punto di interruzione con un conteggio di passaggi di 101 e si esegue nuovamente il programma, esso si arresterà in corrispondenza della chiamata a `CnvtV` che ha causato il blocco.

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Impostazione di punti di interruzione](/previous-versions/ktf38f66(v=vs.100))
- [Debug del codice nativo](../debugger/debugging-native-code.md)