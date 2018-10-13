---
title: 'Errore: Computer remoto non viene visualizzata una finestra di dialogo connessioni Remote | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7b849ea60c48bc5127ddd50167415629daec4e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185159"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Errore: il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se il computer remoto non viene visualizzato nella finestra di dialogo Connessioni remote, controllare le cause più comuni riportate di seguito.  
  
 Se è in uso la modalità di compatibilità gestita, consultare la documentazione di Visual Studio 2010: [Risoluzione dei problemi di debug remoto - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Cause più comuni di questo errore  
  
-   Il computer remoto è in esecuzione in un computer situato in una subnet diversa. Per risolvere questo problema, digitare manualmente il nome del computer o l'indirizzo IP nella finestra di dialogo Qualificatore.  
  
-   Il debugger remoto non è in esecuzione nel computer remoto. Per risolvere questo problema, avviare il debugger remoto.  
  
-   Il firewall blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il firewall per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.  
  
-   Il software antivirus blocca le comunicazioni tra Visual Studio e il computer remoto. Per risolvere questo problema, configurare il software antivirus per consentire a Visual Studio e al debugger remoto (msvsmon) di comunicare.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



