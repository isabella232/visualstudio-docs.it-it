---
title: Supporto di launchSettings.json
description: Questo documento illustra il supporto per launchSettings.jsin Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964590"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Quando si sviluppano progetti ASP.NET Core, è possibile configurare la modalità di avvio del progetto negli scenari di sviluppo personalizzando il contenuto del launchSettings.jsnel file . In Visual Studio per Mac è possibile aggiornare questo file usando l'interfaccia utente delle opzioni del progetto o modificandolo direttamente. Questo file è lo stesso file di configurazione che è possibile usare quando si esegue Visual Studio in Windows o dalla riga di comando tramite `dotnet` . Questo file viene archiviato nel progetto nella cartella Proprietà.

Per informazioni più dettagliate, vedere [Usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments). In questo articolo verrà illustrato come aggiornare questo file in Visual Studio per Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aggiornare la configurazione iniziale usando Visual Studio per Mac

È possibile modificare direttamente il launchSettings.jsnel file in Visual Studio per Mac oppure è possibile usare le opzioni di progetto per modificarlo. Per visualizzare le opzioni del progetto, fare clic con il pulsante destro del mouse sul progetto e scegliere **Opzioni.**

![Project menu di scelta rapida con l'opzione "Opzioni" selezionata](media/vsmac-ctx-proj-options.png)

Selezionare **Run** Configurations Default  >  **(Esegui**  >  **configurazioni predefinite).**

!["Esegui", "Configurazioni" e "Predefinito" nelle opzioni del progetto](media/vsmac-run-config-default.png)

In primo luogo, si configureranno due elementi:

- Variabili di ambiente
- URL dell'app per il progetto

## <a name="configure-environment-variables"></a>Configurare le variabili di ambiente

È possibile usare la griglia per specificare i valori per le variabili di ambiente. Queste variabili di ambiente verranno impostate quando si avvia l'applicazione in Visual Studio per Mac. Quando si sviluppano applicazioni ASP.NET Core, è necessario conoscere la variabile di `ASPNETCORE_ENVIRONMENT` ambiente speciale. Per altre informazioni, vedere [Usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurare l'URL di avvio

Per configurare l'URL con cui verrà avviata l'applicazione, passare alla **ASP.NET Core** impostazioni.

![URL dell'applicazione nelle opzioni del progetto](media/vsmac-run-config-default-aspnetcore.png)

Qui è possibile specificare l'URL su cui l'applicazione sarà in ascolto all'avvio.
