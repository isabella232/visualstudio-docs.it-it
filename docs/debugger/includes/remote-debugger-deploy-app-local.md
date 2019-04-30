---
title: Distribuire in una cartella locale
description: Distribuire un'app in una cartella locale
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407772"
---
1. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Publish** (per Web Form, **pubblicare App Web**).

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **nuovo profilo**.

1. Nel **Publish** finestra di dialogo **cartella**, fare clic su **Sfoglia**e creare una nuova cartella denominata **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Per un'app Web Form, scegli **Custom** nella finestra di dialogo di pubblicazione, immettere un nome di profilo e scegliere **OK**.

1. Fare clic su **Crea profilo** nell'elenco a discesa scegliere (**Publish** è il valore predefinito).

1. Nel **Publish** della finestra di dialogo fare clic sul **impostazioni** collegamento e quindi selezionare il **impostazioni** scheda.

1. Impostare la configurazione su **Debug**, selezionare **Elimina tutti i file esistenti prima della pubblicazione**, quindi fare clic su **Salva**.

    > [!NOTE]
    > Se si usa una build di rilascio, si disabilita il debug nel file Web. config quando si pubblica.

1. Fare clic su **Pubblica**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    L'applicazione pubblica un **Debug** configurazione del progetto nella cartella locale. Viene illustrato lo stato di avanzamento nella finestra di Output.

1. Copiare la directory del progetto ASP.NET dal computer di Visual Studio nella directory locale configurata per l'app ASP.NET (in questo esempio **C:\Publish**) nel computer Windows Server. In questa esercitazione si presuppone che si sta copiando manualmente, ma è possibile usare altri strumenti come PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    > Se è necessario apportare modifiche al codice o ricompilazione, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.    Se non si eseguire questa operazione si riceverà un `cannot find or open the PDB file` avviso in Visual Studio quando si prova a eseguire il debug del processo.

1. Nel Server di Windows, verificare che sia possibile eseguire correttamente l'app aprendo l'app nel browser.

    Se l'app non viene eseguita correttamente, potrebbe esserci una mancata corrispondenza tra la versione di ASP.NET installati sul server e computer di Visual Studio oppure si potrebbe avere un problema con la configurazione di IIS o il sito Web. Controlla di nuovo i passaggi precedenti.
