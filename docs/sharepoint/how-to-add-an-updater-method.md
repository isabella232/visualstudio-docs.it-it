---
title: 'Procedura: Aggiungere un metodo updater | Microsoft Docs'
description: Informazioni su come consentire agli utenti di aggiornare i dati aziendali in un SharePoint esterno aggiungendo un metodo updater.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dbdd742184ebea14912bbcca2938192b8de459f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093099"
---
# <a name="how-to-add-an-updater-method"></a>Procedura: Aggiungere un metodo Updater
  È possibile abilitare gli utenti per aggiornare i dati aziendali in un SharePoint esterno creando un *metodo updater.* Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-an-updater-method"></a>Per creare un metodo Updater

1. Nella finestra di progettazione BDC scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza altri**  >  **Windows**  >  **metodo BDC**.

    Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati. Per altre informazioni su questa finestra, vedere Panoramica degli strumenti di progettazione del modello [BDC.](../sharepoint/bdc-model-design-tools-overview.md)

3. **Nell'elenco Aggiungi metodo** scegliere Crea metodo di **aggiornamento**.

    Visual Studio aggiunge gli elementi seguenti al modello. Questi elementi vengono visualizzati nella finestra Dettagli metodo BDC.

   - Metodo denominato **Update**.

   - Parametro di input per il metodo.

   - Descrittore di tipo per il parametro. Per impostazione predefinita, Visual Studio il descrittore del tipo di entità definito per il metodo Finder (ad esempio, Contact).

   - Istanza del metodo per il metodo .

     Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

   > [!NOTE]
   > Se l'identificatore del tipo di entità rappresenta un campo in una tabella di database non generato automaticamente, impostare la proprietà **Campo pre-aggiornamento** su **True.**

4. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità e quindi scegliere **Visualizza codice**.

    Il file di codice del servizio entità viene aperto **nell'editor di codice**. Per altre informazioni su tale file, vedere Creare un modello di [connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Aggiungere codice al metodo Update per aggiornare i dati. L'esempio seguente aggiorna le informazioni per un contatto nel database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet5":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet5":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
