---
title: Configurare un progetto di servizio cloud di Azure con Visual Studio | Microsoft Docs
description: Informazioni su come configurare un progetto di servizio cloud di Azure in Visual Studio, a seconda dei requisiti per il progetto.
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002951"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Configurare un progetto di servizio cloud di Azure con Visual Studio
È possibile configurare un progetto di servizio cloud di Azure, a seconda dei requisiti per il progetto. È possibile impostare proprietà per il progetto per le categorie seguenti:

- **Pubblicare un servizio cloud in Azure** -è possibile impostare una proprietà per assicurarsi che un servizio cloud esistente distribuito in Azure non è stato eliminato accidentalmente.
- **Eseguire o eseguire il debug di un servizio cloud nel computer locale** -è possibile selezionare una configurazione del servizio da usare e indicare se si desidera avviare l'emulatore di archiviazione di Azure.
- **Convalidare un pacchetto del servizio cloud al momento della creazione** -è possibile decidere di trattare tutti gli avvisi come errori in modo che è possibile assicurarsi che il pacchetto del servizio cloud venga distribuito senza problemi. 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Passaggi per configurare un progetto di servizio cloud di Azure
1. Aprire o creare un progetto servizio cloud in Visual Studio

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **proprietà**.
   
1. Nella pagina delle proprietà del progetto, selezionare la **sviluppo** scheda.

    ![Menu proprietà del progetto](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Impostare **Chiedi conferma prima di eliminare una distribuzione esistente** al **True**. Questa impostazione consente di accertarsi di che non eliminare accidentalmente una distribuzione esistente in Azure

1. Selezionare il valore desiderato **configurazione del servizio** per indicare quale configurazione del servizio da usare quando si esegue o eseguire il debug del servizio cloud in locale. Per altre informazioni su come modificare una configurazione del servizio per un ruolo, vedere [come configurare i ruoli per un servizio cloud di Azure con Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Impostare **emulatore di archiviazione di Azure avviare** al **True** per avviare l'emulatore di archiviazione di Azure quando si esegue o eseguire il debug del servizio cloud in locale.

1. Impostare **considerarli come errori** al **True** per assicurarsi che sia possibile pubblicare se sono presenti errori di convalida del pacchetto.

1. Impostare **usano le porte del progetto web** al **True** per assicurarsi che il ruolo web usi la stessa porta ogni volta che viene avviato in locale in IIS Express.

1. Nella barra degli strumenti di Visual Studio, selezionare **salvare**.

## <a name="next-steps"></a>Passaggi successivi
- [Configurare un progetto Azure tramite più configurazioni del servizio](vs-azure-tools-multiple-services-project-configurations.md)

