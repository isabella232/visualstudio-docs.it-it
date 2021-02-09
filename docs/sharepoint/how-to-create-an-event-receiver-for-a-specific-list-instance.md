---
title: "Procedura: creare un ricevitore di eventi per un'istanza di elenco specifica | Microsoft Docs"
titleSuffix: ''
description: Creare un ricevitore di eventi per un'istanza di elenco specifica. Un ricevitore di eventi di istanza elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925497"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Procedura: creare un ricevitore di eventi per un'istanza di elenco specifica
  Un ricevitore di eventi di istanza elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco. Sebbene il modello di ricevitore di eventi non consenta la destinazione di un'istanza di elenco specifica, è possibile modificare un ricevitore di eventi che ha come ambito una definizione di elenco per rispondere agli eventi in un'istanza di elenco specifica.

 Per fare riferimento a un'istanza di elenco specifica, nella *Elements.xml* per il ricevitore di eventi sostituire `ListTemplateId` con `ListUrl` e aggiungere l'URL dell'istanza di elenco.

## <a name="create-a-list-instance-event-receiver"></a>Creazione di un ricevitore di eventi di istanza elenco
 Nei passaggi seguenti viene illustrato come modificare un ricevitore di eventi di un elemento di elenco per rispondere solo agli eventi che si verificano in un'istanza di elenco annunci personalizzata.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Per modificare un ricevitore di eventi per rispondere a un'istanza di elenco specifica

1. In un browser aprire il sito di SharePoint.

2. Nel riquadro di spostamento, **Elenca** il collegamento.

3. Nella pagina **tutto il contenuto del sito** scegliere il collegamento **Crea** .

4. Nella finestra di dialogo **Crea** scegliere il tipo di **annuncio** , denominare l'annuncio **TestAnnouncements**, quindi scegliere il pulsante **Crea** .

5. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di ricevitore di eventi.

6. Nell'elenco **specificare il tipo di ricevitore di eventi desiderato** scegliere **eventi elemento elenco**.

    > [!NOTE]
    > È anche possibile selezionare qualsiasi altro tipo di ricevitore di eventi che ambia a una definizione di elenco, ad esempio **elencare gli eventi di posta elettronica** o **elencare gli eventi del flusso di lavoro**.

7. Nell'elenco specificare l' **elemento che deve essere l'origine evento** scegliere **annunci**.

8. Nell'elenco **Gestisci gli eventi seguenti** selezionare la casella di controllo **elemento da aggiungere** , quindi scegliere il pulsante **fine** .

9. In **Esplora soluzioni**, in EventReceiver1, aprire *Elements.xml*.

     Il ricevitore di eventi fa riferimento attualmente alla definizione di elenco degli annunci tramite la riga seguente:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Modificare questa riga nel testo seguente:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     In questo modo il ricevitore di eventi risponderà solo agli eventi che si verificano nel nuovo elenco di annunci **TestAnnouncements** appena creato. È possibile modificare l' `ListURL` attributo in modo che faccia riferimento a qualsiasi istanza di elenco nel server SharePoint.

10. Aprire il file di codice per il ricevitore di eventi e inserire un punto di interruzione nel metodo ItemAdding.

11. Premere il tasto **F5** per compilare ed eseguire la soluzione.

12. In SharePoint scegliere il collegamento **TestAnnouncements** nel riquadro di spostamento.

13. Scegliere il collegamento **Aggiungi nuovo annuncio** .

14. Immettere un titolo per l'annuncio, quindi scegliere il pulsante **Salva** .

     Si noti che il punto di interruzione viene raggiunto quando il nuovo elemento viene aggiunto all'elenco degli annunci personalizzati.

15. Premere il tasto **F5** per riprendere.

16. Nel riquadro di spostamento scegliere il collegamento **elenchi** , quindi scegliere il collegamento **annunci** .

17. Aggiungere un nuovo annuncio.

     Si noti che il ricevitore di eventi non viene attivato sul nuovo annuncio perché il ricevitore è configurato per rispondere solo agli eventi nell'istanza dell'elenco di annunci personalizzati, **TestAnnouncements**.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
