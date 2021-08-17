---
title: Il debugger non può visualizzare il codice sorgente o il disassembly
description: Vedere i motivi del messaggio "Il debugger non può visualizzare il codice sorgente o il disassembly per il percorso corrente in cui l'esecuzione è stata arrestata".
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 050a0f486be9e39f69b80013586a9755ba03d410
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080989"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Impossibile visualizzare il codice sorgente o il disassembly
Il testo del messaggio di errore è il seguente:

 Impossibile visualizzare il codice sorgente o disassembly relativo alla posizione corrente in cui si è interrotta l'esecuzione.

 Questo messaggio di errore può essere visualizzato in alcune situazioni:

- È possibile che sia stato raggiunto un punto di interruzione in una posizione per la quale non esiste un codice sorgente, mentre si esegue il debug di un linguaggio che non supporta il disassembly. Aprire la finestra **Punti di** interruzione, individuare il punto di interruzione ed eliminarlo.

- Se si sta eseguendo il debug di script, è possibile che sia stato raggiunto un punto di interruzione mentre non esistevano thread nel programma. Scegliere **Esegui** o **Continua** dal menu **Debug** per continuare l'esecuzione del debug.

- È possibile che per aspetti relativi alla sicurezza il debugger non sia stato in grado di leggere lo stack, il thread, il registro e altre informazioni sul contesto dal programma di cui si sta eseguendo il debug. Questa condizione si verifica più spesso se si esegue il debug di un'applicazione Web e non si dispone dell'autorizzazione corretta per accedere alla directory virtuale. Impostare la sicurezza anonima per la directory virtuale e riprovare.

## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)