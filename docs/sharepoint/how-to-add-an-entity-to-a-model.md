---
title: "Procedura: aggiungere un'entità a un modello | Microsoft Docs"
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b80f39494b98014a75d4265f228906be2ff45188
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016676"
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

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
