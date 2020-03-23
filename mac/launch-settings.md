---
title: Supporto per launchSettings.json
description: Questo documento illustra il supporto per launchSettings.json in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715928"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Quando si sviluppano ASP.NET progetti Core, è possibile configurare la modalità di avvio del progetto negli scenari di sviluppo personalizzando il contenuto del file launchSettings.json. In Visual Studio per Mac è possibile aggiornare questo file usando l'interfaccia utente delle opzioni del progetto o modificandolo direttamente. Questo file è lo stesso file di configurazione che è possibile utilizzare `dotnet`quando si esegue Visual Studio in Windows o dalla riga di comando tramite . Questo file viene archiviato nel progetto nella cartella Proprietà.

Per informazioni più dettagliate, vedere [Usare più ambienti in ASP.NET Core.](/aspnet/core/fundamentals/environments) In questo articolo verrà illustrato come aggiornare questo file in Visual Studio per Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aggiornare la configurazione di avvio utilizzando Visual Studio per MacUpdate the start configuration by using Visual Studio for Mac

È possibile modificare direttamente il file launchSettings.json in Visual Studio per Mac oppure è possibile usare le opzioni di progetto per modificarlo. Per accedere alle opzioni del progetto, fare clic con il pulsante destro del mouse sul progetto e scegliere **Opzioni**.

![Menu di scelta rapida del progetto con l'opzione "Opzioni" selezionata](media/vsmac-ctx-proj-options.png)

Selezionare **Esegui** > **configurazioni** > **predefinite**.

!["Esegui", "Configurazioni" e "Predefinito" nelle opzioni di progetto](media/vsmac-run-config-default.png)

Principalmente, si configureranno due cose qui:

 - Variabili di ambiente
 - URL dell'app per il progetto

## <a name="configure-environment-variables"></a>Configurare le variabili di ambiente

È possibile utilizzare la griglia per specificare i valori per le variabili di ambiente. Queste variabili di ambiente verranno impostate quando si avvia l'applicazione in Visual Studio per Mac.These environment variables will be set when you start your application in Visual Studio for Mac. Quando si sviluppano ASP.NET applicazioni Core, è `ASPNETCORE_ENVIRONMENT` necessario tenere presente la variabile di ambiente speciale. Per altre informazioni, vedere [Usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurare l'URL di avvio

Per configurare l'URL con cui verrà avviata l'applicazione, passare alla scheda **ASP.NET Core.**

![URL dell'applicazione nelle opzioni del progetto](media/vsmac-run-config-default-aspnetcore.png)

Qui è possibile specificare l'URL su cui l'applicazione rimarrà in ascolto all'avvio.