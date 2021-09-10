---
title: Pubblicare in una cartella
description: È possibile usare lo strumento Pubblica per la pubblicazione di app ASP.NET Core in una cartella.
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: e2d1b0bb67c30daf13503196546f3280ceb7a635
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962021"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Pubblicare un'app Web in una cartella usando Visual Studio per Mac

È possibile usare lo strumento Pubblica per la pubblicazione di app ASP.NET Core in una cartella.

## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio 2017 per Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) installato con ASP.NET Core abilitato.
- Un progetto ASP.NET Core. Se non si ha già un progetto, è possibile [crearne uno](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-folder"></a>Pubblicare in una cartella

Con Visual Studio per Mac è possibile pubblicare i progetti ASP.NET Core in una cartella con lo strumento Pubblica. Dopo la pubblicazione in una cartella è possibile trasferire i file nel server Web per spostarli in un ambiente diverso. Per eseguire la pubblicazione in una cartella attenersi alla procedura seguente.

 1. Nel riquadro della soluzione fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Menu di scelta rapida per la pubblicazione](media/publish-context-menu.png)

 2. Se in precedenza il progetto è stato pubblicato, il profilo di pubblicazione sarà visualizzato nel menu. Selezionare il profilo di pubblicazione per avviare il processo di pubblicazione.

 3. Per pubblicare il progetto in una cartella per la prima volta, selezionare **Pubblica nella cartella**

    ![Menu di scelta rapida Pubblica nella cartella](media/publish-to-folder-context-menu.png)

 4. Viene visualizzata la finestra di dialogo **Pubblica nella cartella**. In questa finestra di dialogo è possibile personalizzare la cartella in cui verrà pubblicato il progetto. Per far ciò è possibile usare il pulsante **Sfoglia** o incollare un percorso.

 5. Dopo aver fatto clic su **Pubblica** vengono eseguite alcune operazioni. Prima di tutto viene creato un profilo di pubblicazione. Un profilo di pubblicazione è un file MSBuild che viene importato nel progetto durante il processo di pubblicazione. Contiene le proprietà che vengono usate durante il processo di pubblicazione. Questi file vengono archiviati in `Properties/PublishProfiles` e hanno estensione `.pubxml`. Successivamente, viene avviato il processo di pubblicazione. Visual Studio per Mac consente di monitorare l'avanzamento tramite la barra di stato.

    ![Barra di stato dell'IDE con lo stato della pubblicazione](media/publish-to-folder-status-bar.png)

 6. Una volta completata la pubblicazione, verrà aperta una finestra del Finder nella cartella di pubblicazione. Una volta creato, il profilo di pubblicazione viene visualizzato nel menu di scelta rapida Pubblica.

    ![Menu di scelta rapida Pubblica con profilo della cartella](media/publish-context-menu-with-folder-profile.png)

 7. Per pubblicare nuovamente il progetto con le stesse impostazioni, è possibile fare clic sul profilo nel menu di scelta rapida Pubblica.

## <a name="customize-publish-options"></a>Personalizzare le opzioni di pubblicazione

Per modificare il nome del profilo di pubblicazione che viene visualizzato nel menu di scelta rapida Pubblica, rinominare il file del profilo di pubblicazione. Assicurarsi di non modificare l'estensione del file (`.puxbml`).

Per modificare il percorso della cartella di pubblicazione, aprire il profilo di pubblicazione e modificare il valore `publishUrl`.

Per modificare la configurazione di compilazione usata, modificare la proprietà `LastUsedBuildConfiguration` nel profilo di pubblicazione.