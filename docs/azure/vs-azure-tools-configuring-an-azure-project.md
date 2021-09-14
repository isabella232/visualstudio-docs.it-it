---
title: Configurare un progetto di servizio cloud di Azure
description: Informazioni su come configurare un progetto di servizio cloud di Azure in Visuali Studio, in base ai requisiti specifici per il progetto.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 59b4c08f0dfcc4a8712996f26ee9e4b7fcdb6771
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633179"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Configurare un progetto di servizio cloud di Azure con Visual Studio
È possibile configurare un progetto di servizio cloud di Azure, in base ai requisiti specifici per il progetto. È possibile impostare proprietà per il progetto per le categorie seguenti:

- **Pubblicare un servizio cloud in Azure** - È possibile impostare una proprietà per verificare che un servizio cloud esistente distribuito in Azure non venga eliminato inavvertitamente.
- **Eseguire o eseguire il debug di** un servizio cloud nel computer locale: è possibile selezionare una configurazione del servizio da usare e indicare se si vuole avviare il Archiviazione di Azure Emulator.
- **Convalidare un pacchetto del servizio cloud quando viene creato** - È possibile decidere di trattare tutti gli avvisi come errori in modo da assicurarsi che il pacchetto del servizio cloud venga distribuito senza problemi.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Procedura per configurare un progetto di servizio cloud di Azure
1. Aprire o creare un progetto di servizio cloud in Visual Studio

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà** dal menu di scelta rapida.

1. Nella pagina delle proprietà del progetto, selezionare la scheda **Sviluppo**.

    ![Menu Proprietà del progetto](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Impostare **Chiedi conferma prima di eliminare una distribuzione esistente** su **True**. Questa impostazione aiuta a evitare l'eliminazione involontaria di una distribuzione esistente in Azure.

1. Per indicare la **Configurazione del servizio** da usare durante l'esecuzione o il debug del servizio cloud in locale, nell'elenco Configurazione servizio scegliere la configurazione del servizio. Per altre informazioni su come modificare una configurazione del servizio per un ruolo, vedere [Procedura: Configurare i ruoli di un servizio cloud di Azure con Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Impostare **Avvia Archiviazione di Azure Emulator** su True **per** avviare il Archiviazione di Azure Emulator quando si esegue o si esegue il debug del servizio cloud in locale.

1. Per assicurarsi che non sia possibile pubblicare se sono presenti errori di convalida del pacchetto, in **Considera gli avvisi come errori** scegliere **True**.

1. Per assicurarsi che il ruolo Web usi la stessa porta a ogni avvio in locale in IIS Express, in **Usa le porte del progetto Web** scegliere **True**.

1. Dalla barra degli strumenti di Visual Studio selezionare **Salva**.

## <a name="next-steps"></a>Passaggi successivi
- [Configurare un progetto di servizio cloud di Azure tramite più configurazioni del servizio](vs-azure-tools-multiple-services-project-configurations.md)
