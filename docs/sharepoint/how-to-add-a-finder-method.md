---
title: 'Procedura: Aggiungere un metodo Finder | Microsoft Docs'
description: Aggiungere un metodo Finder in Visual Studio, che consente al servizio BDC (Business Data Connectivity) di visualizzare un elenco di entità in una web part SharePoint o un elenco.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 3df15148f2a42d0dea7a258d17097d515a1249e9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625193"
---
# <a name="how-to-add-a-finder-method"></a>Procedura: Aggiungere un metodo Finder
  Per consentire al servizio Business Data Connectivity (BDC) di visualizzare un elenco di entità in una web part o un elenco, è necessario creare un *metodo Finder.* Un metodo Finder è un metodo speciale che restituisce una raccolta di istanze di entità. Per altre informazioni, vedere [Progettazione di un modello di connettività dei dati di business.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-a-finder-method"></a>Per creare un metodo Finder

1. In Progettazione **integrazione applicativa dei** dati scegliere un'entità.

    Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello.](../sharepoint/how-to-add-an-entity-to-a-model.md)

2. Sulla barra dei menu scegliere **Visualizza altri**  >  **Windows**  >  **dettagli metodo BDC**.

    Verrà **visualizzata la finestra BDC Method Details (Dettagli metodo BDC).** Per altre informazioni sulla finestra **Dettagli metodo BDC,** vedere Panoramica degli strumenti di progettazione del [modello BDC.](../sharepoint/bdc-model-design-tools-overview.md)

3. **Nell'elenco Add a Method (Aggiungi** metodo) scegliere Create Finder Method **(Crea metodo Finder).**

    Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Configurare il descrittore di tipo come descrittore di tipo della raccolta di entità. Per altre informazioni su come creare un descrittore del tipo di raccolta di entità, vedere [Procedura: Definire](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)il descrittore di tipo di un parametro .

   > [!NOTE]
   > Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder specifico all'entità. Visual Studio usa il descrittore di tipo definito nel metodo Finder specifico.

5. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità e quindi scegliere **Visualizza codice.** Per altre informazioni sul file di codice del servizio, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

6. Aggiungere codice al metodo Finder. Il codice esegue queste operazioni:

   - Recupera i dati da un'origine dati.

   - Restituisce un elenco di entità al servizio BDC.

     L'esempio seguente restituisce una raccolta di entità usando i dati del `Contact` database di esempio AdventureWorks per SQL Server.

   > [!NOTE]
   > Sostituire il valore del `ServerName` campo con il nome del server.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
