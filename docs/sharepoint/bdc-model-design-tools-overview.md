---
title: Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati | Microsoft Docs
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
ms.openlocfilehash: eb2f257feaa8faa6acf58c8e8763d15d08a1079e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596568"
---
# <a name="bdc-model-design-tools-overview"></a>Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati
  È possibile progettare un modello di integrazione applicativa dei dati (BDC) usando la finestra di progettazione di integrazione applicativa dei dati, il **Dettagli metodo BDC** finestra e il **Esplora integrazione applicativa dei dati**.

 Il **Esplora integrazione applicativa dei dati** consente di esplorare il modello, il modello di ricerca e definire i descrittori di tipo.

## <a name="bdc-designer"></a>Finestra di progettazione integrazione applicativa dei dati
 La finestra di progettazione di integrazione applicativa dei dati ti permette di definire le entità nel modello e per disporre in modo visivo le relazioni tra loro. Utilizzare la finestra di progettazione di integrazione applicativa dei dati per eseguire le attività seguenti:

- Aggiungere le entità nel modello.

- Rimuovere entità dal modello.

- Definire le relazioni tra entità.

  Per aprire la finestra di progettazione di integrazione applicativa dei dati, fare doppio clic il file del modello nel progetto o aprire il menu di scelta rapida per il file del modello e quindi scegliere **aprire**. Aggiungere un'entità nel modello trascinando o copiando un **Entity** dalle **della casella degli strumenti** nella finestra di progettazione. Per creare un'associazione tra due entità, scegliere il **Association** controllare nel **della casella degli strumenti**, scegliere la prima entità e quindi scegliere la seconda entità.

## <a name="bdc-method-details-window"></a>Finestra Dettagli metodo di integrazione applicativa dei dati
 Usare la **Dettagli metodo BDC** finestra per definire i parametri, le istanze e descrittori di filtro di un metodo.

 È possibile generare rapidamente Finder Finder specifico, autore, aggiornamento e Deleter metodi nel **Dettagli metodo BDC** finestra. Quando si generano questi metodi, Visual Studio aggiunge i metadati, ad esempio parametri, le istanze e descrittori del tipo, al metodo. È possibile modificare i metadati per soddisfare uno scenario specifico.

 Per aprire la **Dettagli metodo BDC** finestra nella barra dei menu, scegliere **View** > **Other Windows** > **Dettagli metodo di integrazione applicativa dei dati** .

 Per visualizzare i metodi nel **Dettagli metodo BDC** finestra, scegliere l'entità nella finestra di progettazione integrazione applicativa dei dati. I metodi dell'entità selezionata vengono visualizzati nei **Dettagli metodo BDC** finestra. Se non si sceglie un'entità nella finestra di progettazione integrazione applicativa dei dati, il **Dettagli metodo BDC** finestra consente di visualizzare alcuna informazione.

 Espandere o comprimere nodi il **Dettagli metodo BDC** finestra definire parametri, le istanze e descrittori di filtro. Usare la **Esplora integrazione applicativa dei dati** per definire i descrittori di tipo.

## <a name="bdc-explorer"></a>Esplora integrazione applicativa dei dati
 Il **Esplora integrazione applicativa dei dati** Visualizza gli elementi che costituiscono il modello. Per aprire la **Esplora integrazione applicativa dei dati**, nella barra dei menu, scegliere **View** > **Other Windows** > **Esplora integrazione applicativa dei dati**. Per esplorare il modello, espandere i nodi le **Esplora integrazione applicativa dei dati**. Ogni nodo rappresenta un elemento nel codice XML del file del modello.

 Mentre si selezionano nodi nel **Esplora integrazione Applicativa**, vengono visualizzate le proprietà di ogni nodo che si sceglie nel **proprietà** finestra. Molte di queste proprietà corrispondono agli attributi nel file del modello. È possibile cercare il modello usando la casella di ricerca in cima il **Esplora integrazione applicativa dei dati**.

> [!NOTE]
>  Il **Esplora integrazione applicativa dei dati** non visualizza gli identificatori, le proprietà personalizzate, le stringhe localizzate, i gruppi di associazioni, azioni, descrittori di filtro, gli elenchi di controllo di azione e i valori di parametro predefiniti.

### <a name="define-type-descriptors"></a>Definire i descrittori di tipo
 Usare la **Esplora integrazione applicativa dei dati** per definire i descrittori di tipo. Le soluzioni di integrazione applicativa dei dati consente di definire un descrittore di tipi una sola volta e riusare quindi tale descrittore di tipo in un' posizione nel modello. A tale scopo, copiare un descrittore di tipi e incollarlo in qualsiasi altro parametro oppure descrittore di tipo.

> [!NOTE]
>  Le modifiche a un descrittore di tipo originale non influiscono le copie che del descrittore di tipo.

 Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Creare un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)
- [Procedura dettagliata: Creare un elenco esterno in SharePoint utilizzando i dati di business](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Creazione di un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettazione di un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
