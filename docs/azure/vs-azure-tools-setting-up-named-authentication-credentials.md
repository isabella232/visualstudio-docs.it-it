---
title: Configurare credenziali per l'autenticazione denominate | Microsoft Docs
description: Informazioni su come fornire le credenziali che Visual Studio può usare per l'autenticazione delle richieste ad Azure per pubblicare un'applicazione in Azure da Visual Studio o monitorare un servizio cloud esistente.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: e7d8acc861e1460cc569ce6e1bd75ce01bd6e4b4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633036"
---
# <a name="set-up-named-authentication-credentials"></a>Configurare le credenziali di autenticazione denominate

Per pubblicare un'applicazione in Azure o monitorare un servizio cloud esistente, è necessario fornire le credenziali che Visual Studio può usare per l'autenticazione delle richieste inviate ad Azure, vale a dire l'ID sottoscrizione di Azure e un certificato X.509 v3 valido con una chiave di almeno 2048 bit. È possibile fornire le credenziali tramite uno dei metodi seguenti:

- In Visual Studio selezionare **Visualizza > Esplora server**, fare clic con il pulsante destro del mouse sul nodo **Azure**, quindi selezionare **Connetti alla sottoscrizione di Microsoft Azure** ed eseguire l'accesso.
- Creare un file di sottoscrizione (`.publishsettings`) che contiene una chiave pubblica per il certificato. Il file di sottoscrizione può contenere le credenziali per più di una sottoscrizione, come descritto in questo articolo.

Nota: queste credenziali sono diverse da quelle usate per autenticare le richiesta ai servizi di archiviazione di Azure.

## <a name="create-a-subscription-file"></a>Creare un file di sottoscrizione

In Esplora server fare clic con il pulsante destro del mouse sul nodo **Azure** e quindi selezionare **Gestisci e filtra sottoscrizioni**. Selezionare quindi la scheda **Certificati** ed eseguire una delle azioni seguenti:

- Selezionare **Importa** per aprire la finestra di dialogo **Importa sottoscrizioni Microsoft Azure**. Selezionare il collegamento **Scarica file di sottoscrizione** e nel browser salvare il file scaricato in una posizione temporanea. Nella finestra di dialogo sfogliare il percorso di download e quindi importarlo per l'uso in autenticazione.
- Scegliere una sottoscrizione attiva e selezionare **Modifica** per aprire la finestra di dialogo in cui è possibile modificare una sottoscrizione esistente per l'uso in autenticazione.
- Selezionare **Nuovo** per aprire la finestra di dialogo **Nuova sottoscrizione** e inserire le informazioni richieste. Per caricare il certificato nel servizio cloud indicato nella finestra di dialogo, accedere al portale di Azure, cercare il servizio cloud, selezionare **Impostazioni > Certificati di gestione**, selezionare **Carica** e specificare il percorso al file `.cer`.

Se si vuole creare un certificato, vedere le istruzioni contenute in [Creare e caricare un certificato di gestione per Azure](/azure/cloud-services/cloud-services-certs-create) e quindi caricare manualmente il certificato nel [portale di Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Passaggi successivi

- [Panoramica di App Web](/azure/app-service/)
- [Distribuire l'app nel servizio app di Azure](/azure/app-service/app-service-deploy-local-git)
- [Distribuzione di processi Web usando Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Creare e distribuire un servizio cloud](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
