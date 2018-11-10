---
title: Creazione di un progetto di servizio cloud di Azure con Visual Studio | Microsoft Docs
description: Informazioni su come creare un progetto di servizio cloud di Azure con Visual Studio
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003030"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Creazione di un progetto di servizio cloud di Azure con Visual Studio
Gli strumenti di Azure per Visual Studio offre un modello di progetto che consente di creare un [servizio cloud di Azure](/azure/cloud-services/cloud-services-choose-me), ovvero un semplice servizio di Azure per utilizzo generico. Dopo aver creato il progetto, Visual Studio consente di configurare, eseguire il debug e distribuire il servizio cloud in Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Procedura per creare un progetto di servizio cloud di Azure in Visual Studio
In questa sezione illustra la creazione di un progetto di servizio cloud di Azure in Visual Studio con uno o più ruoli web.  

1. Avviare Visual Studio come amministratore.

1. Nel menu principale, selezionare **File** > **New** > **progetto**.

1. Selezionare **Cloud** nell'oggetto visivo C# o Visual Basic nodi del modello di progetto e selezionare **servizio Cloud di Azure** dall'elenco dei modelli.

    ![Nuovo servizio cloud di Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Specificare la versione di .NET Framework da usare per sviluppare il progetto.

1. Immettere un nome e percorso per il progetto e un nome per la soluzione. 

1. Scegliere **OK**.

1. Nel **nuovo servizio Cloud di Microsoft Azure** finestra di dialogo selezionare i ruoli che si desidera aggiungere e scegliere il pulsante freccia destra per aggiungerli alla soluzione.

    ![Selezionare i nuovi ruoli del servizio cloud di Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Per rinominare un ruolo che è stato aggiunto, passare il mouse sul ruolo nella **nuovo servizio Cloud di Microsoft Azure** finestra di dialogo e, dal menu di scelta rapida, selezionare **rinominare**. È inoltre possibile rinominare un ruolo all'interno della soluzione (nelle **Esplora soluzioni**) dopo che è stato aggiunto.

    ![Rinominare il ruolo di servizi cloud di Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Il progetto Azure in Visual Studio contiene le associazioni ai progetti di ruolo nella soluzione. Il progetto include anche il *file di definizione del servizio* e *file di configurazione del servizio*:

- **File di definizione del servizio** -definisce le impostazioni di runtime per l'applicazione, tra cui quali ruoli sono obbligatori, endpoint e le dimensioni della macchina virtuale. 
- **File di configurazione del servizio** -configura il numero di istanze di un ruolo vengono eseguite e i valori delle impostazioni definiti per un ruolo. 

Per altre informazioni su questi file, vedere [configurare i ruoli per un servizio cloud di Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Passaggi successivi
- [Gestione dei ruoli nei progetti servizio cloud di Azure con Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
