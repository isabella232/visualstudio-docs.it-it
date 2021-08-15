---
title: 'Procedura: Aggiungere un metodo Finder specifico | Microsoft Docs'
description: Ottenere un'istanza di entità aggiungendo un metodo Finder. Il servizio BDC chiama il metodo quando un utente seleziona un'entità in una web part di dati aziendali o in un elenco esterno.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8dd983f9a7929298dc6f5e3ef549027d9ab15ba4cbe180483a617712f3e30af6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315187"
---
# <a name="how-to-add-a-specific-finder-method"></a>Procedura: Aggiungere un metodo Finder specifico
  È possibile restituire una singola istanza di entità creando un *metodo Finder* specifico. Il servizio BDC (Business Data Connectivity) esegue il metodo Finder specifico quando un utente sceglie un'entità in una web part di dati business o in un elenco esterno. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-a-specific-finder-method"></a>Per creare un metodo Finder specifico

1. In Progettazione **BDC** scegliere un'entità.

    Per informazioni su come aggiungere un'entità a **Progettazione integrazione** Visual Studio, vedere [Procedura: Aggiungere un'entità a un modello.](../sharepoint/how-to-add-an-entity-to-a-model.md)

2. Sulla barra dei menu scegliere **Visualizza** altri  >  **Windows**, Dettagli **metodo BDC**.

    Verrà **visualizzata la finestra Dettagli metodo BDC.** Per altre informazioni su tale finestra, vedere Panoramica degli strumenti di progettazione del modello [BDC.](../sharepoint/bdc-model-design-tools-overview.md)

3. **Nell'elenco Add a Method (Aggiungi metodo)** scegliere Create Specific Finder Method **(Crea metodo Finder specifico).**

    Visual Studio aggiunge gli elementi seguenti al modello. Questi elementi vengono visualizzati nella finestra **Dettagli metodo BDC.**

   - Un metodo.

   - Parametro di input per il metodo.

   - Parametro restituito per il metodo.

   - Descrittore di tipo per ogni parametro.

   - Istanza del metodo per il metodo .

     Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. Aprire la Visual Studio **proprietà.**

5. Configurare il descrittore di tipo del parametro restituito come descrittore del tipo di entità. Per informazioni su come creare un descrittore del tipo di entità, vedere [Procedura: Definire il](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)descrittore di tipo di un parametro .

   > [!NOTE]
   > Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder all'entità. Visual Studio il descrittore di tipo definito nel metodo Finder.

   > [!NOTE]
   > Se il campo identificatore del tipo di entità rappresenta un campo in una tabella di database generata automaticamente, impostare la proprietà **Di** sola lettura del campo identificatore su **True**.

6. Nella finestra **Dettagli metodo** scegliere l'istanza del metodo.

7. Nella finestra **Proprietà** impostare la **proprietà Return Parameter Name** sul nome del parametro restituito del metodo. Per altre informazioni sulle proprietà dell'istanza del metodo, vedere [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità e quindi scegliere **Visualizza codice**.

    Il file di codice del servizio entità viene aperto nell'editor di codice. Per altre informazioni sul file di codice del servizio entità, vedere [Creare un modello di connettività dati business](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Aggiungere codice al metodo Finder specifico. Il codice esegue queste operazioni:

   - Recupera un record da un'origine dati.

   - Restituisce un'entità al servizio BDC.

     Nell'esempio seguente viene restituito un contatto dal database di esempio AdventureWorks per SQL Server.

     > [!NOTE]
     > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
