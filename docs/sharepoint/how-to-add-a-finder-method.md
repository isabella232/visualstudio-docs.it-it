---
title: 'Procedura: aggiungere un metodo Finder | Microsoft Docs'
description: Aggiungere un metodo Finder in Visual Studio, che consente al servizio di integrazione applicativa dei dati di visualizzare un elenco di entità in una Web part o un elenco di SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7e2bb74278194878ed4496c12c918707cdc1e6e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915089"
---
# <a name="how-to-add-a-finder-method"></a>Procedura: aggiungere un metodo Finder
  Per abilitare il servizio di integrazione applicativa dei dati per visualizzare un elenco di entità in una Web part o in un elenco, è necessario creare un metodo *Finder* . Un metodo di ricerca è un metodo speciale che restituisce una raccolta di istanze di entità. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Per creare un metodo Finder

1. Nella **finestra di progettazione dell'integrazione applicativa** dei dati scegliere un'entità.

    Per altre informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Sulla barra dei menu scegliere **Visualizza**  >  **altri**  >  **Dettagli metodo di integrazione applicativa dei dati** di Windows.

    Verrà visualizzata la finestra **Dettagli metodo BDC** . Per ulteriori informazioni sulla finestra **Dettagli metodo di integrazione applicativa dei dati** , vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nell'elenco **Aggiungi metodo** scegliere **Crea metodo Finder**.

    Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Configurare il descrittore di tipo come descrittore di tipo di raccolta di entità. Per ulteriori informazioni sulla creazione di un descrittore di tipo di raccolta di entità, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Non è necessario eseguire questo passaggio se è stato aggiunto un metodo di ricerca specifico all'entità. Visual Studio usa il descrittore di tipo definito nel metodo di ricerca specifico.

5. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità, quindi scegliere **Visualizza codice**. Per ulteriori informazioni sul file di codice del servizio, vedere la pagina relativa alla [creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Aggiungere il codice al metodo Finder. Il codice esegue queste operazioni:

   - Recupera i dati da un'origine dati.

   - Restituisce un elenco di entità al servizio di integrazione applicativa dei dati.

     Nell'esempio seguente viene restituita una raccolta di `Contact` entità utilizzando i dati del database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
