---
title: 'Procedura: creare un ricevitore di eventi | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 26d8c9f433fad051716b6ebd37e3d1f3b3f9f4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016921"
---
# <a name="how-to-create-an-event-receiver"></a>Procedura: creare un ricevitore di eventi
  Creando i *ricevitori di eventi*, è possibile rispondere quando un utente interagisce con gli elementi di SharePoint, ad esempio elenchi o elementi di elenco. Ad esempio, il codice in un ricevitore di eventi può essere attivato quando un utente modifica il calendario o Elimina un nome da un elenco di contatti. Seguendo questo argomento, è possibile apprendere come aggiungere un ricevitore di eventi a un'istanza di elenco.

 Per completare questi passaggi, è necessario aver installato [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e supportato le edizioni di Windows e SharePoint. Poiché questo esempio richiede un progetto SharePoint, è inoltre necessario aver completato la procedura descritta nell'argomento [procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Aggiunta di un ricevitore di eventi
 Il progetto creato in [procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) include colonne del sito personalizzate, un elenco personalizzato e un tipo di contenuto. Nella procedura seguente si espanderà il progetto aggiungendo un semplice gestore eventi (un ricevitore di eventi) a un'istanza di elenco per illustrare come gestire gli eventi che si verificano negli elementi di SharePoint, ad esempio gli elenchi.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Per aggiungere un ricevitore di eventi all'istanza dell'elenco

1. Aprire il progetto creato in [procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. In **Esplora soluzioni**scegliere il nodo del progetto SharePoint, denominato **Clinic**.

3. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

4. In **Visual C#** o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere l'elemento **2010** .

5. Nel riquadro **modelli** scegliere ricevitore di **eventi**, denominarlo **TestEventReceiver1**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

6. Nell'elenco **specificare il tipo di ricevitore di eventi desiderato** scegliere **eventi elemento elenco**.

7. Nell'elenco specificare l' **elemento che deve essere l'origine evento** scegliere **patients (Clinic\Patients)**.

8. Nell'elenco **Gestisci gli eventi seguenti** selezionare la casella di controllo accanto a **un elemento aggiunto**, quindi scegliere il pulsante **fine** .

     Il file di codice per il nuovo ricevitore di eventi contiene un solo metodo denominato `ItemAdded` . Nel passaggio successivo si aggiungerà codice a questo metodo in modo che ogni contatto verrà denominato Scott Brown per impostazione predefinita.

9. Sostituire il `ItemAdded` metodo esistente con il codice seguente, quindi premere il tasto **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Viene eseguito il codice e il sito di SharePoint viene visualizzato nel Web browser.

10. Sulla barra QuickLaunch scegliere il collegamento **patients** , quindi scegliere il collegamento **Aggiungi nuovo elemento** .

     Viene aperto il modulo di immissione per i nuovi elementi.

11. Immettere i dati nei campi, quindi scegliere il pulsante **Salva** .

     Dopo aver scelto il pulsante **Salva** , la colonna **nome del paziente** viene aggiornata automaticamente con il nome Scott Brown.

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)