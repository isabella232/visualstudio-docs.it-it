---
title: supporto di launchSettings. JSON
description: Questo documento illustra il supporto per launchSettings. JSON in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 7135dd05c687e3caed3ee64618ff71c093f4cd63
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322590"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Quando si sviluppano progetti di ASP.NET Core, è possibile configurare la modalità di avvio del progetto in scenari di sviluppo personalizzando il contenuto del file launchSettings. JSON. In Visual Studio per Mac, è possibile aggiornare questo file usando l'interfaccia utente delle opzioni del progetto o modificando direttamente il file. Si tratta dello stesso file di configurazione che è possibile usare quando si esegue Visual Studio in Windows o dalla riga di comando `dotnet`tramite. Questo file viene archiviato nel progetto nella cartella Proprietà.

Per informazioni più dettagliate, vedere [usare più ambienti in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). Questo articolo illustra come aggiornare il file in Visual Studio per Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aggiornare la configurazione di avvio usando Visual Studio per Mac

È possibile modificare direttamente il file launchSettings. JSON in Visual Studio per Mac oppure è possibile usare le opzioni del progetto per modificarlo. Per ottenere le opzioni del progetto, fare clic con il pulsante destro del mouse sul progetto e scegliere **Opzioni**.

![Menu di scelta rapida del progetto con "Options" selezionato](media/vsmac-ctx-proj-options.png)

Selezionare **Esegui** > configurazionipredefinite > .

!["Run", "Configurations" e "default" nelle opzioni del progetto](media/vsmac-run-config-default.png)

Principalmente, verranno configurati due elementi:

 - Variabili di ambiente
 - URL app per il progetto

## <a name="configure-environment-variables"></a>Configurare le variabili di ambiente

È possibile utilizzare la griglia per specificare i valori per le variabili di ambiente. Queste variabili di ambiente verranno impostate quando si avvia l'applicazione in Visual Studio per Mac. Quando si sviluppano applicazioni ASP.NET Core, è necessario essere a conoscenza della variabile `ASPNETCORE_ENVIRONMENT` di ambiente speciale. Per altre informazioni, vedere [usare più ambienti in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurare l'URL iniziale

Per configurare l'URL con cui verrà avviata l'applicazione, passare alla scheda **ASP.NET Core** .

![URL applicazione nelle opzioni del progetto](media/vsmac-run-config-default-aspnetcore.png)

Qui è possibile specificare l'URL su cui l'applicazione resterà in ascolto quando viene avviata.