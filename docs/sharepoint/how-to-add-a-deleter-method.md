---
title: 'Procedura: aggiungere un metodo Deleter | Microsoft Docs'
description: Informazioni su come aggiungere un metodo Deleter nella finestra di progettazione dell'integrazione applicativa dei dati di Visual Studio, in modo che un utente finale possa eliminare un record di dati da un elenco esterno in un sito di SharePoint.
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
ms.workload:
- office
ms.openlocfilehash: f5c9dc0a5ca6b7651b4ddc1f4b58a8b72305a1a5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217996"
---
# <a name="how-to-add-a-deleter-method"></a>Procedura: aggiungere un metodo Deleter
  È possibile consentire a un utente finale di eliminare un record di dati da un elenco esterno in un sito di SharePoint aggiungendo un metodo Deleter al modello. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Per creare un metodo Deleter

1. Nella **finestra di progettazione dell'integrazione applicativa** dei dati scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza**  >  **altri**  >  **Dettagli metodo di integrazione applicativa dei dati** di Windows.

    Verrà visualizzata la finestra **Dettagli metodo BDC** . Per altre informazioni su questa finestra, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nell'elenco **Aggiungi metodo** scegliere **Crea un metodo Deleter**.

    Visual Studio aggiunge al modello gli elementi seguenti. Questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati** .

   - Metodo denominato **Delete**.

   - Parametro di input per il metodo.

   - Descrittore di tipo per il parametro.

   - Istanza di metodo per il metodo.

     Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

4. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità, quindi scegliere **Visualizza codice**.

    Il file di codice di Entity Service verrà aperto nell'editor di codice. Per altre informazioni sul file di codice di Entity Service, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Aggiungere il codice al metodo Deleter per eliminare un record. Nell'esempio seguente viene eliminata una voce da un ordine di vendita utilizzando il database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Il metodo in questo esempio usa due parametri di input.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet6":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet6":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
