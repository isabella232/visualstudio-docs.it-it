---
description: A partire da Visual Studio 2019 versione 16.8, è possibile usare lo strumento Pubblica per pubblicare applicazioni .NET Core 3.1 o versioni più nuove Windows Desktop usando ClickOnce da Visual Studio.
title: Distribuire un'applicazione .NET Windows Desktop usando ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
ms.technology: vs-ide-deployment
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 1a093cbf609e2226967b0879e23f13631db91a79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035774"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Distribuire un'applicazione desktop Windows .NET usando ClickOnce

A partire da Visual Studio 2019 versione 16.8,  è possibile usare lo strumento Pubblica per pubblicare applicazioni .NET Core 3.1 o versioni più nuove Windows Desktop usando ClickOnce da Visual Studio.

> [!NOTE]
> Se è necessario pubblicare un'.NET Framework Windows, vedere [Distribuire un'app desktop usando ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic).

## <a name="publishing-with-clickonce"></a>Pubblicazione con ClickOnce

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-clickonce-solution-explorer.png "Scegliere Pubblica")

1. Se in precedenza sono stati configurati profili di pubblicazione, viene **visualizzata la pagina** Pubblica. Selezionare **Nuovo**.

1. Nella pubblicazione **guidata** selezionare **Cartella**.

    ![Scegliere la cartella come destinazione di pubblicazione](../deployment/media/quickstart-clickonce-publish-folder-category.png "Scegliere la cartella")

1. Nella pagina **Destinazione specifica** selezionare **ClickOnce**.

    ![Selezionare ClickOnce come destinazione specifica](../deployment/media/quickstart-clickonce-publish-folder-target.png "Scegliere ClickOnce")

1. Immettere un percorso o selezionare **Sfoglia per** selezionare il percorso di pubblicazione.

    ![Specificare il percorso per il percorso di pubblicazione](../deployment/media/quickstart-clickonce-publish-location.png "Immettere un percorso")

1. Nella pagina **Percorso di installazione** selezionare la posizione da cui gli utenti installeranno l'applicazione.

    ![Specificare il percorso della cartella](../deployment/media/quickstart-clickonce-install-location.png "Scegliere il percorso di installazione")

1. Nella pagina **Impostazioni,** è possibile specificare le impostazioni necessarie per ClickOnce.

1. Se si è scelto di eseguire l'installazione da un percorso UNC o da un sito Web, questa pagina consente di specificare se l'applicazione è disponibile offline. Se selezionata, questa opzione elenca l'applicazione nel menu Start degli utenti e consente di aggiornare automaticamente l'applicazione quando viene pubblicata una nuova versione. Per impostazione predefinita, gli aggiornamenti sono disponibili nel percorso di installazione.  Se si vuole avere un percorso diverso per gli aggiornamenti, è possibile specificarne l'uso usando il collegamento Impostazioni aggiornamento. Se non si vuole che l'applicazione sia disponibile offline, verrà eseguita dal percorso di installazione.

    ![Specificare le impostazioni di pubblicazione](../deployment/media/quickstart-clickonce-unc-settings.png "Scegliere le impostazioni di pubblicazione")

1. Se si è scelto di eseguire l'installazione da un'unità CD, DVD o USB, questa pagina consente anche di specificare se l'applicazione supporta gli aggiornamenti automatici. Se si sceglie di supportare gli aggiornamenti, il percorso di aggiornamento è obbligatorio e deve essere un percorso UNC valido o un sito Web.

    ![Scegliere le impostazioni di pubblicazione](../deployment/media/quickstart-clickonce-settings.png "Scegliere le impostazioni di pubblicazione")

In questa pagina è inclusa la possibilità di specificare  i file dell'applicazione  da includere nel programma di installazione, i pacchetti prerequisiti da installare e altre opzioni tramite i collegamenti nella parte superiore della pagina. 

In questa pagina è anche possibile impostare la versione di pubblicazione e se la versione verrà incrementata automaticamente a ogni pubblicazione.

> [!NOTE]
> Il numero di versione di pubblicazione è univoco per ogni ClickOnce di pubblicazione. Se si prevede di avere più di un profilo, è necessario tenere presente questo.

10. Nella pagina **Firma manifesti** è possibile specificare se i manifesti devono essere firmati e quale certificato usare.

    ![Firmare i ClickOnce manifesti](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Nella pagina **Configurazione** è possibile selezionare la configurazione del progetto desiderata.

     ![Specificare la configurazione di pubblicazione](../deployment/media/quickstart-clickonce-configuration.png)

    Per altre informazioni sull'impostazione da scegliere, vedere quanto segue:

    - [Distribuzione dipendente dal framework e distribuzione autonoma](/dotnet/core/deploying/)
    - [Identificatori di runtime di destinazione (RID portabile e altri)](/dotnet/core/rid-catalog)
    - [Configurazioni di debug e versione](../ide/understanding-build-configurations.md)

1. Selezionare **Fine** per salvare il nuovo ClickOnce Pubblica profilo.

1. Nella pagina **Riepilogo** selezionare **Pubblica** e Visual Studio compila il progetto e lo pubblica nella cartella di pubblicazione specificata. Questa pagina mostra anche un riepilogo del profilo.

    ![Riquadro Pubblica delle proprietà con il riepilogo di un profilo](../deployment/media/quickstart-clickonce-summary.png)

1. Per pubblicare di nuovo, selezionare **Pubblica**.

## <a name="next-steps"></a>Passaggi successivi

Per le app .NET:

- [Distribuire le .NET Framework e le applicazioni](/dotnet/framework/deployment/)
- [ClickOnce riferimento](clickonce-reference.md)
