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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89326594"
---
Questa procedura Mostra solo una configurazione di base di IIS. Per informazioni più dettagliate o per eseguire l'installazione in un computer desktop Windows, vedere la pagina relativa alla [pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Per i sistemi operativi Windows Server, usare l' **Aggiunta guidata ruoli e funzionalità** tramite il collegamento **Gestisci** o **Dashboard** in **Server Manager**. Nel passaggio **Ruoli del server** selezionare la casella per **Server Web (IIS)**.

![Il ruolo Server Web IIS viene selezionato nel passaggio dei ruoli del server Selezionare.](../media/remotedbg-server-roles-ws2012.png)

Nel passaggio **Servizi ruolo** selezionare i servizi ruolo IIS desiderato o accettare i servizi ruolo predefiniti forniti. Se si vuole abilitare la distribuzione usando le impostazioni di pubblicazione e Distribuzione Web, assicurarsi che sia selezionata l'opzione **strumenti e script di gestione IIS** .

Procedere con i passaggi di conferma per installare il ruolo server Web e i servizi. Un riavvio del server/IIS non è necessario dopo l'installazione del ruolo Server Web (IIS).