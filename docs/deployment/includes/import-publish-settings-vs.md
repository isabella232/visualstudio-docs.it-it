---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249926"
---

1. Nel computer in cui è aperto il progetto ASP.NET in Visual Studio fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Pubblica**.

   Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **nuovo** o su **Crea nuovo profilo**.

1. Selezionare l'opzione per importare un profilo.

   ::: moniker range=">=vs-2019"
   Nella finestra di dialogo **pubblica** fare clic su **Importa profilo**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra di dialogo **Selezionare una destinazione di pubblicazione** fare clic su **Importa profilo**.
   ::: moniker-end

   ![Scegliere Pubblica](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Passare al percorso del file delle impostazioni di pubblicazione creato nella sezione precedente.

1. Nella finestra di dialogo **Importa file di impostazioni di pubblicazione** passare a e selezionare il profilo creato nella sezione precedente e fare clic su **Apri**.

   ::: moniker range=">=vs-2019"
   Fare clic su **fine** per salvare il profilo di pubblicazione e quindi fare clic su **pubblica**.

   Visual Studio avvia il processo di distribuzione e la finestra Output mostra lo stato di avanzamento e i risultati.

   Se vengono visualizzati errori di distribuzione, fare clic su **modifica** per modificare le impostazioni. Modificare le impostazioni e fare clic su **Convalida** per testare le nuove impostazioni. Se il nome host non viene trovato, provare l'indirizzo IP anziché il nome host nei campi **Server** e **URL di destinazione**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio avvia il processo di distribuzione e la finestra Output mostra lo stato di avanzamento e i risultati.

   Se si verificano errori di distribuzione, fare clic su **Impostazioni** per modificare le impostazioni. Modificare le impostazioni e fare clic su **Convalida** per testare le nuove impostazioni. Se il nome host non viene trovato, provare l'indirizzo IP anziché il nome host nei campi **Server** e **URL di destinazione**.
   ::: moniker-end

   ![Modificare le impostazioni nello strumento di pubblicazione](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
