---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Impostazione | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: ba9de2e6af5c066e83b75576f9b104f20908aec6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-easy-tables"></a>Creare tabelle semplici

Ora che in Azure è disponibile un'app per dispositivi mobili con inizializzazione di tabelle semplici, è il momento di creare le tabelle con cui tenere traccia dei dati inviati da un gioco Unity.

## <a name="setup-the-crash-heatmap-table"></a>Configurare la tabella della mappa termica degli impatti

1. Nel portale di Azure fare clic su Tutte le risorse e quindi selezionare l'app per dispositivi mobili configurata per le tabelle semplici nei passaggi precedenti.

  ![Selezionare l'app per dispositivi mobili](media/vstu_azure-setup-table-schema-image1.png)

2. Scorrere verso il basso fino all'intestazione **DISPOSITIVI MOBILI** e selezionare **Tabelle semplici**. Non dovrebbe comparire più alcun avviso relativo all'inizializzazione dell'app per le tabelle semplici.  

  ![Selezionare tabelle semplici](media/vstu_azure-setup-table-schema-image2.png)

3. Fare clic sul pulsante **Aggiungi**.

  ![Fare clic su Aggiungi.](media/vstu_azure-setup-table-schema-image3.png)

4. Denominare la tabella "**CrashInfo**" e fare clic su **OK**. Per le altre opzioni lasciare invariate le impostazioni predefinite.

  > [!WARNING]
  > Questo nome deve corrispondere al nome della classe di modelli di dati creata più avanti nella procedura dettagliata.

  ![Assegnare un nome e fare clic su OK](media/vstu_azure-setup-table-schema-image4.png)

5. Al termine della creazione della nuova tabella verrà visualizzata una notifica.

> [!NOTE]
> Con le tabelle semplici, in realtà, lo schema della tabella viene creato dinamicamente man mano che si aggiungono dati. Ciò significa che non è necessario impostare manualmente le colonne di dati in questo passaggio.

## <a name="setup-the-leaderboard-table"></a>Configurare la tabella del tabellone punteggi

1. Tornare al pannello Tabelle semplici e fare clic su **Aggiungi** per aggiungere una seconda tabella.

  ![Aggiungere una seconda tabella](media/vstu_azure-setup-table-schema-image10.png)

2. Denominare la nuova tabella "**HighScoreInfo**" e fare clic su **OK**. Per le altre opzioni lasciare invariate le impostazioni predefinite.

  > [!WARNING]
  > Questo nome deve corrispondere al nome della classe di modelli di dati creata più avanti nella procedura dettagliata.

  ![Assegnare un nome e fare clic su OK](media/vstu_azure-setup-table-schema-image11.png)

3. Al termine della creazione della nuova tabella verrà visualizzata una notifica.


## <a name="next-step"></a>Passaggio successivo

* [Preparare l'ambiente di sviluppo](visual-studio-tools-for-unity-azure-prepare.md)
