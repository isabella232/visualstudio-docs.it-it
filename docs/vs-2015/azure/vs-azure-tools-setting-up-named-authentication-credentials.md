---
title: Configurare credenziali per l'autenticazione denominate | Microsoft Docs
description: Informazioni su come fornire le credenziali che Visual Studio può usare per autenticare le richieste ad Azure, in modo che è possibile pubblicare un'applicazione in Azure da Visual Studio o monitorare un servizio cloud esistente.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002911"
---
# <a name="set-up-named-authentication-credentials"></a>Configurare le credenziali di autenticazione denominate

Per pubblicare un'applicazione in Azure o per monitorare un servizio cloud esistente, Visual Studio richiede le credenziali per autenticare le richieste ad Azure, vale a dire l'ID sottoscrizione di Azure e un certificato X.509 v3 valido con una chiave di almeno 2048 bit. È fornire le credenziali tramite uno dei metodi seguenti:

- In Visual Studio selezionare **Visualizza > Esplora Server**, fare doppio clic sul **Azure** nodo, seleziona **Connetti a sottoscrizione di Microsoft Azure**ed eseguire l'accesso.
- Creare un file di sottoscrizione (`.publishsettings`), che contiene una chiave pubblica del certificato. Il file di sottoscrizione può contenere le credenziali per più di una sottoscrizione, come descritto in questo articolo.

Nota: queste credenziali sono diverse da quelle usate per autenticare le richieste ai servizi di archiviazione di Azure.

## <a name="create-a-subscription-file"></a>Creare un file di sottoscrizione

In Esplora Server, fare doppio clic il **Azure** nodo e selezionare **Gestisci e filtra sottoscrizioni**. Quindi selezionare il **certificati** scheda e quindi eseguire una delle azioni seguenti:

- Selezionare **importazione** per aprire il **Importa sottoscrizioni Microsoft Azure** nella finestra di dialogo. Selezionare il **Scarica file di sottoscrizione** collegare e nel browser salvare il file scaricato in un percorso temporaneo. Nella finestra di dialogo, selezionare il percorso di download e quindi importarlo per l'uso in autenticazione.
- Scegliere una sottoscrizione attiva e selezionare **modifica**, che apre una finestra di dialogo in cui si modifica una sottoscrizione esistente per l'uso in autenticazione.
- Selezionare **New** per aprire il **nuova sottoscrizione** finestra di dialogo e specificare i dettagli richiesti. Per caricare il certificato al cloud di servizio sono indicate nella finestra di dialogo, accedere al portale di Azure, passare al servizio cloud, selezionare **Impostazioni > certificati di gestione**, selezionare **caricare**, quindi specificare il percorso di `.cer` file.

Se si desidera creare un certificato, è possibile fare riferimento alle istruzioni in [creare e caricare un certificato di gestione per Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) e quindi caricare manualmente il certificato per il [portale di Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Passaggi successivi

- [Panoramica generale delle App Web](https://docs.microsoft.com/azure/app-service/)
- [Distribuire l'app nel servizio App di Azure](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Distribuire processi Web usando Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Creare e distribuire un servizio cloud](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)