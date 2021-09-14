---
title: 'Procedura: Aggiungere un metodo Creator | Microsoft Docs'
description: Informazioni su come aggiungere un metodo Creator, che aggiunge nuovi dati all'origine dati di un'entità nel servizio Business Data Connectivity (BDC) in SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: adec17c0a381edb3587da50d3d9e3e8aedbc6cdd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625200"
---
# <a name="how-to-add-a-creator-method"></a>Procedura: Aggiungere un metodo Creator
  Un metodo Creator aggiunge nuovi dati all'origine dati di un'entità. Il servizio BDC (Business Data Connectivity) chiama  questo metodo  quando gli utenti scelgono il pulsante Nuovo elemento sulla barra multifunzione di un elenco basato sul modello. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-add-a-creator-method"></a>Per aggiungere un metodo Creator

1. In Progettazione **integrazione applicativa dei** dati scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza altri**  >  **Windows**  > **dettagli metodo BDC**.

    Verrà **visualizzata la finestra BDC Method Details (Dettagli metodo BDC).** Per altre informazioni su tale finestra, vedere Panoramica [degli strumenti di progettazione del modello BDC.](../sharepoint/bdc-model-design-tools-overview.md)

3. **Nell'elenco Add a Method (Aggiungi** metodo) scegliere Create Creator Method **(Crea metodo creator).**

    Visual Studio aggiunge gli elementi seguenti al modello e questi elementi vengono visualizzati nella finestra **Dettagli metodo BDC.**

   - Un metodo denominato **Create.**

   - Parametro di input per il metodo.

   - Parametro restituito per il metodo.

   - Descrittori di tipo per i parametri.

   - Istanza del metodo per il metodo.

     Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità e quindi scegliere **Visualizza codice.**

    Il file di codice del servizio entità viene aperto nell'editor di codice. Per altre informazioni sul file di codice del servizio entità, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Aggiungere al metodo Creator il codice che aggiunge dati all'origine dati. Nell'esempio seguente viene aggiunto un contatto al database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
