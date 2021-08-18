---
title: Distribuire ASP.NET contenitore Docker nel registro Registro Registro Controllo di accesso
description: Informazioni su come usare Visual Studio Container Tools per distribuire un'app Web ASP.NET o ASP.NET Core in un registro contenitori
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-container-tools
ms.date: 03/15/2021
ms.author: ghogen
ms.openlocfilehash: eb1b22273a3fe946d7760bccae9583c4b1d6726c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091240"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Distribuire un contenitore ASP.NET in un registro contenitori tramite Visual Studio

## <a name="overview"></a>Panoramica

Docker è un motore contenitore leggero, simile in qualche modo a una macchina virtuale, che è possibile usare per ospitare applicazioni e servizi.
Nell'esercitazione verrà usato Visual Studio per pubblicare l'applicazione in contenitori in un [Registro Azure Container](https://azure.microsoft.com/services/container-registry).

Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione:

::: moniker range="vs-2017"
* Installare la versione più recente di [Visual Studio 2017 con](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)il carico di lavoro "sviluppo ASP.NET Web"
::: moniker-end
::: moniker range=">=vs-2019"
* Installare la versione più recente di [Visual Studio 2019 con](https://visualstudio.microsoft.com/downloads) il carico di lavoro "sviluppo ASP.NET Web"
::: moniker-end
* Installare [Docker per Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Creare un'app Web ASP.NET Core

La procedura seguente illustra la creazione di un'app ASP.NET Core di base che verrà usata in questa esercitazione. Se si ha già un progetto, è possibile ignorare questa sezione.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Pubblicare il contenitore in Registro Azure Container

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
2. Nella finestra **di dialogo Publish target** (Pubblica destinazione) selezionare Container Registry **(Registro contenitori).**
3. Scegliere **Nuovo Registro Azure Container** e fare clic su **Pubblica**.
4. Inserire i valori desiderati in **Creare un nuovo Registro Azure Container**.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Fare clic su **Crea**
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Pubblicare il contenitore in Registro Azure Container
1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Pubblica**.
2. Nella finestra **di dialogo** Pubblica selezionare **Registro Contenitori Docker**.

   ![Screenshot della finestra di dialogo Pubblica: scegliere Registro Contenitori Docker](media/container-tools/vs-2019/docker-container-registry.png)

3. Scegliere **Crea nuovo Registro Azure Container**.
 
   ![Screenshot della finestra di dialogo Pubblica: scegliere Crea nuovo Registro Azure Container](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Compilare i valori desiderati nella **Registro Azure Container** schermata.

    | Impostazione      | Valore consigliato  | Descrizione                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefisso DNS** | Nome univoco a livello globale | Nome che identifica in modo univoco il registro contenitori. |
    | **Sottoscrizione** | Scegliere la sottoscrizione | Sottoscrizione di Azure da usare. |
    | **[Gruppo di risorse](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome del gruppo di risorse in cui creare il registro contenitori. Per creare un nuovo gruppo di risorse scegliere **Nuovo**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Livello di servizio del registro contenitori  |
    | **Percorso del registro** | Un percorso vicino | Scegliere un Percorso in una [regione](https://azure.microsoft.com/regions/) nelle vicinanze o vicino ad altri servizi usati nel registro contenitori. |

    ![Finestra di dialogo Creare un'istanza di Registro Azure Container di Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Fare clic su **Crea**.

6. Scegliere **Fine** per completare il processo.
::: moniker-end

È possibile ora eseguire il pull del contenitore dal registro a qualsiasi host in grado di eseguire immagini Docker, ad esempio [Istanze di Azure Container ](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Vedi anche

[Guida introduttiva: Distribuire un'istanza di contenitore in Azure con l'interfaccia della riga di comando di Azure](/azure/container-instances/container-instances-quickstart)
