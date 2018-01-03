---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: d5242dd873591abee15f528d09b6f588ea12f5ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Uso di tabelle semplici di Azure con la procedura dettagliata di Unity

![Screenshot del gioco di esempio](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Introduzione

Azure rappresenta una soluzione scalabile per l'archiviazione dei dati di telemetria e di altri dati del gioco nel cloud. Con la versione 2017 Unity supporta .NET 4.6, rendendo l'integrazione di Azure più semplice che mai grazie alla possibilità di usare Azure Mobile Client SDK.

Questi passaggi descrivono in dettaglio la procedura di impostazione di un progetto Unity che si avvale di Azure per il salvataggio dei dati di telemetria e del tabellone punteggi nel cloud.

> [!NOTE]
> Questo progetto richiede il runtime di scripting di Mono .NET 4.6 "sperimentale" in Unity 2017. [Unity ha dichiarato che presto questa sarà l'impostazione predefinita](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/). Al momento, tuttavia, è ancora etichettato come "sperimentale" e possono verificarsi problemi.

> Questa procedura dettagliata illustra un esempio di connessione al back-end di un'app per dispositivi mobili di Azure da una build Unity per PC. Al momento della stesura di questo documento, alcuni problemi noti impediscono il funzionamento di questo progetto con le piattaforme Mac e Android. Si tratta di problemi noti che verranno risolti, ma la sequenza temporale è incerta. Per altre informazioni, visitare il [forum sullo scripting sperimentale](https://forum.unity3d.com/forums/experimental-scripting-previews.107/) di Unity.

## <a name="download-the-completed-project"></a>Scaricare il progetto completato

Il progetto completato è disponibile in GitHub. La procedura dettagliata, tuttavia, presuppone che si inizi da un nuovo progetto vuoto e, quando necessario, fornisce i collegamenti per scaricare le risorse.

## <a name="walkthrough-steps"></a>Passaggi della procedura dettagliata

1. [Configurare tabelle semplici in Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Creare tabelle semplici](visual-studio-tools-for-unity-azure-setup.md)
3. [Preparare l'ambiente di sviluppo](visual-studio-tools-for-unity-azure-prepare.md)
4. [Creare classi di modelli di dati](visual-studio-tools-for-unity-azure-data.md)
5. [Implementare Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Aggiornare l'archivio certificati di protezione di Mono di Unity](visual-studio-tools-for-unity-azure-security.md)
7. [Testare la connessione client](visual-studio-tools-for-unity-azure-connection.md)
7. [Importare le risorse del gioco di esempio](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Testare il gioco di esempio](visual-studio-tools-for-unity-azure-game.md)
9. [Spiegazione di RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Spiegazione di HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Spiegazione di LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Passaggio successivo
* [Configurare tabelle semplici in Azure](visual-studio-tools-for-unity-azure-configure.md)
