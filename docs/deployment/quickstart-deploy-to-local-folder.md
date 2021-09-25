---
title: Distribuire in una cartella locale
description: Informazioni su come usare lo strumento Pubblica per pubblicare app ASP.NET, ASP.NET Core, .NET Core e Python in una cartella da Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c3df338150c4cf4f72aec310084c32f3db16bcd8
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429069"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Distribuire un'app in una cartella usando Visual Studio

È possibile usare lo **strumento Pubblica** per pubblicare ASP.NET, ASP.NET Core, .NET Core e Python in una cartella da Visual Studio. Per Node.js la procedura è supportata, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop Windows in una cartella, vedere Distribuire [un'app desktop .NET Windows](quickstart-deploy-using-clickonce-folder.md)usando ClickOnce , Distribuire un'app desktop .NET Framework Windows usando [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Per C++/CLR, vedere [Distribuire un'app nativa tramite ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) oppure per C/C++, vedere [Distribuire un'app nativa tramite un progetto di installazione](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop .NET Core 3.1 o versione più recente Windows in una cartella, vedere Distribuire un'applicazione [.NET Windows usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Distribuire in una cartella locale

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se in precedenza sono stati configurati profili di pubblicazione, viene **visualizzata la finestra** Pubblica. Selezionare **Nuovo**.

1. Nella finestra **Pubblica** selezionare **Cartella.**

   ![Scegliere la cartella come destinazione di pubblicazione](../deployment/media/quickstart-publish-folder-new.png "Scegliere la cartella")

   ::: moniker range=">=vs-2019"

   Se si distribuisce un'applicazione .NET Core 3.1 o versione più recente, Windows potrebbe essere necessario selezionare Cartella nella **finestra Destinazione** specifica. 

   ![Scegliere la cartella come destinazione specifica](../deployment/media/quickstart-publish-folder-targets.png "Scegliere una destinazione specifica")

   Se si vuole pubblicare un'applicazione Windows .NET Core 3.1 o versione più recente con ClickOnce, vedere Distribuire un'applicazione [.NET Windows usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).
   ::: moniker-end

1. Immettere un percorso o selezionare **Sfoglia** per specificare una cartella.

   ![Specificare il percorso della cartella](../deployment/media/quickstart-publish-folder-path.png "Scegliere la cartella")

   ::: moniker range=">=vs-2019"
   Fare **clic su** Fine per salvare il profilo.

   ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Selezionare **Pubblica**. Visual Studio compila il progetto e lo pubblica nella cartella specificata.

   ::: moniker range="vs-2017"
   Viene visualizzato il riquadro **Pubblica** delle proprietà del progetto con un riepilogo del profilo.

   ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Per configurare le impostazioni di distribuzione, **selezionare Modifica** nel riepilogo del profilo di pubblicazione e selezionare la **Impostazioni** distribuzione.

   Le impostazioni che vengono visualizzati dipendono dal tipo di applicazione. La figura seguente mostra le impostazioni di esempio per un ASP.NET Core app.

    ![Impostazioni del profilo](../deployment/media/quickstart-profile-settings.png "Impostazioni del profilo")

    Per altre informazioni sulla scelta delle impostazioni in .NET, vedere quanto segue:

    - [Distribuzione dipendente dal framework e distribuzione autonoma](/dotnet/core/deploying/)
    - [Identificatori di runtime di destinazione (RID portabile e altri)](/dotnet/core/rid-catalog)
    - [Configurazioni di debug e rilascio](../ide/understanding-build-configurations.md)

1. Configurare le opzioni, ad esempio se distribuire una configurazione di debug o di rilascio e selezionare **Salva**.

1. Per pubblicare di nuovo, selezionare **Pubblica**.

Distribuire i file pubblicati con il metodo desiderato. È ad esempio possibile inserire i file in un file *zip*, usare un semplice comando di copia o distribuire i file con un pacchetto di installazione a scelta.

## <a name="next-steps"></a>Passaggi successivi

Per le app .NET:

- [Distribuire un'applicazione .NET Core con lo strumento Pubblica](/dotnet/core/deploying/deploy-with-vs)
- [Pubblicazione di applicazioni .NET Core (distribuzioni dipendenti dal framework e indipendenti)](/dotnet/core/deploying/)
- [Distribuire le .NET Framework e le applicazioni](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [Distribuire un'applicazione .NET Windows usando ClickOnce](quickstart-deploy-using-clickonce-folder.md).
 ::: moniker-end
