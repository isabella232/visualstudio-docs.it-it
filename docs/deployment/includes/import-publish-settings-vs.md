---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65846451"
---

1. Nel computer in cui è aperto il progetto ASP.NET in Visual Studio fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Pubblica**.

1. Se sono stati configurati tutti i profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **Crea nuovo profilo**.

1. Nella finestra di dialogo **Selezionare una destinazione di pubblicazione** fare clic su **Importa profilo**.

    ![Scegliere Pubblica](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Passare al percorso del file delle impostazioni di pubblicazione creato nella sezione precedente.

1. Nella finestra di dialogo **Importa file di impostazioni di pubblicazione** selezionare il profilo creato nella sezione precedente e fare clic su **Apri**.

    Visual Studio avvia il processo di distribuzione e la finestra Output mostra lo stato di avanzamento e i risultati.

    Se si verificano errori di distribuzione, fare clic su **Impostazioni** per modificare le impostazioni. Modificare le impostazioni e fare clic su **Convalida** per testare le nuove impostazioni. Se il nome host non viene trovato, provare l'indirizzo IP anziché il nome host nei campi **Server** e **URL di destinazione**.

    ![Modificare le impostazioni nello strumento di pubblicazione](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
