---
title: "Procedura: aggiungere un'entità a un modello | Microsoft Docs"
description: Aggiungere un'entità a un modello aggiungendo un controllo entità dalla casella degli strumenti di Visual Studio nella finestra di progettazione di integrazione applicativa dei dati.
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
ms.workload:
- office
ms.openlocfilehash: 94d34e6a623438cd0e2d63d74ee2321841a0582a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216774"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procedura: aggiungere un'entità a un modello
  Per creare un'entità, aggiungere un controllo entità dalla **casella degli strumenti** di Visual Studio nella finestra di progettazione di integrazione applicativa dei dati.

### <a name="to-add-an-entity-to-the-model"></a>Per aggiungere un'entità al modello

1. Creare un progetto BDC o aprire un progetto BDC esistente. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

2. Nella **casella degli strumenti**, dal gruppo **BusinessDataCatalog** , aggiungere un controllo **entità** nella finestra di progettazione.

     La nuova entità verrà visualizzata nella finestra di progettazione. Visual Studio aggiunge un `<Entity>` elemento all'XML del file del modello di integrazione applicativa dei dati nel progetto. Per ulteriori informazioni sugli attributi di un elemento entità, vedere [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. Nella finestra di progettazione aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **identificatore**.

     Viene visualizzato un nuovo identificatore nell'entità.

    > [!NOTE]
    > È possibile modificare il nome dell'entità e l'identificatore nella finestra **Proprietà** .

4. Definire i campi dell'entità in una classe. È possibile aggiungere una nuova classe al progetto o usare una classe esistente creata usando altri strumenti, ad esempio la Object Relational Designer (O/R Designer). Nell'esempio seguente viene illustrata una classe di entità denominata Contact.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>Vedi anche
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
