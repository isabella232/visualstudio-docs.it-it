---
title: Configurare un Host Docker con VirtualBox | Documentazione Microsoft
description: Istruzioni passo a passo per configurare un'istanza di Docker predefinita usando Docker Machine e VirtualBox
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140722"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>Configurare un Host Docker con VirtualBox
## <a name="overview"></a>Panoramica
Questo articolo consente di configurare un'istanza di Docker predefinita usando Docker Machine e VirtualBox.
Se si utilizza il [Docker per Windows](https://www.docker.com/products/docker-desktop), questa configurazione non è necessaria.

## <a name="prerequisites"></a>Prerequisiti
È necessario installare gli strumenti seguenti.

* [Docker Toolbox](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Configurare il client Docker con Windows PowerShell
Per configurare un client Docker, è sufficiente aprire Windows PowerShell ed eseguire la procedura seguente:

1. Creare un'istanza di host docker predefinita.

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. Verificare che l'istanza predefinita sia configurata e in esecuzione. Verrà visualizzata un'istanza denominata `default' in esecuzione.

    ```PowerShell
    docker-machine ls
    ```

    ![docker-machine ls output](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. Impostare l'host corrente come predefinito e configurare la shell.

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. Visualizzare i contenitori del Docker attivi. L'elenco deve essere vuoto.

    ```PowerShell
    docker ps
    ```

    ![docker ps output](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> Ogni volta che si riavvia il computer di sviluppo, sarà necessario riavviare l'host Docker locale.
> A questo scopo, al prompt dei comandi eseguire questo comando: `docker-machine start default`.
