---
description: A partire da Visual Studio 2019 versione 16,8, è possibile usare lo strumento di pubblicazione per pubblicare applicazioni desktop di Windows .NET Core 3,1 o versioni successive usando ClickOnce da Visual Studio.
title: Distribuire un'applicazione desktop di Windows .NET tramite ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165709"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Distribuire un'applicazione desktop di Windows .NET tramite ClickOnce

A partire da Visual Studio 2019 versione 16,8, è possibile usare lo strumento di **pubblicazione** per pubblicare applicazioni desktop di Windows .net core 3,1 o versioni successive usando ClickOnce da Visual Studio.

> [!NOTE]
> Se è necessario pubblicare un .NET Framework applicazione Windows, vedere [distribuire un'app desktop usando ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic).

## <a name="publishing-with-clickonce"></a>Pubblicazione con ClickOnce

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Il comando pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-clickonce-solution-explorer.png "Scegliere Pubblica")

1. Se in precedenza sono stati configurati profili di pubblicazione, viene visualizzata la pagina **pubblica** . Selezionare **Nuovo**.

1. Nella **pubblicazione** guidata selezionare **cartella**.

    ![Scegliere la cartella come destinazione di pubblicazione](../deployment/media/quickstart-clickonce-publish-folder-category.png "Scegli cartella")

1. Nella pagina **destinazione specifica** selezionare **ClickOnce**.

    ![Selezionare ClickOnce come destinazione specifica](../deployment/media/quickstart-clickonce-publish-folder-target.png "Scegliere ClickOnce")

1. Immettere un percorso o selezionare **Sfoglia** per selezionare il percorso di pubblicazione.

    ![Specificare il percorso per il percorso di pubblicazione](../deployment/media/quickstart-clickonce-publish-location.png "Immettere un percorso")

1. Nella pagina **percorso di installazione** selezionare la posizione da cui gli utenti installeranno l'applicazione.

    ![Specificare il percorso della cartella](../deployment/media/quickstart-clickonce-install-location.png "Scegliere il percorso di installazione")

1. Nella pagina **Impostazioni** è possibile specificare le impostazioni necessarie per ClickOnce.

1. Se si è scelto di installare da un percorso UNC o da un sito Web, questa pagina consente di specificare se l'applicazione è disponibile offline. Quando questa opzione è selezionata, l'applicazione viene elencata nel menu Start utenti, che consente di aggiornare automaticamente l'applicazione quando viene pubblicata una nuova versione. Per impostazione predefinita, gli aggiornamenti sono disponibili dal percorso di installazione.  Se si desidera disporre di un percorso diverso per gli aggiornamenti, è possibile specificare che utilizzando il collegamento Impostazioni aggiornamento. Se non si desidera che l'applicazione sia disponibile offline, verrà eseguita dal percorso di installazione.

    ![Specificare le impostazioni di pubblicazione](../deployment/media/quickstart-clickonce-unc-settings.png "Scegliere le impostazioni di pubblicazione")

1. Se si è scelto di installare da un CD, un DVD o un'unità USB, questa pagina consente anche di specificare se l'applicazione supporta gli aggiornamenti automatici. Se si sceglie di supportare gli aggiornamenti, il percorso di aggiornamento è obbligatorio e deve essere un percorso UNC o un sito Web valido.

    ![Scegliere le impostazioni di pubblicazione](../deployment/media/quickstart-clickonce-settings.png "Scegliere le impostazioni di pubblicazione")

In questa pagina è inclusa la possibilità di specificare i **file dell'applicazione** da includere nel programma di installazione, i pacchetti dei **prerequisiti** da installare e altre **Opzioni** tramite i collegamenti nella parte superiore della pagina.

Inoltre, in questa pagina è anche possibile impostare la versione di pubblicazione e se la versione verrà incrementata automaticamente a ogni pubblicazione.

> [!NOTE]
> Il numero di versione di pubblicazione è univoco per ogni profilo ClickOnce. Se si prevede di avere più di un profilo, sarà necessario tenerlo presente.

10. Nella pagina **firma manifesti** è possibile specificare se i manifesti devono essere firmati e quale certificato utilizzare.

    ![Firma i manifesti ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Nella pagina **configurazione** è possibile selezionare la configurazione del progetto desiderata.

     ![Specificare la configurazione di pubblicazione](../deployment/media/quickstart-clickonce-configuration.png)

    Per ulteriori informazioni sull'impostazione da scegliere, vedere gli argomenti seguenti:

    - [Distribuzione autonoma e dipendente dal Framework](/dotnet/core/deploying/)
    - [Identificatori di runtime di destinazione (RID portatile, et al)](/dotnet/core/rid-catalog)
    - [Configurazioni di debug e di rilascio](../ide/understanding-build-configurations.md)

1. Selezionare **fine** per salvare il nuovo profilo di pubblicazione ClickOnce.

1. Nella pagina **Riepilogo** selezionare **pubblica** e Visual Studio compila il progetto e lo pubblica nella cartella di pubblicazione specificata. Questa pagina mostra anche un riepilogo del profilo.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-clickonce-summary.png)

1. Per pubblicare di nuovo, selezionare **Pubblica**.

## <a name="next-steps"></a>Passaggi successivi

Per le app .NET:

- [Distribuire il .NET Framework e le applicazioni](/dotnet/framework/deployment/)
- [Riferimento a ClickOnce](clickonce-reference.md)
