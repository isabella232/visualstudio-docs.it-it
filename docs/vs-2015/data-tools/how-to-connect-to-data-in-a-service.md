---
title: 'Procedura: connettersi ai dati in un servizio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654694"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: connettersi ai dati di un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per connettere l'applicazione ai dati restituiti da un servizio, è possibile eseguire la [Configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selezionare **servizio** nella pagina **scegliere un tipo di origine dati** .

 Al termine della procedura guidata, al progetto viene aggiunto un riferimento al servizio che è immediatamente disponibile nella [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Se, ad esempio, il servizio restituisce un DataSet non tipizzato, al termine della procedura guidata non verrà visualizzato alcun elemento nella **finestra Origini dati** . Questo perché i set di dati non tipizzati non forniscono lo schema, quindi la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2. Selezionare **servizio** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

3. Immettere l'indirizzo del servizio che si desidera utilizzare oppure fare clic su **individua** per individuare i servizi nella soluzione corrente, quindi fare clic su **Vai**.

4. Facoltativamente, è possibile digitare un nuovo **spazio dei nomi** al posto del valore predefinito.

    > [!NOTE]
    > Fare clic su **Avanzate** per aprire la finestra di [dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md).

5. Fare clic su **OK** per aggiungere un riferimento al servizio al progetto.

6. Scegliere **Fine**.

     L'origine dati viene aggiunta alla finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

#### <a name="to-add-functionality-to-your-application"></a>Per aggiungere funzionalità all'applicazione

- Selezionare un elemento nella finestra **origini dati** e trascinarlo su un form per creare i controlli associati. Per altre informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF a un servizio WCF Data](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [services Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
