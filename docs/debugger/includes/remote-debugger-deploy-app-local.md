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
ms.openlocfilehash: 36effcf08969c5233eaee54578c9f5e3101528b96e41cb7cbf6c0025c1f7c56b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058425"
---
1. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere Pubblica **(per** Web Forms, Pubblica **app Web).**

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Fare **clic su Nuovo profilo**.

1. Nella finestra **di** dialogo Pubblica selezionare **Cartella**, fare clic **su Sfoglia** e creare una nuova cartella, **C:\Publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Screenshot della finestra di dialogo Selezionare una destinazione di pubblicazione Visual Studio con la cartella &quot;C:\Publish&quot; selezionata come destinazione di pubblicazione.":::

   Fare **clic su** Fine per salvare il profilo di pubblicazione.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Screenshot della finestra di dialogo Selezionare una destinazione di pubblicazione Visual Studio con la cartella 'bin\Release\Publish' selezionata come destinazione di pubblicazione.](../media/remotedbg_publish_local.png)
   Per un Web Forms app, scegliere **Personalizzato nella** finestra di dialogo Pubblica, immettere un nome di profilo e scegliere **OK.**

   Fare **clic su Crea** profilo nell'elenco a discesa (**Publish** è il valore predefinito).
   ::: moniker-end

1. Passare a una configurazione di debug.

   ::: moniker range=">=vs-2019"
   Scegliere **Modifica** per modificare il profilo e quindi scegliere **Impostazioni**. Scegliere una **configurazione** di debug e quindi scegliere **Rimuovi file aggiuntivi nella destinazione** nelle opzioni **Pubblicazione** file.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella finestra **Impostazioni,** abilitare il debug facendo clic su Avanti **,**  scegliere una configurazione di **debug** e quindi scegliere Rimuovi file aggiuntivi nella destinazione nelle opzioni **Pubblicazione** file.
   ::: moniker-end

   > [!NOTE]
   > Se si usa una build di rilascio, si disabilita il debug nel file *web.config* durante la pubblicazione.

1. Fare clic su **Pubblica**.

    ![Screenshot della scheda Impostazioni nella finestra di dialogo Pubblica. La configurazione è impostata su Debug e il pulsante Pubblica è selezionato.](../media/remotedbg_publish_debug_config.png)

    L'applicazione pubblica una **configurazione di** debug del progetto nella cartella locale. Lo stato di avanzamento viene visualizzato nella finestra Output.

1. Copiare la directory del progetto ASP.NET dal computer Visual Studio nella directory locale configurata per l'app ASP.NET (in questo **esempio, C:\Publish)** nel computer Windows Server. In questa esercitazione si presuppone che la copia sia manuale, ma è possibile usare altri strumenti come PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    > Se è necessario apportare modifiche al codice o ricompilare, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli. Se non si esegue questa operazione, verrà visualizzato un avviso in Visual Studio `cannot find or open the PDB file` quando si tenta di eseguire il debug del processo.

1. In Windows Server verificare che sia possibile eseguire correttamente l'app aprendo l'app nel browser.

    Se l'app non viene eseguita correttamente, potrebbe verificarsi una mancata corrispondenza tra la versione di ASP.NET installata nel server e il computer Visual Studio oppure potrebbe verificarsi un problema con la configurazione di IIS o del sito Web. Controllare di nuovo i passaggi precedenti.
