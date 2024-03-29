---
title: Panoramica degli strumenti di progettazione del modello BDC | Microsoft Docs
description: Leggere una panoramica degli strumenti di progettazione da usare con un modello BDC (Business Data Connectivity). Informazioni su Progettazione BDC, sulla finestra Dettagli metodo BDC e su BDC Explorer.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e2045699cf0ce48edef3c9186cea3135c0a54dab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060336"
---
# <a name="bdc-model-design-tools-overview"></a>Panoramica degli strumenti di progettazione del modello BDC
  È possibile progettare un modello di integrazione applicativa dei dati (BDC) usando Progettazione BDC, la finestra Dettagli metodo **BDC** e **BDC Explorer.**

 BDC **Explorer consente** di esplorare il modello, cercare il modello e definire i descrittori di tipo.

## <a name="bdc-designer"></a>Progettazione BDC
 BDC Designer consente di definire le entità nel modello e di disporre visivamente le relazioni tra loro. Usare Progettazione integrazione applicativa dei dati per eseguire le attività seguenti:

- Aggiungere entità al modello.

- Rimuovere entità dal modello.

- Definire le relazioni tra entità.

  Per aprire Progettazione integrazione applicativa dei dati, fare doppio clic sul file del modello nel progetto oppure aprire il menu di scelta rapida per il file di modello e quindi scegliere **Apri**. Aggiungere un'entità al modello trascinando o copiando **un'entità** dalla casella **degli** strumenti nella finestra di progettazione. Per creare un'associazione tra due  entità, scegliere il controllo Associazione nella casella degli **strumenti,** scegliere la prima entità e quindi scegliere la seconda entità.

## <a name="bdc-method-details-window"></a>Finestra Dettagli metodo BDC
 Usare la **finestra Dettagli metodo BDC** per definire i parametri, le istanze e i descrittori di filtro di un metodo.

 È possibile generare rapidamente i metodi Finder, Specific Finder, Creator, Updater e Deleter nella finestra **Dettagli metodo BDC.** Quando si generano questi metodi, Visual Studio al metodo vengono aggiunti metadati, ad esempio parametri, istanze e descrittori di tipo. È possibile modificare questi metadati per soddisfare lo scenario specifico.

 Per aprire la **finestra Dettagli metodo BDC,** sulla barra dei menu scegliere Visualizza altri Windows   >    >  **dettagli metodo BDC**.

 Per visualizzare i metodi nella **finestra Dettagli metodo BDC,** scegliere l'entità in Progettazione BDC. I metodi dell'entità selezionata vengono visualizzati nella finestra **Dettagli metodo BDC.** Se non si sceglie un'entità in Progettazione integrazione applicativa dei dati, nella finestra Dettagli metodo **BDC** non vengono visualizzate informazioni.

 Espandere o comprimere i nodi nella finestra Dettagli metodo **BDC** per definire parametri, istanze e descrittori di filtro. Usare **BDC Explorer** per definire i descrittori di tipo.

## <a name="bdc-explorer"></a>Esplora integrazione applicativa dei dati
 BDC **Explorer visualizza** gli elementi che costituiscono il modello. Per aprire **BDC Explorer,** sulla barra dei menu scegliere Visualizza  >  **Windows**  >  **BDC Explorer.** Per esplorare il modello, espandere i nodi in **BDC Explorer.** Ogni nodo rappresenta un elemento nel codice XML del file di modello.

 Quando si scelgono i nodi in **BDC Explorer,** le proprietà di ogni nodo scelto vengono visualizzate nella **finestra** Proprietà. Molte di queste proprietà corrispondono agli attributi nel file di modello. È possibile cercare il modello usando la casella di ricerca nella parte superiore di **BDC Explorer.**

> [!NOTE]
> BDC **Explorer** non visualizza identificatori, proprietà personalizzate, stringhe localizzate, gruppi di associazioni, azioni, descrittori di filtro, elenchi di controllo delle azioni e valori dei parametri predefiniti.

### <a name="define-type-descriptors"></a>Definire i descrittori di tipo
 Usare **BDC Explorer** per definire i descrittori di tipo. BDC Explorer consente di definire un descrittore di tipo una sola volta e quindi di riutilizzarlo in un'altra posizione del modello. A tale scopo, copiare un descrittore di tipo e incollarlo in qualsiasi altro parametro o descrittore di tipo.

> [!NOTE]
> Le modifiche apportate a un descrittore di tipo originale non influiscono sulle copie di tale descrittore.

 Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Procedura dettagliata: Creare un elenco esterno in SharePoint usando i dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Creazione di un modello di connettività dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettazione di un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)
