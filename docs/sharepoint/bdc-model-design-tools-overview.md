---
title: Panoramica degli strumenti di progettazione dei modelli BDC | Microsoft Docs
description: Leggi una panoramica degli strumenti di progettazione da usare con un modello di integrazione applicativa dei dati. Informazioni sulla finestra di progettazione dell'integrazione applicativa dei dati, la finestra Dettagli del metodo BDC e l'esplorazione BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6e78b6809d3136c0db1f558d175706dc0ecd75b
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850312"
---
# <a name="bdc-model-design-tools-overview"></a>Panoramica degli strumenti di progettazione dei modelli BDC
  È possibile progettare un modello di integrazione applicativa dei dati tramite la finestra di progettazione dell'integrazione applicativa dei dati, la finestra **Dettagli metodo** di integrazione applicativa dei dati e l' **esplorazione BDC**.

 **Esplora integrazione applicativa** dei dati consente di esplorare il modello, eseguire ricerche nel modello e definire descrittori di tipo.

## <a name="bdc-designer"></a>Progettazione integrazione applicativa dei dati
 La finestra di progettazione dell'integrazione applicativa dei dati consente di definire le entità nel modello e di organizzare visivamente le relazioni tra loro. Utilizzare la finestra di progettazione dell'integrazione applicativa dei dati per eseguire le attività seguenti:

- Aggiungere entità al modello.

- Rimuovere entità dal modello.

- Definire le relazioni tra entità.

  Per aprire la finestra di progettazione dell'integrazione applicativa dei dati, fare doppio clic sul file del modello nel progetto oppure aprire il menu di scelta rapida per il file del modello, quindi scegliere **Apri**. Aggiungere un'entità al modello trascinando o copiando un' **entità** dalla **casella degli strumenti** nella finestra di progettazione. Per creare un'associazione tra due entità, scegliere il controllo **associazione** nella **casella degli strumenti**, scegliere la prima entità, quindi scegliere la seconda entità.

## <a name="bdc-method-details-window"></a>Finestra Dettagli metodo di integrazione applicativa dei dati
 Utilizzare la finestra **Dettagli metodo di integrazione applicativa dei dati** per definire i parametri, le istanze e i descrittori di filtro di un metodo.

 Nella finestra **Dettagli metodo di integrazione applicativa dei dati** è possibile generare rapidamente metodi Finder, Finder specifico, creatore, aggiornamento ed eliminatori. Quando si generano questi metodi, Visual Studio aggiunge al metodo i metadati, ad esempio parametri, istanze e descrittori di tipo. È possibile modificare questi metadati per soddisfare lo scenario specifico.

 Per aprire la finestra **Dettagli metodo di integrazione applicativa dei dati** , sulla barra dei menu scegliere **Visualizza**  >  **altri**  >  **Dettagli metodo di integrazione applicativa** Windows.

 Per visualizzare i metodi nella finestra **Dettagli metodo BDC** , scegliere l'entità nella finestra di progettazione dell'integrazione applicativa dei dati. I metodi dell'entità selezionata vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati** . Se non si sceglie un'entità nella finestra di progettazione dell'integrazione applicativa dei dati, nella finestra **Dettagli metodo BDC** non vengono visualizzate informazioni.

 Espandere o comprimere i nodi nella finestra **Dettagli metodo di integrazione applicativa dei dati** per definire parametri, istanze e descrittori di filtro. Utilizzare **Esplora integrazione applicativa** dei dati per definire i descrittori di tipo.

## <a name="bdc-explorer"></a>Esplora integrazione applicativa dei dati
 In **Esplora integrazione applicativa** dei dati vengono visualizzati gli elementi che costituiscono il modello. Per aprire **Esplora integrazione applicativa** dei dati, sulla barra dei menu scegliere **Visualizza**  >  **altro**  >  **Esplora BDC** di Windows. Per esplorare il modello, espandere i nodi in **Esplora integrazione applicativa** dei dati. Ogni nodo rappresenta un elemento nel codice XML del file di modello.

 Quando si scelgono i nodi in **Esplora integrazione applicativa** dei dati, le proprietà di ogni nodo scelto vengono visualizzate nella finestra **Proprietà** . Molte di queste proprietà corrispondono agli attributi nel file di modello. È possibile eseguire ricerche nel modello utilizzando la casella di ricerca nella parte superiore di **Esplora integrazione applicativa** dei dati.

> [!NOTE]
> In **Esplora integrazione applicativa** dei dati non vengono visualizzati identificatori, proprietà personalizzate, stringhe localizzate, gruppi di associazioni, azioni, descrittori di filtro, elenchi di controlli delle azioni e valori di parametro predefiniti.

### <a name="define-type-descriptors"></a>Definisci descrittori di tipo
 Utilizzare **Esplora integrazione applicativa** dei dati per definire i descrittori di tipo. Esplora integrazione applicativa dei dati consente di definire un descrittore di tipo una sola volta e quindi di riutilizzare il descrittore di tipo in un'altra posizione A tale scopo, copiare un descrittore di tipo e incollarlo in qualsiasi altro parametro o descrittore di tipo.

> [!NOTE]
> Le modifiche a un descrittore di tipo originale non influiscono sulle copie del descrittore di tipo.

 Per altre informazioni, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Procedura dettagliata: creare un elenco esterno in SharePoint usando i dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
