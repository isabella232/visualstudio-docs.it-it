---
title: 'Procedura: connettersi ai dati di un servizio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d6f90a99a387452500686af332edb1d112a88f82
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089118"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: connettersi ai dati in un servizio

Per connettere l'applicazione ai dati restituiti da un servizio eseguendo il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionando **Service** sul **scegliere un tipo di origine dati**pagina.

Dopo il completamento della procedura guidata, viene aggiunto al progetto un riferimento al servizio ed è immediatamente disponibile nel [finestra Origini dati](add-new-data-sources.md).

> [!NOTE]
> Gli elementi visualizzati nei **Zdroje dat** finestra dipendono le informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per il **configurazione guidata origine dati** per creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, viene visualizzato alcun elemento nel **finestra Origini dati** dopo aver completato la procedura guidata. Questo avviene perché i set di dati non tipizzati non forniscono alcuno schema, in modo che la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

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

     L'origine dati viene aggiunta per il **Zdroje dat** finestra.

## <a name="next-steps"></a>Passaggi successivi

Per aggiungere funzionalità all'applicazione, selezionare un elemento di **Zdroje dat** finestra e trascinarlo su un form per creare controlli associati. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servizi dati di servizi Windows Communication Foundation e WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)