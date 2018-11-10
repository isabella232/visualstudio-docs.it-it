---
title: L'accesso ai cloud privati di Azure con Visual Studio | Microsoft Docs
description: Informazioni su come accedere alle risorse del cloud privato con Visual Studio.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002961"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>L'accesso ai cloud privati di Azure con Visual Studio

Per impostazione predefinita, Visual Studio supporta gli endpoint REST di cloud di Azure. In questo articolo descrive come usare il certificato del cloud privato per accedere e interagire con il cloud privato da Visual Studio.

1. Nel portale di Azure per il cloud privato scaricare il file di impostazioni di pubblicazione o contattare l'amministratore per un file di impostazioni di pubblicazione. (Il file con estensione `.publishsettings`.)

1. In Visual Studio **Esplora Server**, fare doppio clic il **Azure** nodo e selezionare **Gestisci e filtra sottoscrizioni**.

    ![Comando Gestisci sottoscrizioni](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. Nel **Gestisci sottoscrizioni Microsoft Azure** finestra di dialogo, seleziona la **certificati** tab, quindi selezionare **importazione**.

    ![L'importazione di certificati di Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. Nel **Importa sottoscrizioni Microsoft Azure** finestra di dialogo, seleziona **Sfoglia**.

    ![Pulsante Sfoglia nella finestra di dialogo Importa sottoscrizioni Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. Nel **aperto** finestra di dialogo, individuare la directory in cui è stato salvato il file di impostazioni di pubblicazione, selezionare il file e quindi selezionare **Open**.

    ![Selezionare il file di impostazioni di pubblicazione](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Quando restituito per il **Importa sottoscrizioni Microsoft Azure** finestra di dialogo, seleziona **importazione**.

    ![Importare il file di impostazioni di pubblicazione](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    I certificati vengono importati dal file di impostazioni di pubblicazione in Visual Studio e a questo punto è possibile interagire con le risorse del cloud privato.

