---
title: 'Procedura: aggiungere un metodo Creator | Microsoft Docs'
description: Informazioni su come aggiungere un metodo Creator, che aggiunge nuovi dati all'origine dati di un'entità nel servizio di integrazione applicativa dei dati in SharePoint.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 790b4265b232c71ff3e0613cffcb45e710081fa3
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915453"
---
# <a name="how-to-add-a-creator-method"></a>Procedura: aggiungere un metodo Creator
  Un metodo Creator aggiunge nuovi dati all'origine dati di un'entità. Il servizio di integrazione applicativa dei dati chiama questo metodo quando gli utenti scelgono il pulsante **nuovo elemento** sulla **barra multifunzione** di un elenco basato sul modello. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Per aggiungere un metodo Creator

1. Nella **finestra di progettazione dell'integrazione applicativa** dei dati scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza**  >  **altri**  > **Dettagli metodo di integrazione applicativa dei dati** di Windows.

    Verrà visualizzata la finestra **Dettagli metodo BDC** . Per ulteriori informazioni su tale finestra, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nell'elenco **Aggiungi metodo** scegliere **Crea metodo creatore**.

    Visual Studio aggiunge gli elementi seguenti al modello e questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati** .

   - Metodo denominato **create**.

   - Parametro di input per il metodo.

   - Parametro restituito per il metodo.

   - Descrittori di tipo per i parametri.

   - Istanza di metodo per il metodo.

     Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

4. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità, quindi scegliere **Visualizza codice**.

    Il file di codice di Entity Service verrà aperto nell'editor di codice. Per altre informazioni sul file di codice di Entity Service, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Aggiungere il codice al metodo Creator che aggiunge i dati all'origine dati. Nell'esempio seguente viene aggiunto un contatto al database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
