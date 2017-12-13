---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Risorse del gioco | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 3b1ad3d7dc6af48986e8b10278a8b8135843239d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="import-sample-game-assets"></a>Importare le risorse del gioco di esempio

Ora che le funzionalità di base sono state testate e si sono dimostrate funzionanti, è il momento di importare le risorse del gioco di esempio.

## <a name="import-package"></a>Importare il pacchetto

1. Scaricare il [pacchetto delle risorse del gioco di esempio](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Verificare che il progetto Unity sia aperto e quindi passare al percorso di download e fare doppio clic sul file. Verrà visualizzata la finestra di dialogo di importazione in Unity.

3. Fare clic su **All** (Tutto) e quindi su **Import** (Importa). Attendere il completamento, visualizzato dagli indicatori di stato.

  ![Importare il pacchetto](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Aggiungere scene alle impostazioni di compilazione

Al termine dell'importazione dei file, è necessario aggiungere i file di scena richiesti nelle impostazioni di compilazione del progetto Unity.

1. Nella finestra del progetto Unity, passare alla directory **Azure Easy Tables sample game assets/Scenes**.

2. Dal menu di Unity scegliere **File > Build Settings...** (File > Impostazioni di compilazione). Verrà visualizzata la finestra di dialogo Build Settings (Impostazioni di compilazione).

3. Trascinare i file **HeatmapScene**, **LeaderboardScene**, **MenuScene** e **RaceScene** dalla finestra Project (Progetto) alla sezione **Scenes In Build** (Scene nella compilazione) della finestra di dialogo Build Settings (Impostazioni di compilazione).

  ![Importare il pacchetto](media/vstu_azure-import-sample-assets-image2.png)

4. Dal menu di Unity scegliere **File > Save Project** (File > Salva progetto) per salvare le impostazioni di compilazione.

## <a name="next-step"></a>Passaggio successivo

* [Testare il gioco di esempio](visual-studio-tools-for-unity-azure-game.md)