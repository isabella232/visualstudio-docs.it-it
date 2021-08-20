---
title: 'Procedura: Aggiungere un metodo deleter | Microsoft Docs'
description: Informazioni su come aggiungere un metodo Deleter in BDC Designer di Visual Studio, in modo che un utente finale possa eliminare un record di dati da un elenco esterno in un SharePoint sito.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b4c42d5020ff78a2d2e66715edb913fe8cea127e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149234"
---
# <a name="how-to-add-a-deleter-method"></a>Procedura: Aggiungere un metodo Deleter
  È possibile consentire a un utente finale di eliminare un record di dati da un elenco esterno in un sito SharePoint aggiungendo un metodo Deleter al modello. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-a-deleter-method"></a>Per creare un metodo Deleter

1. In Progettazione **integrazione applicativa dei** dati scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza altri dettagli**  >  **Windows**  >  **metodo BDC**.

    Verrà **visualizzata la finestra BDC Method Details (Dettagli metodo BDC).** Per altre informazioni su questa finestra, vedere Panoramica [degli strumenti di progettazione del modello BDC.](../sharepoint/bdc-model-design-tools-overview.md)

3. **Nell'elenco Add a Method (Aggiungi** metodo) scegliere Create a **Deleter Method (Crea metodo deleter).**

    Visual Studio aggiunge gli elementi seguenti al modello. Questi elementi vengono visualizzati nella **finestra Dettagli metodo BDC.**

   - Un metodo denominato **Delete.**

   - Parametro di input per il metodo.

   - Descrittore di tipo per il parametro.

   - Istanza del metodo per il metodo.

     Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità e quindi scegliere **Visualizza codice.**

    Il file di codice del servizio entità viene aperto nell'editor di codice. Per altre informazioni sul file di codice del servizio entità, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Aggiungere codice al metodo Deleter per eliminare un record. L'esempio seguente elimina una voce da un ordine di vendita usando il database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Il metodo in questo esempio usa due parametri di input.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet6":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet6":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
