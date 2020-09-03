---
title: 'Procedura: aggiungere un metodo di aggiornamento | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c76373c710908a8ae7edc49c4e26ff7e94336a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014980"
---
# <a name="how-to-add-an-updater-method"></a>Procedura: aggiungere un metodo di aggiornamento
  È possibile consentire agli utenti di aggiornare i dati aziendali in un elenco esterno di SharePoint creando un metodo di *aggiornamento* . Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Per creare un metodo di aggiornamento

1. Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere un'entità.

2. Sulla barra dei menu scegliere **Visualizza**  >  **altri**  >  **Dettagli metodo di integrazione applicativa dei dati**di Windows.

    Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati. Per altre informazioni su questa finestra, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nell'elenco **Aggiungi metodo** scegliere **Crea metodo di aggiornamento**.

    Visual Studio aggiunge al modello gli elementi seguenti. Questi elementi vengono visualizzati nella finestra Dettagli metodo di integrazione applicativa dei dati.

   - Metodo denominato **Update**.

   - Parametro di input per il metodo.

   - Descrittore di tipo per il parametro. Per impostazione predefinita, Visual Studio usa il descrittore del tipo di entità definito per il metodo Finder (ad esempio: Contact).

   - Istanza di metodo per il metodo.

     Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Se l'identificatore del tipo di entità rappresenta un campo in una tabella di database non generata automaticamente, impostare la proprietà del **campo pre-Updater** su **true**.

4. In **Esplora soluzioni**aprire il menu di scelta rapida del file di codice del servizio generato per l'entità, quindi scegliere **Visualizza codice**.

    Il file di codice di Entity Service verrà aperto nell' **editor di codice**. Per ulteriori informazioni su tale file, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Aggiungere il codice al metodo Update per aggiornare i dati. Nell'esempio seguente vengono aggiornate le informazioni per un contatto nel database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>Vedere anche
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
