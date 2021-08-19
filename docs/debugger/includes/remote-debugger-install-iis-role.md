---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 928dc9ae93d475cd05b663cfc7838624e52f1de24411eace0ae7ac9ba818c31f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058432"
---
Questi passaggi illustrano solo una configurazione di base di IIS. Per informazioni più approfondite o per l'installazione in un computer desktop Windows, vedere Pubblicazione in [IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5.](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)

Per Windows sistemi operativi Server, usare **la** procedura  guidata Aggiungi ruoli e funzionalità tramite il collegamento Gestisci o il **collegamento Dashboard** in **Server Manager**. Nel passaggio **Ruoli del server** selezionare la casella per **Server Web (IIS)**.

![Il ruolo Server Web IIS viene selezionato nel passaggio dei ruoli del server Selezionare.](../media/remotedbg-server-roles-ws2012.png)

Nel passaggio **Servizi ruolo** selezionare i servizi ruolo IIS desiderato o accettare i servizi ruolo predefiniti forniti. Se si vuole abilitare la distribuzione usando le impostazioni di pubblicazione e Distribuzione Web, assicurarsi che sia selezionata l'opzione Strumenti e script di gestione **IIS.**

Procedere con i passaggi di conferma per installare il ruolo e i servizi del server Web. Un riavvio del server/IIS non è necessario dopo l'installazione del ruolo Server Web (IIS).