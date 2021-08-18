---
title: 'Procedura: Definire il descrittore di tipo di un oggetto Parameter | Microsoft Docs'
description: Informazioni su come definire il descrittore di tipo di un parametro per un metodo nel modello BDC (Business Data Connectivity).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ae1570010fc71d6edf56cdf9090f371c218a322a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148896"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Procedura: Definire il descrittore di tipo di un parametro
  Un descrittore di tipo contiene proprietà che descrivono il tipo di dati di un parametro. Può definire un campo, un'entità o una raccolta di entità. Per altre informazioni, vedere [TypeDescriptor.](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Definire il descrittore di tipo di un parametro

1. Nella finestra **Dettagli metodo BDC** scegliere il descrittore del tipo del parametro.

2. Sulla barra dei menu scegliere **Visualizza**, **Finestra Proprietà**.

3. Nella finestra **Proprietà** impostare le proprietà del descrittore di tipo.

     Le procedure seguenti descrivono come definire un descrittore di tipo come un campo, un'entità o una raccolta di entità.

### <a name="to-define-a-field"></a>Per definire un campo

1. Nella finestra **Proprietà** impostare la proprietà **Name** del descrittore di tipi sul nome di un campo nel tipo che rappresenta l'entità , ad esempio **FirstName**.

2. Nell'elenco accanto alla **proprietà TypeName** scegliere il tipo di dati appropriato, ad esempio **Int32**.

     Per informazioni su altri parametri facoltativi, vedere [TypeDescriptor.](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))

### <a name="to-define-an-entity"></a>Per definire un'entità

1. Nella finestra **Proprietà** impostare la proprietà **Name** su un nome che descriva l'entità, ad esempio **Contact.**

2. Impostare la **proprietà TypeName** sul nome completo del tipo che rappresenta l'entità. Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.

    - Per una classe nel progetto, scegliere la freccia giù accanto alla proprietà **TypeName,** scegliere la scheda **Project** corrente nella finestra di dialogo visualizzata e quindi scegliere la classe nel progetto.

         Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB. L'esempio seguente imposta il valore **della proprietà TypeName** su una classe nel progetto.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.

         Nell'esempio seguente il valore della **proprietà TypeName** viene impostato su un tipo definito in un assembly a cui si fa riferimento nella soluzione.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include lo spazio dei nomi e il nome del tipo.

         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su un tipo nel modello a oggetti BDC.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. Nella finestra **BDC Method Details (Dettagli metodo BDC)** aprire l'elenco visualizzato per il descrittore di tipo e quindi scegliere **Edit (Modifica).**

     Verrà **visualizzata la finestra BDC Explorer.**

4. In **BDC Explorer aprire** il menu di scelta rapida del descrittore di tipi e quindi scegliere **Aggiungi descrittore di tipo.**

     Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di entità. Configurare il descrittore di tipo come un campo.

5. Ripetere il passaggio 4 per aggiungere un descrittore di tipo figlio per ogni campo dell'entità.

### <a name="to-define-a-collection-of-entities"></a>Per definire una raccolta di entità

1. Nella finestra **BDC Method Details (Dettagli metodo BDC)** scegliere il descrittore del tipo del parametro desiderato.

2. Sulla barra dei menu scegliere **Visualizza**, **Finestra Proprietà**.

3. Nella finestra **Proprietà** impostare la **proprietà Name** su un nome che descriva l'entità, ad esempio **Contacts.**

4. Impostare la **proprietà IsCollection** su **True.** Ciò indica che il descrittore di tipo è una raccolta di entità.

5. Impostare la **proprietà TypeName** su una stringa che contiene un riferimento all'interfaccia e il nome completo del tipo <xref:System.Collections.Generic.IEnumerable%601> che rappresenta l'entità. Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.

   - Per una classe nel progetto, scegliere la freccia giù accanto alla proprietà **TypeName,** scegliere la scheda **Project** corrente nella finestra di dialogo visualizzata e quindi scegliere la classe nel progetto.

      Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB.

      L'esempio seguente imposta il valore **della proprietà TypeName** su una raccolta di classi nel progetto.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.BdcModel1.Contact, BdcModel1]'

   - Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.

      Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una raccolta di tipi in un assembly a cui si fa riferimento nella soluzione.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]'

   - Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include solo lo spazio dei nomi e il nome del tipo.

      Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una raccolta di tipi definiti nel modello a oggetti BDC.

      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'

6. Nella finestra **BDC Method Details (Dettagli metodo BDC)** aprire l'elenco visualizzato per il descrittore di tipo e quindi scegliere **Edit (Modifica).**

    Verrà **visualizzata la finestra BDC Explorer.**

7. In **BDC Explorer aprire** il menu di scelta rapida del descrittore di tipi e quindi scegliere **Aggiungi descrittore di tipo.**

    Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di raccolta. Configurare il descrittore di tipo come un'entità.

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
