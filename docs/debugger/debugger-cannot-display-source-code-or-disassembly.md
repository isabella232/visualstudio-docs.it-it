---
title: Il debugger non è in grado di visualizzare il codice sorgente o il disassembly
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d87de3034cb6cb8ba3364fa362eff1c27e6bae9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738340"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Impossibile visualizzare il codice sorgente o il disassembly
Il testo del messaggio di errore è il seguente:

 Impossibile visualizzare il codice sorgente o disassembly relativo alla posizione corrente in cui si è interrotta l'esecuzione.

 Questo messaggio di errore può essere visualizzato in alcune situazioni:

- È possibile che sia stato raggiunto un punto di interruzione in una posizione per la quale non esiste un codice sorgente, mentre si esegue il debug di un linguaggio che non supporta il disassembly. Aprire la finestra punti di **interruzione** , individuare il punto di interruzione ed eliminarlo.

- Se si sta eseguendo il debug di script, è possibile che sia stato raggiunto un punto di interruzione mentre non esistevano thread nel programma. Scegliere **Esegui** o **Continua** dal menu **Debug** per continuare l'esecuzione del debug.

- È possibile che per aspetti relativi alla sicurezza il debugger non sia stato in grado di leggere lo stack, il thread, il registro e altre informazioni sul contesto dal programma di cui si sta eseguendo il debug. Questa condizione si verifica più spesso se si esegue il debug di un'applicazione Web e non si dispone dell'autorizzazione corretta per accedere alla directory virtuale. Impostare la sicurezza anonima per la directory virtuale e riprovare.

## <a name="see-also"></a>Vedere anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)