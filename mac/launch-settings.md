---
title: Supporto di launchSettings.json
description: Questo documento illustra il supporto per launchSettings.jsin Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247929"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Quando si sviluppano progetti di ASP.NET Core, è possibile configurare la modalità di avvio del progetto in scenari di sviluppo personalizzando il contenuto del launchSettings.jssu file. In Visual Studio per Mac, è possibile aggiornare questo file usando l'interfaccia utente delle opzioni del progetto o modificando direttamente il file. Si tratta dello stesso file di configurazione che è possibile usare quando si esegue Visual Studio in Windows o dalla riga di comando tramite `dotnet` . Questo file viene archiviato nel progetto nella cartella Proprietà.

Per informazioni più dettagliate, vedere [usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments). Questo articolo illustra come aggiornare il file in Visual Studio per Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aggiornare la configurazione di avvio usando Visual Studio per Mac

È possibile modificare direttamente il launchSettings.jsnel file Visual Studio per Mac oppure è possibile usare le opzioni del progetto per modificarlo. Per ottenere le opzioni del progetto, fare clic con il pulsante destro del mouse sul progetto e scegliere **Opzioni**.

![Menu di scelta rapida del progetto con "Options" selezionato](media/vsmac-ctx-proj-options.png)

Selezionare **Esegui**  >  **configurazioni**  >  **predefinite**.

!["Run", "Configurations" e "default" nelle opzioni del progetto](media/vsmac-run-config-default.png)

Principalmente, verranno configurati due elementi:

- Variabili di ambiente
- URL app per il progetto

## <a name="configure-environment-variables"></a>Configurare le variabili di ambiente

È possibile utilizzare la griglia per specificare i valori per le variabili di ambiente. Queste variabili di ambiente verranno impostate quando si avvia l'applicazione in Visual Studio per Mac. Quando si sviluppano applicazioni ASP.NET Core, è necessario essere a conoscenza della `ASPNETCORE_ENVIRONMENT` variabile di ambiente speciale. Per altre informazioni, vedere [Usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurare l'URL iniziale

Per configurare l'URL con cui verrà avviata l'applicazione, passare alla scheda **ASP.NET Core** .

![URL applicazione nelle opzioni del progetto](media/vsmac-run-config-default-aspnetcore.png)

Qui è possibile specificare l'URL su cui l'applicazione resterà in ascolto quando viene avviata.
