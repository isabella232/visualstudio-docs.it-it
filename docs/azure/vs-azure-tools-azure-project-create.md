---
title: Creare un progetto di servizio cloud di Azure
description: Informazioni su come creare un progetto di servizio cloud di Azure con Visual Studio
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: b5893787a1a5a7569c072d49fddd6902118f6aed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082413"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Creare un progetto di servizio cloud di Azure con Visual Studio

Visual Studio un modello di progetto che consente di creare un servizio cloud di [Azure,](/azure/cloud-services/cloud-services-choose-me)che è un semplice servizio di Azure per utilizzo generico. Dopo aver creato il progetto, Visual Studio consente di configurare, eseguire il debug e distribuire il servizio cloud in Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Procedura per creare un progetto di servizio cloud di Azure in Visual Studio
In questa sezione viene illustrata la creazione di un progetto di servizio cloud di Azure in Visual Studio con uno o più ruoli Web.

::: moniker range="vs-2017"
1. Aprire Visual Studio come amministratore.

1. Nel menu principale selezionare **File** > **nuovo** > **Project**.

1. Selezionare **Cloud** dai nodi del modello del progetto di Visual C# o Visual Basic e selezionare **Servizio cloud di Azure** dall'elenco dei modelli.

    ![Nuovo servizio cloud di Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Specificare la versione di .NET Framework che si vuole usare per sviluppare il progetto.

1. Immettere un nome e un percorso per il progetto e un nome per la soluzione.

1. Selezionare **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella casella di ricerca digitare *Cloud*, quindi scegliere **Servizio cloud di Azure**.

   ![Nuovo servizio cloud di Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Specificare un nome per il progetto e scegliere **Crea**.

   ![Assegnare un nome al progetto](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. Nella finestra di dialogo **Nuovo servizio cloud Microsoft Azure** scegliere i ruoli che si desidera aggiungere e fare clic sul pulsante con la freccia destra per aggiungerli alla soluzione.

    ![Selezionare i ruoli del nuovo servizio cloud di Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Per rinominare un ruolo che è stato aggiunto, passare il mouse sul ruolo nella finestra di dialogo **Nuovo servizio cloud Microsoft Azure** e dal menu di scelta rapida, selezionare **Rinomina**. Una volta aggiunto, un ruolo può essere rinominato (in **Esplora soluzioni**) anche nella soluzione.

    ![Rinominare un ruolo dei servizi cloud di Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Il progetto Azure in Visual Studio contiene le associazioni ai progetti di ruolo nella soluzione. Il progetto include anche i *file di definizione del servizio* e i *file di configurazione del servizio*:

- **File di definizione del servizio:** definisce le impostazioni di run-time per l'applicazione, inclusi i ruoli necessari, gli endpoint e le dimensioni della macchina virtuale.
- Il **file di configurazione del servizio** configura il numero delle istanze di un ruolo eseguite e i valori delle impostazioni definiti per un ruolo.

Per altre informazioni su queste impostazioni, vedere [Configurare i ruoli di un servizio cloud di Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Passaggi successivi
- [Gestione dei ruoli nei progetti di servizi cloud di Azure con Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
