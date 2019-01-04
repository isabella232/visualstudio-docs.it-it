---
title: "Procedura: Aggiungere un'entità a un modello | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 347728ac4f096359f06ca7823adfcd1b25ff527a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964034"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procedura: Aggiungere un'entità a un modello
  Per creare un'entità, aggiungere un controllo dell'entità da Visual Studio **casella degli strumenti** nella finestra di progettazione integrazione applicativa dei dati (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Per aggiungere un'entità al modello  
  
1.  Creare un progetto di integrazione applicativa dei dati o aprire un progetto di integrazione applicativa dei dati esistente. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Nel **casella degli strumenti**, dal **BusinessDataCatalog** gruppo, aggiungere un' **entità** controllo nella finestra di progettazione.  
  
     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un `<Entity>` elemento al codice XML del file di modello di integrazione applicativa dei dati nel progetto. Per altre informazioni sugli attributi di un elemento di entità, vedere [entità](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Nella finestra di progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Add**, quindi scegliere **identificatore**.  
  
     Viene visualizzato un nuovo identificatore dell'entità.  
  
    > [!NOTE]  
    >  È possibile modificare il nome dell'entità e l'identificatore di **proprietà** finestra.  
  
4.  Definire i campi dell'entità in una classe. È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata tramite altri strumenti, ad esempio il Object Relational Designer (O/R Designer). Nell'esempio seguente viene illustrata una classe di entità denominata Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)  
