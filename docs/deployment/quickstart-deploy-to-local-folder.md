---
title: Distribuire in una cartella locale
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781913"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Distribuire un'app in una cartella locale usando Visual Studio

È possibile usare la **pubblica** dello strumento per la pubblicazione di App ASP.NET, ASP.NET Core, .NET Core e Python in una cartella locale da Visual Studio. Per Node. js, sono supportati i passaggi, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Distribuire in una cartella locale

1. In Esplora soluzioni fare clic sul progetto e scegliere **Publish** (o utilizzare il **compilare** > **pubblica** voce di menu).

    ![Il comando Pubblica nel menu di scelta rapida progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere pubblica")

1. Se sono stati configurati tutti i profili di pubblicazione, il **pubblica** viene visualizzato il riquadro. Selezionare **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **cartella**.

    ![Scegliere la cartella locale come una destinazione di pubblicazione](../deployment/media/quickstart-publish-folder.png "Scegli cartella")

1. Immettere un percorso o selezionarne **esplorare** per specificare una cartella locale.

1. Selezionare **Pubblica**. Visual Studio compila il progetto e lo pubblica nella cartella specificata. Le proprietà del progetto **pubblica** viene visualizzato il riquadro, con un profilo il riepilogo.

    ![Riquadro delle proprietà con il riepilogo un profilo di pubblicazione](../deployment/media/quickstart-publish-folder-summary.png)

1. Per configurare le impostazioni di distribuzione, selezionare **Configure** nel profilo del riepilogo e seleziona il **impostazioni** scheda.

    ![Impostazioni del profilo](../deployment/media/quickstart-profile-settings.png "impostazioni del profilo")

1. Configurare le opzioni, ad esempio se si desidera distribuire una configurazione Debug o rilascio e quindi selezionare **salvare**.

1. Per pubblicare di nuovo, selezionare **pubblica**.

Distribuire i file pubblicati con il metodo desiderato. Ad esempio, è possibile creare un pacchetto in un *zip* file, usare un comando di copia semplice o distribuirli con qualsiasi pacchetto di installazione di propria scelta.

## <a name="next-steps"></a>Passaggi successivi

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Creare un pacchetto dell'applicazione desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Distribuire .NET Framework e applicazioni](/dotnet/framework/deployment/)
