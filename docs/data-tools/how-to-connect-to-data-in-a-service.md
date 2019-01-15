---
title: 'Procedura: Connettersi ai dati di un servizio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 66a13ac6f23caa3e6ccf28d5d68c03b3fe7fdb4f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923874"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: Connettersi ai dati di un servizio

Per connettere l'applicazione ai dati restituiti da un servizio eseguendo il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionando **Service** sul **scegliere un tipo di origine dati**pagina.

Dopo il completamento della procedura guidata, viene aggiunto al progetto un riferimento al servizio ed è immediatamente disponibile nel [finestra Origini dati](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, viene visualizzato alcun elemento nel **Zdroje dat** finestra dopo aver completato la procedura guidata. Questo avviene perché i set di dati non tipizzati non forniscono alcuno schema, in modo che la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio

1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2.  Selezionare **Service** nel **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

3.  Immettere l'indirizzo del servizio che si desidera usare oppure fare clic su **Discover** per individuare servizi nella soluzione corrente e quindi fare clic su **Vai**.

4.  Facoltativamente, è possibile digitare un nuovo **Namespace** al posto del valore predefinito.

    > [!NOTE]
    > Fare clic su **avanzate** per aprire il [nella finestra di dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md).

5.  Fare clic su **OK** per aggiungere un riferimento al servizio al progetto.

6.  Scegliere **Fine**.

     L'origine dati viene aggiunta alla finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

Per aggiungere funzionalità all'applicazione, selezionare un elemento di **Zdroje dat** finestra e trascinarlo su un form per creare controlli associati. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servizi Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)