---
title: 'Procedura: Aggiungere un parametro a un metodo | Microsoft Docs'
description: Informazioni su come aggiungere un parametro a un metodo BDC (Business Data Connectivity), che consente di passare informazioni nel metodo o di restituire informazioni dal metodo .
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 1023044ebcd765a411aa6edfb358f5f6191ed7028d5e8559fe020e27f7d57ade
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121332339"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Procedura: Aggiungere un parametro a un metodo
  Usare un parametro per passare informazioni nel metodo o per restituire informazioni da un metodo. Tutti i metodi devono avere almeno un parametro. Per altre informazioni su come progettare un parametro per supportare il tipo di metodo che si desidera creare, vedere Progettazione di un modello di [connettività dei dati di business.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Quando si aggiunge un parametro a un metodo, Visual Studio l'elemento Parameter al codice XML del file di modello nel progetto. Per altre informazioni sugli attributi di un elemento Parameter, vedere [Parameter](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Per aggiungere un parametro a un metodo

1. Aggiungere un metodo a un'entità.

2. Sulla barra dei menu scegliere **Visualizza altri dettagli**  >  **Windows**  >  **metodo BDC**.

     Verrà **visualizzata la finestra BDC Method Details (Dettagli metodo BDC).** Per altre informazioni, vedere [BDC Model Design Tools Overview](../sharepoint/bdc-model-design-tools-overview.md).

3. Nella finestra **Dettagli metodo BDC** espandere il nodo del metodo e quindi espandere **il nodo** Parametri .

4. **Nell'elenco Aggiungi parametro** scegliere Crea **parametro**.

     Sotto il nodo Parametri viene visualizzato **un nuovo** parametro.

5. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà.**

6. Nella finestra **Proprietà** impostare la **proprietà Name** su qualsiasi nome sensato. Ad esempio, se il metodo restituirà clienti, è possibile assegnare al metodo il nome **GetCustomers**.

7. Nella finestra **BDC Method Details (Dettagli metodo BDC)** aprire l'elenco visualizzato per la direzione del parametro e quindi scegliere **In**, **InOut**, **Out** o **Return**.

     Per altre informazioni sulla direzione da scegliere per il metodo del tipo che si sta creando, vedere Progettare un modello [di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

8. Modificare il descrittore di tipo del parametro. Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
