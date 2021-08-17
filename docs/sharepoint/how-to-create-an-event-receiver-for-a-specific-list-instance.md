---
title: "Procedura: Creare un ricevitore di eventi per un'istanza di elenco | Microsoft Docs"
titleSuffix: ''
description: Creare un ricevitore di eventi per un'istanza di elenco specifica. Un ricevitore di eventi dell'istanza di elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 815cb4a46141ddc5f6e85fefe4ff71a53cd473e958ffaa5c2779e99355aca6cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228558"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Procedura: Creare un ricevitore di eventi per un'istanza di elenco specifica
  Un ricevitore di eventi dell'istanza di elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco. Sebbene il modello del ricevitore di eventi non abiliti la destinazione di un'istanza di elenco specifica, è possibile modificare un ricevitore di eventi con ambito definizione di elenco per rispondere agli eventi in un'istanza di elenco specifica.

 Per impostare come destinazione un'istanza di elenco specifica, nel *Elements.xml* per il ricevitore dell'evento sostituire con e aggiungere `ListTemplateId` l'URL `ListUrl` dell'istanza dell'elenco.

## <a name="create-a-list-instance-event-receiver"></a>Creare un ricevitore di eventi dell'istanza di elenco
 La procedura seguente illustra come modificare un ricevitore di eventi dell'elemento elenco in modo che risponda solo agli eventi che si verificano in un'istanza personalizzata di announcements-list.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Per modificare un ricevitore di eventi in modo che risponda a un'istanza di elenco specifica

1. In un browser aprire il sito di SharePoint.

2. Nel riquadro di spostamento selezionare **il collegamento** Elenchi.

3. Nella pagina **Tutto il contenuto del** sito scegliere il **collegamento** Crea.

4. Nella finestra **di** dialogo Crea scegliere il tipo **Annunci,** assegnare all'annuncio il nome **TestAnnouncements** e quindi scegliere **il pulsante** Crea.

5. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto ricevitore di eventi.

6. **Nell'elenco What type of event receiver do you want?** (Che tipo di ricevitore di eventi si vuole? scegliere **List Item Events**).

    > [!NOTE]
    > È anche possibile selezionare qualsiasi altro tipo di ricevitore di eventi che ha come ambito una definizione di elenco, ad esempio Elenca eventi di posta **elettronica** o Elenca eventi del **flusso di lavoro**.

7. **Nell'elenco Quale elemento deve essere l'origine evento?** scegliere **Annunci**.

8. **Nell'elenco Gestisci gli eventi seguenti** selezionare la casella di controllo È **in** corso l'aggiunta di un elemento e quindi scegliere **il pulsante** Fine.

9. In **Esplora soluzioni**, in EventReceiver1 aprire *Elements.xml*.

     Il ricevitore di eventi fa riferimento attualmente alla definizione di elenco degli annunci tramite la riga seguente:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Modificare questa riga nel testo seguente:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Questo indica al ricevitore di eventi di rispondere solo agli eventi che si verificano nel nuovo elenco di annunci **TestAnnouncements** appena creato. È possibile modificare `ListURL` l'attributo per fare riferimento a qualsiasi istanza di elenco nel server SharePoint server.

10. Aprire il file di codice per il ricevitore dell'evento e inserire un punto di interruzione nel metodo ItemAdding.

11. Premere **F5 per** compilare ed eseguire la soluzione.

12. In SharePoint scegliere il **collegamento TestAnnouncements nel** riquadro di spostamento.

13. Scegliere il **collegamento Aggiungi nuovo** annuncio.

14. Immettere un titolo per l'annuncio e quindi scegliere **il pulsante** Salva.

     Si noti che il punto di interruzione viene raggiunto quando il nuovo elemento viene aggiunto all'elenco di annunci personalizzati.

15. Premere **F5** per riprendere.

16. Nel riquadro di spostamento scegliere il **collegamento Elenchi** e quindi scegliere il **collegamento Annunci.**

17. Aggiungere un nuovo annuncio.

     Si noti che il ricevitore di eventi non viene attivato nel nuovo annuncio perché il ricevitore è configurato per rispondere solo agli eventi nell'istanza dell'elenco di annunci personalizzato, **TestAnnouncements**.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
