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
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762608"
---
1. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **pubblica** (per Web Form, **pubblica app Web**).

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **nuovo profilo**.

1. Nella finestra di dialogo **pubblica** selezionare **cartella**, fare clic su **Sfoglia** e creare una nuova cartella, **C:\publish**.

    ![Screenshot della finestra di dialogo selezionare una destinazione di pubblicazione in Visual Studio con la cartella "bin\Release\Publish" selezionata come destinazione di pubblicazione.](../media/remotedbg_publish_local.png)

    Per un'app Web Form, scegliere **personalizzata** nella finestra di dialogo pubblica, immettere un nome di profilo e scegliere **OK**.

1. Fare clic su **Crea profilo** nell'elenco a discesa (**Publish** è il valore predefinito).

1. Nella finestra di dialogo **pubblica** fare clic sul collegamento **Impostazioni** , quindi selezionare la scheda **Impostazioni** .

1. Impostare la configurazione su **debug**, selezionare **Elimina tutti i file esistenti prima della pubblicazione** e quindi fare clic su **Salva**.

    > [!NOTE]
    > Se si usa una build di rilascio, si disabilita il debug nel file di web.config durante la pubblicazione.

1. Fare clic su **Pubblica**.

    ![Screenshot della scheda Impostazioni della finestra di dialogo pubblica. La configurazione è impostata su debug e viene selezionato il pulsante pubblica.](../media/remotedbg_publish_debug_config.png)

    L'applicazione pubblica una configurazione di **debug** del progetto nella cartella locale. Lo stato di avanzamento viene visualizzato nella finestra output.

1. Copiare la directory del progetto ASP.NET dal computer di Visual Studio alla directory locale configurata per l'app ASP.NET (in questo esempio, **C:\publish**) nel computer Windows Server. In questa esercitazione si presuppone che la copia venga eseguita manualmente, ma è possibile usare altri strumenti come PowerShell, XCOPY o Robocopy.

    > [!CAUTION]
    > Se è necessario apportare modifiche al codice o ricompilare, è necessario ripubblicarlo e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.    Se non si esegue questa operazione, verrà visualizzato un `cannot find or open the PDB file` avviso in Visual Studio quando si tenta di eseguire il debug del processo.

1. Nel server Windows verificare che sia possibile eseguire l'app correttamente aprendo l'app nel browser.

    Se l'app non viene eseguita correttamente, potrebbe essersi verificata una mancata corrispondenza tra la versione di ASP.NET installata nel server e il computer che esegue Visual Studio oppure è possibile che si verifichi un problema con la configurazione di IIS o del sito Web. Controllare nuovamente i passaggi precedenti.
