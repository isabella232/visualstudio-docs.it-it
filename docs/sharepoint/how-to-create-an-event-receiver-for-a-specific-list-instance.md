---
title: "Procedura: Creare un ricevitore di eventi per un'istanza di elenco specifica | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 615b9bc4974a0483dec5e9c39727ebae50039a1f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596529"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Procedura: Creare un ricevitore di eventi per un'istanza di elenco specifico
  Un ricevitore di eventi di istanza di elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco. Anche se il modello del ricevitore di eventi non abilita l'impostazione della destinazione di un'istanza di elenco specifico, è possibile modificare un ricevitore di eventi con ambito di una definizione di elenco per rispondere agli eventi in un'istanza di elenco specifico.

 Come destinazione un'istanza di elenco specifico, per il *Elements* per il ricevitore di eventi, sostituire `ListTemplateId` con `ListUrl` e aggiungere l'URL dell'istanza di elenco.

## <a name="create-a-list-instance-event-receiver"></a>Creare un ricevitore di eventi di istanza di elenco
 La procedura seguente illustra come modificare un ricevitore di eventi elemento elenco in modo che risponda solo gli eventi che si verificano in un'istanza di elenco di annunci personalizzati.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Per modificare un ricevitore di eventi per rispondere a un'istanza di elenco specifico

1.  In un browser aprire il sito di SharePoint.

2.  Nel riquadro di spostamento **Elenca** collegamento.

3.  Nel **All Site Content** pagina, scegliere il **crea** collegamento.

4.  Nel **Create** finestra di dialogo scegliere la **annunci** digitare, denominare l'annuncio **TestAnnouncements**e quindi scegliere il **crea**pulsante.

5.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di ricevitore di eventi.

6.  Nel **quale tipo di ricevitore di eventi da?** casella di riepilogo **eventi elementi elenco**.

    > [!NOTE]
    >  È anche possibile selezionare qualsiasi altro tipo di ricevitore di eventi che definisce l'ambito di una definizione di elenco, ad esempio, **elenco eventi di posta elettronica** oppure **elenco eventi di flusso di lavoro**.

7.  Nel **selezionare l'elemento deve essere l'origine dell'evento?** casella di riepilogo **annunci**.

8.  Nel **gestire gli eventi seguenti** elenco, selezionare la **viene aggiunto un elemento** casella di controllo e quindi scegliere il **fine** pulsante.

9. Nelle **Esplora soluzioni**, sotto EventReceiver1 aprire *Elements*.

     Il ricevitore di eventi fa riferimento attualmente alla definizione di elenco degli annunci tramite la riga seguente:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Modificare questa riga nel testo seguente:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Questa azione apre il ricevitore di eventi per rispondere solo a eventi che si verificano nel nuovo **TestAnnouncements** elenco di annunci appena creato. È possibile modificare il `ListURL` attributo per fare riferimento a qualsiasi istanza di elenco nel server SharePoint.

10. Aprire il file di codice per il ricevitore di eventi e inserire un punto di interruzione nel metodo ItemAdding.

11. Scegliere il **F5** chiave per compilare ed eseguire la soluzione.

12. In SharePoint, scegliere il **TestAnnouncements** collegamento nel riquadro di spostamento.

13. Scegliere il **Aggiungi nuovo annuncio** collegamento.

14. Immettere un titolo per l'annuncio e quindi scegliere il **salvare** pulsante.

     Si noti che il punto di interruzione viene raggiunto quando il nuovo elemento viene aggiunto all'elenco degli annunci personalizzati.

15. Scegliere il **F5** tasto per continuare.

16. Nel riquadro di spostamento, scegliere il **sono elencati** collegamento e quindi scegliere il **annunci** collegamento.

17. Aggiungere un nuovo annuncio.

     Si noti che il ricevitore di eventi non attivare il nuovo annuncio perché il destinatario è configurato per rispondere solo agli eventi nell'istanza di elenco di annuncio personalizzato, **TestAnnouncements**.

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
