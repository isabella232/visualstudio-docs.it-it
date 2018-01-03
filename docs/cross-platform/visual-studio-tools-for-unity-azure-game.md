---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Gioco | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7d0a7da4093b8f90ab76dee55f1ec9ad6dc21679
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-sample-game"></a>Testare il gioco di esempio

Il gioco di esempio è una semplice corsa automobilistica che registra i dati relativi al comportamento del giocatore e li archivia in tabelle semplici di Azure. Il gioco di esempio include anche scene che leggono i dati da Azure e li visualizzano per il giocatore.

Questa sezione illustra in modo semplice come giocare con il gioco di esempio e come verificarne il corretto funzionamento. Le sezioni successive illustrano in maggiore dettaglio il funzionamento del gioco di esempio.

## <a name="starting-the-game"></a>Avvio del gioco

1. Nella finestra Project (Progetto) di Unity passare alla cartella **Assets/Azure Easy Tables sample game assets/Scenes**.

2. Fare doppio clic sulla voce **MenuScene** per aprirla.

3. Nella finestra Game (Gioco) di Unity, fare clic sull'**elenco a discesa delle proporzioni** e scegliere **16:9**.

  ![Impostare le proporzioni](media/vstu_azure-test-sample-game-image1.png)

4. Passare a Unity e fare clic sul pulsante **Esegui** per eseguire il gioco nell'editor di Unity.


## <a name="complete-a-race"></a>Completare una corsa

Prima di visualizzare il tabellone punteggi o la mappa termica, è consigliabile creare alcuni dati di esempio completando la corsa almeno una volta.

1. Con il gioco in esecuzione nell'editor di Unity fare clic sul pulsante **Race!** (Gioca) per avviare una nuova corsa.

2. Usare i tasti **W, A, S e D** o i **tasti di direzione** per guidare l'auto e completare un giro di pista in senso orario. Ai fini dell'esempio, assicurarsi di scontrarsi con la parete più volte lungo il percorso. L'output di debug nella console di Unity indica il momento in cui è stata registrata una collisione.

  >[!NOTE]
  > Se l'auto si capovolge e non è possibile continuare, fare clic su **Restart** (Riavvia). I dati vengono inviati ad Azure solo al termine di un giro.

  ![Avviare una corsa](media/vstu_azure-test-sample-game-image2.png)

3. Dopo che è stato oltrepassato il traguardo, il gioco deve visualizzare il messaggio **Finished** (Completato). A questo punto i dati relativi agli impatti vengono caricati in Azure.

4. Se il giro completato è tra i 10 giri più veloci, verrà richiesto di immettere il nome per il punteggio record. Immettere il nome e fare clic su **Submit** (Invia).

  ![Avviare una corsa](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Visualizzare la mappa termica

1. Fare clic sul pulsante **View Crash Heatmap** (Visualizza mappa termica impatti) o selezionare **Heatmap Crash** (Mappa termica impatti) dal menu principale.

2. La scena della mappa termica carica i dati dalla tabella CrashInfo in Azure e visualizza una sfera rossa trasparente nei punti in cui i giocatori si sono scontrati con le pareti del percorso di gara. Se si verificano più collisioni in aree sovrapposte, le sfere sono più luminose.

  ![Mappa termica](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Visualizzare il tabellone punteggi

1. Fare clic sul pulsante **Leaderboard** (Tabellone punteggi) nella scena della corsa o nel menu principale.

2. La scena del tabellone punteggi carica i dati dei record dalla tabella HighScoreInfo in Azure e visualizza il nome del giocatore e il tempo del giro per ogni punteggio.

  ![Tabellone punteggi](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Passaggio successivo

* [Spiegazione di RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
