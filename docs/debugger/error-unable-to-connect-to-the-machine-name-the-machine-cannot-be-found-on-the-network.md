---
title: Non è possibile connettersi al nome del computer &lt; &gt; . Impossibile trovare il computer sulla rete. | Microsoft Docs
description: "Questo comportamento si verifica quando viene soddisfatta una delle condizioni seguenti: (1) la connessione al computer remoto è stata interrotta. (2) l'account utente nel computer remoto è disabilitato. (3) la password del computer remoto è scaduta."
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
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146431"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Errore: non è possibile connettersi al nome del computer &lt; &gt; . Impossibile trovare il computer sulla rete.
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
- [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)
