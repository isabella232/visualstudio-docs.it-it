---
title: Modificare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come modificare Visual Studio.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 06/12/2018
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03dbfd8140249a93dfb649894dabab1c57b203c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "57984001"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti

Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. Per eseguire questa operazione, avviare il nuovo programma di installazione di Visual Studio e apportare le modifiche necessarie.

Ecco come fare.

## <a name="modify-workloads"></a>Modificare i carichi di lavoro

 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

>[!IMPORTANT]
>Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Individuare il programma di installazione di Microsoft Visual Studio")

     >[!NOTE]
     >In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. Fare clic o toccare per avviare il programma di installazione e selezionare **Modifica**.

     ![Avviare o modificare Visual Studio](media/modify-visual-studio.png "Modificare Visual Studio 2017")

     Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo è possibile modificare Visual Studio senza aggiornarlo, se si preferisce. Fare clic su **Altro** e scegliere **Modifica**.

     ![Aggiornare o modificare Visual Studio](media/modify-or-update-visual-studio.png "Aggiornare o modificare Visual Studio 2017")

3. Nella schermata **Carichi di lavoro** selezionare o deselezionare i carichi di lavoro da installare o disinstallare.

    ![Finestra di dialogo di installazione di Visual Studio 2017](media/vs2017-modify-workloads.PNG "Scegliere un carico di lavoro in Visual Studio 2017")

4. Scegliere nuovamente **Modifica**.

5. Dopo aver installato i carichi di lavoro e i componenti nuovi, scegliere **Avvia**.

## <a name="modify-individual-components"></a>Modificare i singoli componenti

Se non si intende usare la comoda funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere l'opzione **Singoli componenti** dal programma di installazione di Visual Studio, selezionare i componenti desiderati e seguire le istruzioni visualizzate.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
