---
title: 'Errore: non è possibile connettersi al computer &lt;name &gt;. Impossibile trovare il computer sulla rete. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736832"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Errore: non è possibile connettersi al computer &lt;name &gt;. Impossibile trovare il computer sulla rete.
Questo messaggio di errore viene visualizzato quando si verifica una delle seguenti condizioni:

- La connessione stabilita al computer remoto è stata interrotta.

- L'account utente utilizzato per la connessione al computer remoto è stato disabilitato.

- La password utilizzata per la connessione al computer remoto è scaduta.

### <a name="to-resolve-this-behavior"></a>Per risolvere questo comportamento

- Assicurarsi che il computer locale e il computer remoto si trovino nella stessa rete. A tale scopo, utilizzare Esplora risorse o Esplora file per tentare di accedere al computer remoto.

     \- e -

- Assicurarsi che l'account utente utilizzato per la connessione al computer remoto sia attivato.

     \- e -

- Assicurarsi che la password utilizzata per la connessione al computer remoto sia valida e non scaduta.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)