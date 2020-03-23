---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "68159593"
---
1. Avviare Visual Studio e selezionare **File** > **nuovo** > **progetto**.

1. Nella finestra di dialogo **Nuovo progetto** cercare "Python", selezionare il modello **Da codice Python esistente**, assegnare al progetto il nome e una posizione e selezionare **OK**.

1. Nella procedura guidata visualizzata impostare il percorso al codice esistente, un filtro per i tipi di file ed eventuali percorsi di ricerca richiesti dal progetto e quindi fare clic su **Avanti**. Se non si sa quali sono i percorsi di ricerca, lasciare vuoto il campo.

    ![Nuovo progetto da codice esistente, passaggio 1](../media/projects-from-existing-1.png)

1. Nella finestra di dialogo successiva selezionare il file di avvio per il progetto e selezionare **Avanti**. Se lo si desidera, selezionare un ambiente; accettare in caso contrario le impostazioni predefinite. Si noti che la finestra di dialogo mostra solo i file nella cartella principale; se il file desiderato si trova in una sottocartella, lasciare vuoto il file di avvio e impostarlo in un secondo momento in **Esplora soluzioni** (descritto di seguito).

    ![Nuovo progetto da codice esistente, passaggio 2](../media/projects-from-existing-2.png)

1. Selezionare il percorso in cui salvare il file di progetto (un file con estensione *pyproj* su disco). Se applicabile, in questa finestra di dialogo è anche possibile includere il rilevamento automatico di ambienti virtuali e personalizzare il progetto per diversi framework Web. Se non si è certi di queste opzioni, lasciarle impostate sui valori predefiniti.

    ![Nuovo progetto da codice esistente, passaggio 3](../media/projects-from-existing-3.png)

1. Selezionare **Fine**. Visual Studio crea il progetto e lo apre in **Esplora soluzioni**. Se si vuole spostare il file con estensione *pyproj*, selezionarlo in **Esplora soluzioni** e scegliere **File** > **Salva con nome**. Questa azione implica l'aggiornamento dei riferimenti dei file nel progetto, ma non lo spostamento di file di codice.

1. Per impostare un file di avvio diverso, individuare il file in **Esplora soluzioni**, fare clic con il pulsante destro del mouse e selezionare **Imposta come file di avvio**.