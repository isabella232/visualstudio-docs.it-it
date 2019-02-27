---
title: 'Procedura: Definire il descrittore di tipo di parametro | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f28de400b417011b127b76c8813024f9721cc375
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843163"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Procedura: Definire il descrittore di tipo di parametro
  Un descrittore di tipo contiene proprietà che descrivono il tipo di dati di un parametro. Può definire un campo, un'entità o una raccolta di entità. Per altre informazioni, vedere [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Definire il descrittore di tipo di un parametro

1.  Nel **Dettagli metodo BDC** finestra, scegliere il descrittore di tipo del parametro.

2.  Nella barra dei menu, scegliere **View**, **finestra proprietà**.

3.  Nel **proprietà** finestra, impostare le proprietà del descrittore del tipo.

     Le procedure seguenti descrivono come definire un descrittore di tipo come un campo, un'entità o una raccolta di entità.

### <a name="to-define-a-field"></a>Per definire un campo

1.  Nel **le proprietà** impostare nella finestra di **nome** proprietà del descrittore del tipo per il nome di un campo nel tipo che rappresenta l'entità (ad esempio: **FirstName**).

2.  Nell'elenco accanto al **nomeTipo** proprietà, scegliere il tipo di dati appropriato (ad esempio **Int32**).

     Per informazioni sugli altri parametri facoltativi, vedere [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Per definire un'entità

1.  Nel **proprietà** impostare nella finestra di **nome** proprietà a un nome che descriva l'entità (ad esempio: **Contatto**).

2.  Impostare il **TypeName** proprietà per specificare il nome completo del tipo che rappresenta l'entità. Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.

    -   Per una classe nel progetto, scegliere la freccia giù accanto al **nomeTipo** proprietà, scegliere il **progetto corrente** scheda nella finestra di dialogo visualizzata e quindi scelta la classe nel progetto.

         Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB. Nell'esempio seguente imposta il valore della **TypeName** proprietà a una classe nel progetto.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    -   Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.

         Nell'esempio seguente imposta il valore della **TypeName** proprietà a un tipo definito in un assembly cui viene fatto riferimento nella soluzione.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    -   Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include lo spazio dei nomi e il nome del tipo.

         Nell'esempio seguente imposta il valore della **TypeName** proprietà a un tipo nel modello a oggetti di integrazione applicativa dei dati.

         `Microsoft.BusinessData.Runtime.DynamicType`

3.  Nel **Dettagli metodo BDC** finestra, aprire l'elenco visualizzato del descrittore di tipo e quindi scegliere **modificare**.

     Il **Esplora integrazione applicativa dei dati** verrà visualizzata la finestra.

4.  Nel **Esplora integrazione Applicativa**, aprire il menu di scelta rapida del descrittore del tipo e quindi scegliere **Aggiungi descrittore tipo**.

     Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di entità. Configurare il descrittore di tipo come un campo.

5.  Ripetere il passaggio 4 per aggiungere un descrittore di tipo figlio per ogni campo dell'entità.

### <a name="to-define-a-collection-of-entities"></a>Per definire una raccolta di entità

1. Nel **Dettagli metodo BDC** finestra, scegliere il descrittore di tipo del parametro desiderato.

2. Nella barra dei menu, scegliere **View**, **finestra proprietà**.

3. Nel **proprietà** impostare nella finestra di **nome** proprietà a un nome che descriva l'entità (ad esempio: **Contatta**).

4. Impostare il **IsCollection** proprietà **True**. Ciò indica che il descrittore di tipo è una raccolta di entità.

5. Impostare il **nomeTipo** proprietà in una stringa che contiene un riferimento al <xref:System.Collections.Generic.IEnumerable%601> interfaccia e il nome completo del tipo che rappresenta l'entità. Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.

   - Per una classe nel progetto, scegliere la freccia giù accanto al **nomeTipo** proprietà, scegliere il **progetto corrente** scheda nella finestra di dialogo visualizzata e quindi scelta la classe nel progetto.

      Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB.

      Nell'esempio seguente imposta il valore della **TypeName** proprietà a una raccolta di classi nel progetto.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.BdcModel1.Contact, BdcModel1]`

   - Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.

      Nell'esempio seguente imposta il valore della **TypeName** proprietà a una raccolta di tipi in un assembly cui viene fatto riferimento nella soluzione.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`

   - Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include solo lo spazio dei nomi e il nome del tipo.

      Nell'esempio seguente imposta il valore della **TypeName** proprietà a una raccolta di tipi definiti nel modello a oggetti di integrazione applicativa dei dati.

      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`

6. Nel **Dettagli metodo BDC** finestra, aprire l'elenco visualizzato del descrittore di tipo e quindi scegliere **modificare**.

    Il **Esplora integrazione applicativa dei dati** verrà visualizzata la finestra.

7. Nel **Esplora integrazione Applicativa**, aprire il menu di scelta rapida del descrittore del tipo e quindi scegliere **Aggiungi descrittore tipo**.

    Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di raccolta. Configurare il descrittore di tipo come un'entità.

## <a name="see-also"></a>Vedere anche
- [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
- [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
