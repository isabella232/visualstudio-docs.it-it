---
description: Se il computer remoto non viene visualizzato nella finestra di dialogo Connessioni remote, controllare le cause più comuni riportate di seguito.
title: Il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 08802c1d24d55469b3dc47d7d68f1132baba4378
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121087"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Errore: il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote
Se il computer remoto non viene visualizzato nella finestra di dialogo Connessioni remote, controllare le cause più comuni riportate di seguito.

 Se è in uso la modalità di compatibilità gestita, consultare la documentazione di Visual Studio 2010: [Risoluzione dei problemi di debug remoto - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Cause più comuni di questo errore

- Il computer remoto è in esecuzione in un computer situato in una subnet diversa. Per risolvere questo problema, digitare manualmente il nome del computer o l'indirizzo IP nella finestra di dialogo Qualificatore.

- Il debugger remoto non è in esecuzione nel computer remoto. Per risolvere questo problema, avviare il debugger remoto.

- Il firewall blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il firewall per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.

- Il software antivirus blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il software antivirus per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)
