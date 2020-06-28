---
title: 'Errore: Impossibile connettersi al nome del computer &lt; &gt; . Impossibile trovare il computer sulla rete. | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8618a15ab4dcd6c9bbc0d9d8ab9bf347552883b1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460143"
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
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)