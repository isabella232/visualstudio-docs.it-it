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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249884"
---
1. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **pubblica** (per Web Form, **pubblica app Web**).

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare clic su **nuovo profilo**.

1. Nella finestra di dialogo **pubblica** selezionare **cartella**, fare clic su **Sfoglia** e creare una nuova cartella, **C:\publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Screenshot della finestra di dialogo selezionare una destinazione di pubblicazione in Visual Studio con la cartella &quot;C:\Publish&quot; selezionata come destinazione di pubblicazione.":::

   Fare clic su **fine** per salvare il profilo di pubblicazione.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Screenshot della finestra di dialogo selezionare una destinazione di pubblicazione in Visual Studio con la cartella "bin\Release\Publish" selezionata come destinazione di pubblicazione.](../media/remotedbg_publish_local.png)
   Per un'app Web Form, scegliere **personalizzata** nella finestra di dialogo pubblica, immettere un nome di profilo e scegliere **OK**.

   Fare clic su **Crea profilo** nell'elenco a discesa (**Publish** è il valore predefinito).
   ::: moniker-end

1. Passa a una configurazione di debug.

   ::: moniker range=">=vs-2019"
   Scegliere **modifica** per modificare il profilo, quindi scegliere **Impostazioni**. Scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra di dialogo **Impostazioni** abilitare il debug facendo clic su **Avanti**, scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .
   ::: moniker-end

   > [!NOTE]
   > Se si usa una build di rilascio, si disabilita il debug nel file di *web.config* durante la pubblicazione.

1. Fare clic su **Pubblica**.

    ![Screenshot della scheda Impostazioni della finestra di dialogo pubblica. La configurazione è impostata su debug e viene selezionato il pulsante pubblica.](../media/remotedbg_publish_debug_config.png)

    L'applicazione pubblica una configurazione di **debug** del progetto nella cartella locale. Lo stato di avanzamento viene visualizzato nella finestra output.

1. Copiare la directory del progetto ASP.NET dal computer di Visual Studio alla directory locale configurata per l'app ASP.NET (in questo esempio, **C:\publish**) nel computer Windows Server. In questa esercitazione si presuppone che la copia venga eseguita manualmente, ma è possibile usare altri strumenti come PowerShell, XCOPY o Robocopy.

    > [!CAUTION]
    > Se è necessario apportare modifiche al codice o ricompilare, è necessario ripubblicarlo e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli. Se non si esegue questa operazione, verrà visualizzato un `cannot find or open the PDB file` avviso in Visual Studio quando si tenta di eseguire il debug del processo.

1. Nel server Windows verificare che sia possibile eseguire l'app correttamente aprendo l'app nel browser.

    Se l'app non viene eseguita correttamente, potrebbe essersi verificata una mancata corrispondenza tra la versione di ASP.NET installata nel server e il computer che esegue Visual Studio oppure è possibile che si verifichi un problema con la configurazione di IIS o del sito Web. Controllare nuovamente i passaggi precedenti.
