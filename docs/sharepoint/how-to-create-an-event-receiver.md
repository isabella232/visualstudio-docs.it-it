---
title: 'Procedura: Creare un ricevitore di eventi | Microsoft Docs'
description: Creare un ricevitore di eventi in modo che sia possibile rispondere quando un utente interagisce con SharePoint elementi, ad esempio elenchi o elementi di elenco.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 66b62a619b64534f56039e6213b01d4d12bb941a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636924"
---
# <a name="how-to-create-an-event-receiver"></a>Procedura: Creare un ricevitore di eventi
  Creando *ricevitori di eventi*, è possibile rispondere quando un utente interagisce con SharePoint elementi, ad esempio elenchi o elementi di elenco. Ad esempio, il codice in un ricevitore di eventi può essere attivato quando un utente modifica il calendario o elimina un nome da un elenco contatti. Seguendo questo argomento, è possibile apprendere come aggiungere un ricevitore di eventi a un'istanza di elenco.

 Per completare questi passaggi, è necessario aver installato [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e supportato le edizioni di Windows e SharePoint. Poiché questo esempio richiede un progetto SharePoint, è necessario aver completato anche la procedura descritta nell'argomento Procedura dettagliata: Creare una colonna [del sito,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)un tipo di contenuto ed un elenco per SharePoint .

## <a name="adding-an-event-receiver"></a>Aggiunta di un ricevitore di eventi
 Il progetto creato in Procedura dettagliata: Creare una colonna del [sito,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) un tipo di contenuto ed un elenco per SharePoint include colonne del sito personalizzate, un elenco personalizzato e un tipo di contenuto. Nella procedura seguente si espanderà questo progetto aggiungendo un semplice gestore eventi (un ricevitore di eventi) a un'istanza di elenco per mostrare come gestire gli eventi che si verificano SharePoint elementi, ad esempio gli elenchi.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Per aggiungere un ricevitore di eventi all'istanza di elenco

1. Aprire il progetto creato in Procedura [dettagliata: Creare una colonna](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)del sito, un tipo di contenuto ed un elenco per SharePoint .

2. In **Esplora soluzioni** scegliere il nodo SharePoint progetto, denominato **Clinic**.

3. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

4. In **Visual C#** o **Visual Basic** espandere  il SharePoint e quindi scegliere **l'elemento 2010.**

5. Nel riquadro **Modelli** scegliere **Ricevitore di eventi,** assegnare il nome **TestEventReceiver1** e quindi scegliere **il pulsante OK.**

     Verrà **visualizzata SharePoint personalizzazione** guidata.

6. **Nell'elenco What type of event receiver do you want?** (Che tipo di ricevitore di eventi si vuole? scegliere **List Item Events**).

7. **Nell'elenco Quale elemento deve essere l'origine evento?** scegliere Patients **(Clinic\Patients)**.

8. **Nell'elenco Gestisci gli eventi seguenti** selezionare la casella di controllo accanto a È **stato** aggiunto un elemento e quindi scegliere il **pulsante** Fine.

     Il file di codice per il nuovo ricevitore di eventi contiene un singolo metodo denominato `ItemAdded` . Nel passaggio successivo si aggiungerà il codice a questo metodo in modo che ogni contatto sia denominato Scott Brown per impostazione predefinita.

9. Sostituire il `ItemAdded` metodo esistente con il codice seguente e quindi premere **F5:**

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb" id="Snippet1":::

     Il codice viene eseguito e il SharePoint visualizzato nel Web browser.

10. Sulla barra Avvio rapido scegliere il collegamento **Patients** e quindi scegliere il **collegamento Aggiungi nuovo** elemento.

     Verrà aperto il modulo di immissione per i nuovi elementi.

11. Immettere i dati nei campi e quindi scegliere il **pulsante** Salva.

     Dopo aver scelto il **pulsante Salva,** la colonna **Nome paziente** viene aggiornata automaticamente con il nome Scott Brown.

## <a name="see-also"></a>Vedi anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)