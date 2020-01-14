---
title: Distribuire il contenitore Docker ASP.NET nel registro di sistema ACR
description: Informazioni su come usare gli strumenti del contenitore di Visual Studio per distribuire un'app Web ASP.NET o ASP.NET Core in un registro contenitori
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916920"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Distribuire un contenitore ASP.NET in un registro contenitori con Visual Studio

## <a name="overview"></a>Panoramica di

Docker è un motore di contenitori leggero, molto simile a una macchina virtuale, che può essere usato per l'hosting di applicazioni e servizi.
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
La procedura seguente illustra la creazione di un'app ASP.NET Core di base che verrà usata in questa esercitazione. Se si dispone già di un progetto, è possibile ignorare questa sezione.

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

    | Impostazione di      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome globalmente univoco | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | La sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Fare clic su **Crea**

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Vedere anche

[Guida introduttiva: distribuire un'istanza di contenitore in Azure usando l'interfaccia della riga di comando](/azure/container-instances/container-instances-quickstart)
