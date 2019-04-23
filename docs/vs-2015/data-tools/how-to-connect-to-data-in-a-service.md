---
title: 'Procedura: Connettersi ai dati in un servizio | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3361ba51607924ee0bd0701f6f2dddf12334f93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090381"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: Connettersi ai dati di un servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per connettere l'applicazione ai dati restituiti da un servizio eseguendo il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selezionando **Service** sul **scegliere un tipo di origine dati**pagina.  
  
 Dopo il completamento della procedura guidata, viene aggiunto al progetto un riferimento al servizio ed è immediatamente disponibile nel [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, quindi non ci sono elementi vengono visualizzati nei **finestra Origini dati** dopo aver completato la procedura guidata. Questo avviene perché i set di dati non tipizzati non forniscono alcuno schema, in modo che la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio  
  
1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
2. Selezionare **Service** nel **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.  
  
3. Immettere l'indirizzo del servizio che si desidera usare oppure fare clic su **Discover** per individuare servizi nella soluzione corrente e quindi fare clic su **Vai**.  
  
4. Facoltativamente, una nuova **Namespace** possono essere digitate al posto del valore predefinito.  
  
    > [!NOTE]
    >  Fare clic su **avanzate** per aprire il [configurare Service Reference Dialog Box](../data-tools/configure-service-reference-dialog-box.md).  
  
5. Fare clic su **OK** per aggiungere un riferimento al servizio al progetto.  
  
6. Scegliere **Fine**.  
  
     L'origine dati viene aggiunta alla finestra **Origini dati**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
#### <a name="to-add-functionality-to-your-application"></a>Per aggiungere funzionalità all'applicazione  
  
- Selezionare un elemento nel **Zdroje dat** finestra e trascinarlo su un form per creare controlli associati. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
