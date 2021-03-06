---
title: Distribuire in una cartella locale
description: Informazioni su come usare lo strumento di pubblicazione per pubblicare app ASP.NET, ASP.NET Core, .NET Core e Python in una cartella da Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23ef2036af7b93ee6eeaaa14cb8733a4e0ced638
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249527"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Distribuire un'app in una cartella con Visual Studio

È possibile usare lo strumento di **pubblicazione** per pubblicare app ASP.NET, ASP.NET Core, .NET Core e Python in una cartella da Visual Studio. Per Node.js la procedura è supportata, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop di Windows in una cartella, vedere [distribuire un'app desktop usando ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic). Per C++/CLR, vedere [Distribuire un'app nativa tramite ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) oppure per C/C++, vedere [Distribuire un'app nativa tramite un progetto di installazione](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop di Windows .NET Core 3,1 o successiva in una cartella, vedere [distribuire un'applicazione Windows .NET tramite ClickOnce](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Distribuire in una cartella locale

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Il comando pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se sono stati configurati in precedenza tutti i profili di pubblicazione, viene visualizzata la finestra **pubblica** . Selezionare **Nuovo**.

1. Nella finestra **Publish (pubblica** ) selezionare **Folder (cartella**).

   ![Scegliere la cartella come destinazione di pubblicazione](../deployment/media/quickstart-publish-folder-new.png "Scegli cartella")

   ::: moniker range=">=vs-2019"

   Se si distribuisce un'applicazione Windows .NET Core 3,1 o successiva, potrebbe essere necessario selezionare la **cartella** nella finestra di **destinazione specifica** .

   ![Scegliere una cartella come destinazione specifica](../deployment/media/quickstart-publish-folder-targets.png "Scegliere una destinazione specifica")

   Se si vuole pubblicare un'applicazione Windows .NET Core 3,1 o successiva con ClickOnce, vedere [distribuire un'applicazione Windows .NET tramite ClickOnce](quickstart-deploy-using-clickonce-folder.md).
   ::: moniker-end

1. Immettere un percorso o selezionare **Sfoglia** per specificare una cartella.

   ![Specificare il percorso della cartella](../deployment/media/quickstart-publish-folder-path.png "Scegli cartella")

   ::: moniker range=">=vs-2019"
   Fare clic su **fine** per salvare il profilo.

   ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Selezionare **Pubblica**. Visual Studio compila il progetto e lo pubblica nella cartella specificata.

   ::: moniker range="vs-2017"
   Viene visualizzato il riquadro **Pubblica** delle proprietà del progetto con un riepilogo del profilo.

   ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Per configurare le impostazioni di distribuzione, selezionare **modifica** nel riepilogo del profilo di pubblicazione e selezionare la scheda **Impostazioni** .

   Le impostazioni visualizzate dipendono dal tipo di applicazione. Nella figura seguente sono illustrate le impostazioni di esempio per un'app ASP.NET Core.

    ![Impostazioni del profilo](../deployment/media/quickstart-profile-settings.png "Impostazioni del profilo")

    Per ulteriori informazioni sulla scelta delle impostazioni in .NET, vedere gli argomenti seguenti:

    - [Distribuzione autonoma e dipendente dal Framework](/dotnet/core/deploying/)
    - [Identificatori di runtime di destinazione (RID portatile, et al)](/dotnet/core/rid-catalog)
    - [Configurazioni di debug e di rilascio](../ide/understanding-build-configurations.md)

1. Configurare le opzioni, ad esempio se distribuire una configurazione di debug o di rilascio e selezionare **Salva**.

1. Per pubblicare di nuovo, selezionare **Pubblica**.

Distribuire i file pubblicati con il metodo desiderato. È ad esempio possibile inserire i file in un file *zip*, usare un semplice comando di copia o distribuire i file con un pacchetto di installazione a scelta.

## <a name="next-steps"></a>Passaggi successivi

Per le app .NET:

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs)
- [Pubblicazione di applicazioni .NET Core (distribuzioni indipendenti dal Framework e indipendenti)](/dotnet/core/deploying/)
- [Distribuire il .NET Framework e le applicazioni](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [Distribuire un'applicazione Windows .NET tramite ClickOnce](quickstart-deploy-using-clickonce-folder.md).
 ::: moniker-end
