---
title: 'Procedura: connettersi ai dati di un servizio'
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b49840a2190abfd223edf5643b8d70da1a59d6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282228"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: Connettersi ai dati di un servizio

Per connettere l'applicazione ai dati restituiti da un servizio, è possibile eseguire la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionare **servizio** nella pagina **scegliere un tipo di origine dati** .

Al termine della procedura guidata, al progetto viene aggiunto un riferimento al servizio che è immediatamente disponibile nella [finestra Origini dati](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Se, ad esempio, il servizio restituisce un DataSet non tipizzato, non viene visualizzato alcun elemento nella finestra **origini dati** al completamento della procedura guidata. Questo perché i set di dati non tipizzati non forniscono lo schema, quindi la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2. Selezionare **servizio** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

3. Immettere l'indirizzo del servizio che si desidera utilizzare oppure fare clic su **individua** per individuare i servizi nella soluzione corrente, quindi fare clic su **Vai**.

4. Facoltativamente, è possibile digitare un nuovo **spazio dei nomi** al posto del valore predefinito.

    > [!NOTE]
    > Fare clic su **Avanzate** per aprire la finestra di [dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md).

5. Fare clic su **OK** per aggiungere un riferimento al servizio al progetto.

6. Fare clic su **Fine**.

     L'origine dati viene aggiunta alla finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

Per aggiungere funzionalità all'applicazione, selezionare un elemento nella finestra **origini dati** e trascinarlo su un form per creare i controlli associati. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
