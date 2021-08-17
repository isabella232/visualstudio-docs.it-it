---
title: Impossibile connettersi al nome computer &lt; &gt; . Impossibile trovare il computer sulla rete. | Microsoft Docs
description: "Questo comportamento si verifica se si verifica una delle condizioni seguenti: (1) La connessione al computer remoto è stata interrotta. (2) L'account utente nel computer remoto è disabilitato. (3) La password nel computer remoto è scaduta."
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 73bae31eb1e15b96e6878d64954fbaa68828377ee8ad6b802fe466f7ec675d6f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419845"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Errore: Impossibile connettersi al nome computer &lt; &gt; . Impossibile trovare il computer sulla rete.
Questo messaggio di errore viene visualizzato quando si verifica una delle seguenti condizioni:

- La connessione stabilita al computer remoto è stata interrotta.

- L'account utente utilizzato per la connessione al computer remoto è stato disabilitato.

- La password utilizzata per la connessione al computer remoto è scaduta.

### <a name="to-resolve-this-behavior"></a>Per risolvere questo comportamento

- Assicurarsi che il computer locale e il computer remoto si trovino nella stessa rete. A tale scopo, utilizzare Esplora risorse o Esplora file per tentare di accedere al computer remoto.

     - e -

- Assicurarsi che l'account utente utilizzato per la connessione al computer remoto sia attivato.

     - e -

- Assicurarsi che la password utilizzata per la connessione al computer remoto sia valida e non scaduta.

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)
- [Preparazione e Impostazioni debugger](../debugger/debugger-settings-and-preparation.md)
