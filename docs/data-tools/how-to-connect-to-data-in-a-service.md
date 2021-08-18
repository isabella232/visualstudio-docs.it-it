---
title: 'Procedura: connettersi ai dati di un servizio'
description: Connessione'app ai dati restituiti da un servizio eseguendo la Configurazione guidata origine dati e selezionando Servizio nella pagina Scegliere un tipo di origine dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6854b1cd7647f6bc4ac7ca92c920f7454b7ab1fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052746"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: Connettersi ai dati di un servizio

Per connettere l'applicazione ai dati restituiti [](../data-tools/media/data-source-configuration-wizard.png) da un servizio, eseguire la Configurazione guidata origine dati e selezionare Servizio nella pagina Scelta **tipo di origine** dati . 

Al termine della procedura guidata, un riferimento al servizio viene aggiunto al progetto ed è immediatamente disponibile nella [finestra Origini dati](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzato, non verrà visualizzato alcun elemento nella **finestra** Origini dati al termine della procedura guidata. Poiché i set di dati non tipizzati non forniscono lo schema, la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2. Selezionare **Servizio** nella pagina **Scegliere un tipo di origine dati** e quindi fare clic su **Avanti.**

3. Immettere l'indirizzo del servizio che si  vuole usare oppure fare clic su Individua per individuare i servizi nella soluzione corrente e quindi fare clic su **Vai**.

4. Facoltativamente, è possibile digitare un nuovo **spazio dei** nomi al posto del valore predefinito.

    > [!NOTE]
    > Fare **clic su** Avanzate per aprire la finestra di dialogo Configura riferimento al [servizio](../data-tools/configure-service-reference-dialog-box.md).

5. Fare **clic su OK** per aggiungere un riferimento al servizio al progetto.

6. Fare clic su **Fine**.

     L'origine dati viene aggiunta alla finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

Per aggiungere funzionalità all'applicazione, selezionare un elemento nella finestra Origini **dati** e trascinarlo in un form per creare controlli associati. Per altre informazioni, vedere [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Communication Foundation Services e servizi dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
