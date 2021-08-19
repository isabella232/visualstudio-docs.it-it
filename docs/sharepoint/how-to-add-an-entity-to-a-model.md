---
title: "Procedura: Aggiungere un'entità a un modello | Microsoft Docs"
description: Aggiungere un'entità a un modello aggiungendo un controllo entità dalla casella degli strumenti Visual Studio alla finestra di progettazione del servizio Integrazione applicativa dei dati (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7905b4b3686c10ad9c6ac019253c71f94305f0b8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093190"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procedura: Aggiungere un'entità a un modello
  Per creare un'entità, aggiungere un controllo entità dalla casella degli strumenti Visual Studio **alla** finestra di progettazione di Business Data Connectivity (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Per aggiungere un'entità al modello

1. Creare un progetto BDC o aprire un progetto BDC esistente. Per altre informazioni, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

2. Nella casella **degli** strumenti aggiungere un controllo Entità  nella finestra di progettazione dal gruppo **BusinessDataCatalog** .

     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un `<Entity>` elemento al codice XML del file di modello BDC nel progetto. Per altre informazioni sugli attributi di un elemento Entity, vedere [Entity.](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14))

3. Nella finestra di progettazione aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi** e quindi scegliere **Identificatore.**

     Nell'entità viene visualizzato un nuovo identificatore.

    > [!NOTE]
    > È possibile modificare il nome dell'entità e l'identificatore nella **finestra** Proprietà.

4. Definire i campi dell'entità in una classe. È possibile aggiungere una nuova classe al progetto o usare una classe esistente creata usando altri strumenti, ad esempio Object Relational Designer (O/R Designer). L'esempio seguente mostra una classe di entità denominata Contact.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
