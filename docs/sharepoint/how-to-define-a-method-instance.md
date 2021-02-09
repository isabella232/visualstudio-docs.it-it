---
title: "Procedura: definire un'istanza di metodo | Microsoft Docs"
description: Informazioni su come definire un'istanza del metodo per un metodo nel modello di integrazione applicativa dei dati (Business Data Connectivity).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 055193123f99825027238166d762ce54b288d716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885664"
---
# <a name="how-to-define-a-method-instance"></a>Procedura: definire un'istanza di metodo
  È necessario definire almeno un'istanza del metodo per ogni metodo nel modello.

 Aggiungere un'istanza del metodo utilizzando la finestra **Dettagli metodo di integrazione applicativa dei dati** . Quando si aggiunge l'istanza del metodo, Visual Studio aggiunge un `<MethodInstance>` elemento al codice XML del file del modello nel progetto. Per ulteriori informazioni sugli attributi di un `<MethodInstance>` elemento, vedere [oggetto MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Per definire un'istanza di metodo

1. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo di un metodo, quindi espandere il nodo **istanze** .

2. Nell'elenco **Aggiungi istanza metodo** scegliere **Crea istanza Finder**.

     Una nuova istanza del metodo viene visualizzata sotto il nodo **istanze** .

3. Nella barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

4. Nella finestra **Proprietà** impostare le proprietà dell'istanza del metodo. Per ulteriori informazioni su ogni proprietà, vedere [oggetto MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
