---
title: 'Errore: Computer remoto non viene visualizzata una finestra di dialogo connessioni Remote | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da933f078c1b9b8011fe6cf21f31ecce857efbc0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991190"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Errore: Il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote
Se il computer remoto non viene visualizzato nella finestra di dialogo Connessioni remote, controllare le cause più comuni riportate di seguito.  
  
 Se si utilizza la modalità di compatibilità gestita, consultare la documentazione di Visual Studio 2010: [Risoluzione dei problemi di debug remoto - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).  
  
### <a name="common-causes-for-this-error"></a>Cause più comuni di questo errore  
  
-   Il computer remoto è in esecuzione in un computer situato in una subnet diversa. Per risolvere questo problema, digitare manualmente il nome del computer o l'indirizzo IP nella finestra di dialogo Qualificatore.  
  
-   Il debugger remoto non è in esecuzione nel computer remoto. Per risolvere questo problema, avviare il debugger remoto.  
  
-   Il firewall blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il firewall per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.  
  
-   Il software antivirus blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il software antivirus per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.  
  
## <a name="see-also"></a>Vedere anche  
 [Remote Debugging](../debugger/remote-debugging.md)