---
title: Uso dell'emulatore Express per eseguire e il debug di un servizio cloud di Azure in un computer locale | Microsoft Docs
description: Uso dell'emulatore Express per eseguire e il debug di un servizio cloud in un computer locale
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002341"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso dell'emulatore Express per eseguire un servizio cloud di Azure ed eseguirne il debug in un computer locale
Con Emulator Express, è possibile testare e il debug di un servizio cloud senza eseguire Visual Studio come amministratore. È possibile impostare le impostazioni del progetto per usare l'emulatore Express o l'emulatore completo, a seconda dei requisiti del servizio cloud. Per altre informazioni sull'emulatore completo, vedere [eseguire un'applicazione Azure nell'emulatore di calcolo](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso dell'emulatore Express in Visual Studio
Quando si crea un progetto Azure in Azure SDK 2.3 o versione successiva, Emulator Express viene utilizzato automaticamente. Per i progetti esistenti creati con una versione precedente del SDK di Azure, usare la procedura seguente per selezionare l'emulatore Express:

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **proprietà**.

1. Nelle pagine delle proprietà di progetti, selezionare la **Web** scheda.

    ![Proprietà per un progetto di servizio cloud di Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Sotto **Server di sviluppo locale**, selezionare **opzione Usa IIS Express**.

1. Sotto **emulatore**, selezionare **Usa emulatore Express**.
   
1. Per avviare l'emulatore Express, eseguire il comando seguente al prompt dei comandi: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitazioni dell'emulatore Express
I seguenti problemi sono note le limitazioni dell'emulatore Express: 

- L'emulatore Express non è compatibile con il Server Web IIS.
- Il servizio cloud può contenere più ruoli, ma ogni ruolo è limitato a un'istanza.
- Non è possibile accedere i numeri di porta inferiori a 1000. Se si usa un provider di autenticazione che in genere Usa una porta inferiore a 1000, si potrebbe essere necessario modificare questo valore per un numero di porta superiore a 1000.
- Eventuali limitazioni applicabili all'emulatore di calcolo di Azure si applicano anche all'emulatore Express. Ad esempio, è possibile avere più di 50 istanze di ruolo per la distribuzione. Per altre informazioni sull'emulatore di calcolo di Azure, vedere [eseguire un'applicazione Azure nell'emulatore di calcolo](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Passaggi successivi
[Debug dei servizi cloud di Azure](https://msdn.microsoft.com/library/azure/ee405479.aspx)
