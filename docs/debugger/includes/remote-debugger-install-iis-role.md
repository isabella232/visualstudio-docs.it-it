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
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908089"
---
Questi passaggi illustrano solo una configurazione di base di IIS. Per informazioni dettagliate o per installare un computer Desktop Windows, vedere [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) oppure [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Per i sistemi operativi Windows Server, usare il **Aggiungi ruoli e funzionalità** procedura guidata tramite il **Gestisci** collegamento o il **Dashboard** clic sul collegamento nella **Server Manager**. Nel passaggio **Ruoli del server** selezionare la casella per **Server Web (IIS)**.

![Il ruolo Server Web IIS viene selezionato nel passaggio dei ruoli del server Selezionare.](../media/remotedbg-server-roles-ws2012.png)

Nel passaggio **Servizi ruolo** selezionare i servizi ruolo IIS desiderato o accettare i servizi ruolo predefiniti forniti. Se si desidera abilitare la distribuzione usando le impostazioni e distribuzione Web di pubblicazione, assicurarsi che **gli strumenti e script di gestione IIS** sia selezionata.

Continuare la procedura di conferma per installare il ruolo server web e servizi. Un riavvio del server/IIS non è necessario dopo l'installazione del ruolo Server Web (IIS).