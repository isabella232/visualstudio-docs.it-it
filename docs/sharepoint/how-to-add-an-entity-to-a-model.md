---
title: "Procedura: aggiungere un'entità a un modello | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec34a6f93625fdb2cb8a1e5fcc5fb5c95d17653b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procedura: aggiungere un'entità al modello
  Per creare un'entità, aggiungere un controllo di entità da Visual Studio **della casella degli strumenti** nella finestra di progettazione (Applicativa dei dati).  
  
### <a name="to-add-an-entity-to-the-model"></a>Per aggiungere un'entità al modello  
  
1.  Creare un progetto di integrazione applicativa dei dati o aprire un progetto di integrazione applicativa dei dati esistente. Per ulteriori informazioni, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Nel **della casella degli strumenti**, dal **BusinessDataCatalog** gruppo, aggiungere un **entità** controllo nella finestra di progettazione.  
  
     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un `<Entity>` elemento al codice XML del file di modello di integrazione applicativa dei dati nel progetto. Per ulteriori informazioni sugli attributi di un elemento di entità, vedere [entità](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Nella finestra di progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **identificatore**.  
  
     Verrà visualizzato un nuovo identificatore nell'entità.  
  
    > [!NOTE]  
    >  È possibile modificare il nome dell'entità e l'identificatore nel **proprietà** finestra.  
  
4.  Definire i campi dell'entità in una classe. È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata utilizzando altri strumenti, ad esempio il Object Relational Designer (O/R Designer). Nell'esempio seguente viene illustrata una classe di entità denominata contatto.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  