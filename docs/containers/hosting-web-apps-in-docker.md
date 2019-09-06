---
title: Distribuire il contenitore Docker ASP.NET nel registro di sistema ACR
description: Informazioni su come usare gli strumenti di Visual Studio container per distribuire un'app Web di ASP.NET Core in un registro contenitori
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: b3b012bfe3b9fc359a8c9688c52aa5bfc27fd2c7
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312201"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio

## <a name="overview"></a>Panoramica

Docker è un motore contenitore leggero, simile in qualche modo a una macchina virtuale, che è possibile usare per ospitare applicazioni e servizi.
Nell'esercitazione verrà usato Visual Studio per pubblicare l'applicazione in contenitori in un [Registro Azure Container](https://azure.microsoft.com/services/container-registry).

Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione:

::: moniker range="vs-2017"
* Installare la versione più recente di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)con il carico di lavoro "sviluppo di ASP.NET e Web"
::: moniker-end
::: moniker range=">=vs-2019"
* Installare la versione più recente di [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro "sviluppo di ASP.NET e Web"
::: moniker-end
* Installare [Docker per Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Creare un'app Web ASP.NET Core
La procedura seguente illustra la creazione di un'app ASP.NET Core di base che verrà usata in questa esercitazione.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Pubblicare il contenitore in Registro Azure Container
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
2. Nella finestra di dialogo Destinazione di pubblicazione, selezionare la scheda **Registro contenitori**.
3. Scegliere **Nuovo Registro Azure Container** e fare clic su **Pubblica**.
4. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | DESCRIZIONE                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome globalmente univoco | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Fare clic su **Crea**

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).
