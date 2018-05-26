---
title: Distribuire nella cartella locale
description: Distribuire un'app in una cartella locale
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
1. Nel **Esplora**del mouse sul nodo del progetto e scegliere **pubblica** (per Web Form, **pubblicare App Web**).

    Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **nuovo profilo**.

1. Nel **pubblica** nella finestra di dialogo **cartella**, fare clic su **Sfoglia**e creare una nuova cartella **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Per un'app Web Form, scegliere **personalizzato** nella finestra di dialogo pubblica, immettere un nome di profilo e scegliere **OK**.

1. Fare clic su **Crea profilo** nell'elenco a discesa (**pubblica** è il valore predefinito).

1. Nel **pubblica** la finestra di dialogo, fare clic sul **impostazioni** collegamento e quindi selezionare il **impostazioni** scheda.

1. Impostare la configurazione su **Debug**selezionare **Elimina tutti i file esistenti prima della pubblicazione**, quindi fare clic su **salvare**.

    > [!NOTE]
    > Se si utilizza una build di rilascio, disabilitare il debug nel file Web. config quando esegue la pubblicazione.

1. Fare clic su **Pubblica**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Pubblica l'applicazione un **Debug** configurazione del progetto nella cartella locale. Stato di avanzamento Mostra nella finestra di Output.

1. Copiare la directory del progetto ASP.NET dal computer di Visual Studio nella directory locale configurata per l'applicazione ASP.NET (in questo esempio, **C:\Publish**) nel computer del Server di Windows. In questa esercitazione si presuppone che si sta copiando manualmente, ma è possibile utilizzare altri strumenti come PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    >  Se è necessario apportare modifiche al codice o di ricompilazione, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.    Se si non esegue questa operazione si riceverà un `cannot find or open the PDB file` avviso in Visual Studio quando si tenta di eseguire il debug del processo.

1. In Windows Server, verificare che sia possibile eseguire correttamente l'app, aprire l'app nel browser.

    Se l'app non viene eseguito correttamente, può essere presente una mancata corrispondenza tra la versione di ASP.NET installati sul server e computer di Visual Studio oppure si potrebbe avere un problema con la configurazione di IIS o il sito Web. Controlla di nuovo i passaggi precedenti.
