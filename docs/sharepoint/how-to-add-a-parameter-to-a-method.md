---
title: 'Procedura: aggiungere un parametro a un metodo | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6d0496d0fd6a347683d56630990e50af585520ba
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016718"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Procedura: aggiungere un parametro a un metodo
  Usare un parametro per passare informazioni al metodo o per restituire informazioni da un metodo. Tutti i metodi devono avere almeno un parametro. Per ulteriori informazioni sulla progettazione di un parametro per supportare il tipo di metodo che si desidera creare, vedere Progettazione di [un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quando si aggiunge un parametro a un metodo, Visual Studio aggiunge l'elemento Parameter al codice XML del file del modello nel progetto. Per ulteriori informazioni sugli attributi di un elemento Parameter, vedere [Parameter](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Per aggiungere un parametro a un metodo

1. Aggiungere un metodo a un'entità.

2. Sulla barra dei menu scegliere **Visualizza**  >  **altri**  >  **Dettagli metodo di integrazione applicativa dei dati**di Windows.

     Verrà visualizzata la finestra **Dettagli metodo BDC** . Per altre informazioni, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo del metodo, quindi espandere il nodo **parametri** .

4. Nell'elenco **Aggiungi parametri** scegliere **Crea parametro**.

     Un nuovo parametro viene visualizzato sotto il nodo **parametri** .

5. Nella barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

6. Nella finestra **Proprietà** impostare la proprietà **Name** su qualsiasi nome che abbia senso. Se, ad esempio, il metodo restituirà Customers, è possibile assegnare il nome **GetCustomers**al metodo.

7. Nella finestra **Dettagli metodo di integrazione applicativa dei dati** aprire l'elenco visualizzato per la direzione del parametro, quindi scegliere **in**, **InOut**, **out**o **return**.

     Per ulteriori informazioni sulla direzione scelta per il metodo del tipo che si sta creando, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Modificare il descrittore di tipo del parametro. Per altre informazioni, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
