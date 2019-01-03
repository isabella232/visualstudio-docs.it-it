---
title: 'Procedura: Creare un ricevitore di eventi | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a9f18bb4399e52c6afbac9b20a7b16d04a39843
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861572"
---
# <a name="how-to-create-an-event-receiver"></a>Procedura: Creare un ricevitore di eventi
  Creando *ricevitori di eventi*, è possibile rispondere quando un utente interagisce con gli elementi di SharePoint, ad esempio elenchi o elementi di elenco. Ad esempio, il codice in un ricevitore di eventi può essere attivato quando un utente modifica il calendario o elimina un nome da un elenco di contatti. Seguendo questo argomento, è possibile informazioni su come aggiungere un ricevitore di eventi a un'istanza di elenco.

 Per completare questi passaggi, è necessario aver installato [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e le edizioni supportate di Windows e SharePoint. Poiché in questo esempio richiede un progetto SharePoint, è anche necessario avere completato la procedura nell'argomento [procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Aggiunta di un ricevitore di eventi
 Il progetto creato in [procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) include le colonne del sito personalizzato, un elenco personalizzato e un tipo di contenuto. Nella procedura seguente, si sarà espandere questo progetto aggiungendo un gestore di evento semplice (un ricevitore di eventi) a un'istanza di elenco per mostrare come gestire gli eventi che si verificano negli elementi di SharePoint, ad esempio gli elenchi.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Per aggiungere un ricevitore di eventi per l'istanza di elenco

1.  Aprire il progetto creato in [procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2.  Nelle **Esplora soluzioni**, scegliere il nodo di progetto SharePoint, chiamata ScriptHelpers **Clinic**.

3.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

4.  In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** elemento.

5.  Nel **modelli** riquadro, scegliere **ricevitore di eventi**, denominarlo **il nome TestEventReceiver1**e quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

6.  Nel **quale tipo di ricevitore di eventi da?** casella di riepilogo **eventi elementi elenco**.

7.  Nel **selezionare l'elemento deve essere l'origine dell'evento?** elenco, scegliere **i pazienti (Clinic\Patients)**.

8.  Nel **gestire gli eventi seguenti** , selezionare la casella di controllo accanto a **è stato aggiunto un elemento**e quindi scegliere il **fine** pulsante.

     Il file di codice per il nuovo ricevitore di eventi contiene un singolo metodo denominato `ItemAdded`. Nel passaggio successivo, si aggiungerà codice al metodo in modo che ogni contatto verrà denominato Scott Brown per impostazione predefinita.

9. Sostituire il `ItemAdded` metodo con il seguente codice e quindi scegliere il **F5** chiave:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Il codice viene eseguito e il sito verrà visualizzato nel browser web di SharePoint.

10. Nella barra Avvio veloce scegliere il **pazienti** collegamento e quindi scegliere il **Aggiungi nuovo elemento** collegamento.

     Viene aperto il modulo di immissione di nuovi elementi.

11. Immettere i dati nei campi e quindi scegliere il **salvare** pulsante.

     Dopo aver scelto il **salvare** pulsante, il **nome Patient** colonna Aggiorna automaticamente il nome Scott Brown.

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)