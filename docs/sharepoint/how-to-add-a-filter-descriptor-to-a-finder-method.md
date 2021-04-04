---
title: 'Procedura: aggiungere un descrittore di filtro a un metodo Finder | Microsoft Docs'
description: Informazioni su come aggiungere un descrittore di filtro a un metodo di ricerca usando la finestra Dettagli metodo di integrazione applicativa dei dati in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47fcc7e388f240d8b9636a733df4b6b8767f0df4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218009"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Procedura: aggiungere un descrittore di filtro a un metodo Finder
  I descrittori di filtro consentono agli utenti del modello di passare i valori ai metodi prima dell'esecuzione. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

 Uno scenario comune è che gli utenti di SharePoint vogliono recuperare le istanze di un tipo di contenuto esterno che soddisfano alcuni criteri. È possibile supportare questo scenario aggiungendo un descrittore di filtro a un metodo Finder.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Per aggiungere un descrittore di filtro a un metodo Finder

1. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo di un metodo Finder, espandere il nodo **parametri** , quindi aggiungere un parametro di input. Per altre informazioni, vedere [procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. Nella finestra **Dettagli metodo** scegliere il descrittore di tipo del parametro.

3. Nella barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

4. Nella finestra **Proprietà** impostare la proprietà **nome tipo** su un tipo di dati appropriato per il filtro.

     Ad esempio, un filtro può utilizzare una data di ordine per limitare il numero di ordini di vendita restituiti dal metodo. Per supportare tale filtro, la proprietà **nome tipo** del descrittore di tipo deve essere impostata su **System. DateTime**.

5. Nella finestra **Dettagli metodo** espandere il nodo **descrittori di filtro** .

6. Nell'elenco **Aggiungi descrittori di filtro** scegliere **Crea descrittore filtro**.

     Un nuovo descrittore di filtro viene visualizzato sotto il nodo **descrittori di filtro** .

7. Nella barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

8. Nella finestra **Proprietà** scegliere la proprietà **tipo** .

9. Nell'elenco visualizzato per la proprietà **Type** scegliere il modello di filtro desiderato.

     Ad esempio, per creare un filtro che usi una data di ordine per limitare il numero di ordini di vendita restituiti in un metodo di ricerca, scegliere **confronto**. Un filtro di confronto garantisce che un metodo di ricerca restituisca solo le istanze che soddisfano una condizione specifica. Per ulteriori informazioni su ogni modello di filtro, vedere [tipi di filtri supportati da integrazione applicativa](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))dei dati.

10. Nella finestra **Proprietà** scegliere la proprietà **descrittori di tipo associato** .

11. Nell'elenco visualizzato per la proprietà **descrittori di tipo associato** scegliere il descrittore di tipo creato in precedenza in questa procedura. In questo modo il filtro viene correlato al parametro di input del metodo Finder.

12. Aggiungere il codice al metodo Finder che restituisce i dati. È possibile usare il parametro di input come condizione in una query SELECT.

     Nell'esempio seguente vengono restituiti gli ordini di vendita con la data dell'ordine specificata.

    > [!NOTE]
    > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet11":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet11":::

## <a name="see-also"></a>Vedi anche
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
