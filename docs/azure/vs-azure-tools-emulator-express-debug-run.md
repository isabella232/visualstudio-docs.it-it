---
title: Emulator Express per eseguire/eseguire il debug del servizio cloud di Azure in locale
ms.custom: SEO-VS-2020
description: Uso di Emulator Express per l'esecuzione e il debug di un servizio cloud in un computer locale
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: be382d80aea5a8f44001dc453741a1685fb644bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037473"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso dell'emulatore Express per l'esecuzione e il debug di un servizio cloud di Azure in un computer locale
Con l'emulatore Express, è possibile testare ed eseguire il debug di un servizio cloud senza eseguire Visual Studio come amministratore. È possibile configurare le impostazioni del progetto per usare l'emulatore Express o l'emulatore completo, in base ai requisiti del servizio cloud. Per altre informazioni sull'emulatore completo, vedere [Eseguire un'applicazione Azure nell'emulatore di calcolo](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso dell'emulatore Express in Visual Studio
Quando si crea un progetto di Azure in Azure SDK 2.3 o versione successiva, l'emulatore Express è selezionato automaticamente. Per i progetti esistenti creati con una versione precedente dell'SDK di Azure, attenersi alla procedura seguente per selezionare l'emulatore Express:

1. Creare o aprire un progetto del servizio cloud di Azure in Visual Studio.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere Proprietà dal menu **di scelta rapida.**

1. Nelle pagine delle proprietà di progetti, selezionare la scheda **Web**.

    ![Proprietà di un progetto di servizio cloud di Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. In **Server di sviluppo locale**, scegliere **Usa l'opzione IIS Express**.

1. In **Emulatore** selezionare **Usa emulatore Express**.

1. Per avviare l'emulatore Express, eseguire il comando seguente al prompt dei comandi:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitazioni dell'emulatore Express
Di seguito sono indicati alcuni problemi causati da limiti noti dell'emulatore Express:

- L'emulatore Express non è compatibile con il Server Web IIS.
- Il servizio cloud può contenere più ruoli, ma ogni ruolo è limitato a un'istanza.
- È possibile accedere ai numeri di porta inferiori a 1000. Se si usa un provider di autenticazione che in genere usa una porta inferiore a 1000, potrebbe essere necessario modificare questo valore per i numeri di porta superiori a 1000.
- Qualsiasi limitazione dell'emulatore di calcolo di Azure si applica anche all'emulatore Express. Ad esempio, non si può disporre di più di 50 istanze del ruolo per ogni distribuzione. Per altre informazioni sull'emulatore completo di Azure, vedere [Eseguire un'applicazione Azure nell'emulatore di calcolo](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Passaggi successivi
[Debug dei servizi cloud di Azure](vs-azure-tools-debugging-cloud-services-overview.md)
