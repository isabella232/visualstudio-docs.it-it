---
title: supporto di launchSettings. JSON
description: Questo documento illustra il supporto per launchSettings. JSON in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213759"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Quando si sviluppano progetti di ASP.NET Core, è possibile configurare la modalità di avvio del progetto in scenari di sviluppo personalizzando il `launchSettings.json` contenuto del file. In Visual Studio per Mac, è possibile aggiornare questo file usando l'interfaccia utente delle opzioni del progetto o modificando `launchSettings.json` direttamente il file. Si tratta dello stesso file di configurazione che può essere usato quando si esegue Visual Studio in Windows o dalla riga di comando `dotnet`usando. Questo file viene archiviato nel progetto `Properties` nella cartella.

Per informazioni più dettagliate, è possibile passare a [usare più ambienti in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). In questo documento verrà illustrato come aggiornare il file in Visual Studio per Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Aggiornamento della configurazione di avvio tramite Visual Studio per Mac

È possibile modificare direttamente il `launchSettings.json` in Visual Studio per Mac oppure è possibile usare le opzioni del progetto per modificarlo. Per ottenere le opzioni del progetto, fare clic con il pulsante destro del mouse sul progetto e scegliere Opzioni. Vedere l'immagine seguente.

![opzioni del menu di scelta rapida del progetto selezionate](media/vsmac-ctx-proj-options.png)

Quando si accede a questa finestra di dialogo, fare clic su Esegui > Configurazioni > predefinita.

![configurazioni di esecuzione predefinite](media/vsmac-run-config-default.png)

Ci sono principalmente due cose che verranno configurate qui.

 - Variabili di ambiente impostate all'avvio
 - URL iniziale per il progetto

## <a name="configure-environment-variables"></a>Configurare le variabili di ambiente

È possibile utilizzare la griglia per specificare i valori per le variabili di ambiente. Queste variabili di ambiente verranno impostate quando si avvia l'applicazione all'interno Visual Studio per Mac. Quando si sviluppano applicazioni di ASP.NET Core, è necessario essere a `ASPNETCORE_ENVIRONMENT` conoscenza della variabile di ambiente speciale. Per altre informazioni, vedere [usare più ambienti in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Configura URL iniziale

Per configurare l'URL con cui verrà avviata l'applicazione, passare alla scheda ASP.NET Core.

![URL iniziale delle opzioni proj](media/vsmac-run-config-default-aspnetcore.png)

Qui è possibile specificare gli URL su cui l'applicazione resterà in ascolto quando viene avviata.