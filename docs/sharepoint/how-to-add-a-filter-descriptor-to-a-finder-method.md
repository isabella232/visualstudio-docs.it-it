---
title: 'Procedura: Aggiungere un descrittore di filtro a un metodo Finder | Microsoft Docs'
description: Informazioni su come aggiungere un descrittore di filtro a un metodo Finder usando la finestra Dettagli metodo BDC in Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 62d05e77d808744da1fbb8d639e762f55103b7d4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027136"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Procedura: Aggiungere un descrittore di filtro a un metodo Finder
  I descrittori di filtro consentono ai consumer del modello di passare valori ai metodi prima dell'esecuzione. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Uno scenario comune è che gli utenti SharePoint recuperare istanze di un tipo di contenuto esterno che soddisfano alcuni criteri. È possibile supportare questo scenario aggiungendo un descrittore di filtro a un metodo Finder.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Per aggiungere un descrittore di filtro a un metodo Finder

1. Nella finestra **Dettagli metodo BDC** espandere il nodo di un metodo Finder, espandere il **nodo Parametri** e quindi aggiungere un parametro di input. Per altre informazioni, vedere [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. Nella finestra **Dettagli metodo** scegliere il descrittore del tipo del parametro.

3. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

4. Nella finestra **Proprietà** impostare la proprietà **Nome** tipo su un tipo di dati appropriato per il filtro.

     Ad esempio, un filtro potrebbe usare una data dell'ordine per limitare il numero di ordini di vendita restituiti dal metodo . Per supportare tale filtro, la **proprietà Type Name** del descrittore di tipo deve essere impostata su **System.DateTime**.

5. Nella finestra **Dettagli metodo** espandere il **nodo Descrittori di** filtro.

6. **Nell'elenco Add a Filter Descriptor (Aggiungi** descrittore filtro) scegliere Create Filter **Descriptor (Crea descrittore filtro).**

     Sotto il nodo Descrittori di filtro viene visualizzato un nuovo **descrittore di** filtro.

7. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

8. Nella finestra **Proprietà** scegliere la **proprietà Tipo.**

9. Nell'elenco visualizzato per la **proprietà Tipo** scegliere il criterio di filtro desiderato.

     Ad esempio, per creare un filtro che usa una data dell'ordine per limitare il numero di ordini di vendita restituiti in un metodo Finder, scegliere **Confronto**. Un filtro Di confronto garantisce che un metodo finder restituisca solo istanze che soddisfano una condizione specifica. Per altre informazioni su ogni criterio di filtro, vedere [Tipi di filtri supportati dal BDC.](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))

10. Nella finestra **Proprietà** scegliere la **proprietà Descrittori di tipi** associati.

11. Nell'elenco visualizzato per la **proprietà Descrittori di** tipi associati scegliere il descrittore di tipo creato in precedenza in questa procedura. Il filtro è correlato al parametro di input del metodo Finder.

12. Aggiungere il codice al metodo Finder che restituisce i dati. È possibile usare il parametro di input come condizione in una query di selezione.

     Nell'esempio seguente vengono restituiti gli ordini di vendita con la data dell'ordine specificata.

    > [!NOTE]
    > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet11":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet11":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrazione dei dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
