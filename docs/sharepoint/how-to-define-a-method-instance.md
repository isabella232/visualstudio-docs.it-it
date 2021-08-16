---
title: "Procedura: Definire un'istanza del metodo | Microsoft Docs"
description: Informazioni su come definire un'istanza del metodo per un metodo nel modello BDC (Business Data Connectivity).
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c75c41a68c4c6ba2cebf0b7d16bbf5b5ff064aee8f25d4c2962c9574b5c78ef1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409618"
---
# <a name="how-to-define-a-method-instance"></a>Procedura: Definire un'istanza del metodo
  È necessario definire almeno un'istanza del metodo per ogni metodo nel modello.

 Aggiungere un'istanza del metodo usando la **finestra Dettagli metodo BDC.** Quando si aggiunge l'istanza del metodo, Visual Studio aggiunge un elemento al `<MethodInstance>` codice XML del file di modello nel progetto. Per altre informazioni sugli attributi di un `<MethodInstance>` elemento, vedere [MethodInstance.](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))

### <a name="to-define-a-method-instance"></a>Per definire un'istanza del metodo

1. Nella finestra **Dettagli metodo BDC** espandere il nodo di un metodo e quindi espandere il **nodo** Istanze .

2. **Nell'elenco Aggiungi un'istanza di metodo** scegliere Crea istanza **finder**.

     Sotto il nodo Istanze viene visualizzata una **nuova istanza del** metodo.

3. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà.**

4. Nella finestra **Proprietà** impostare le proprietà dell'istanza del metodo. Per altre informazioni su ogni proprietà, vedere [MethodInstance.](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
