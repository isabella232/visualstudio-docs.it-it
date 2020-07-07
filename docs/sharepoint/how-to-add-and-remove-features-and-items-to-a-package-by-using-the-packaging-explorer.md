---
title: 'Esplora pacchetti: aggiungere & rimuovere funzionalità & elementi al pacchetto'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3ea7e30737855cbbb9434e8763f4903d80b82da
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014551"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Esplora pacchetti
  Per configurare un pacchetto per la distribuzione di elementi e funzionalità di SharePoint, è possibile utilizzare Esplora pacchetti. È possibile modificare le funzionalità e gli elementi del progetto SharePoint all'interno del file con estensione wsp.

 In alternativa, è possibile utilizzare la finestra di progettazione per la creazione di pacchetti per visualizzare e riordinare le funzionalità per modificare l'ordine di attivazione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Aprire Esplora pacchetti
 È possibile utilizzare la procedura seguente per aprire Esplora pacchetti, se la soluzione di Visual Studio include almeno un progetto SharePoint. In alternativa, Esplora pacchetti viene aperto automaticamente quando si visualizza una funzionalità o progettazione pacchetti. Dopo aver chiuso tutte le finestre di progettazione di pacchetti e funzionalità, viene chiuso anche lo Esplora pacchetti.

#### <a name="to-open-the-packaging-explorer"></a>Per aprire Esplora pacchetti

1. Sulla barra dei menu scegliere **Visualizza**  >  **altri Windows**  >  **Packaging Explorer**.

     **Esplora pacchetti** viene visualizzato nella **casella degli strumenti**.

## <a name="adding-a-feature-to-a-package"></a>Aggiunta di una funzionalità a un pacchetto
 È possibile aggiungere funzionalità nuove ed esistenti a un pacchetto usando Esplora pacchetti.

#### <a name="to-add-a-sharepoint-feature"></a>Per aggiungere una funzionalità di SharePoint

1. Aprire **Esplora pacchetti**, aprire il menu di scelta rapida per il progetto, quindi scegliere **Aggiungi funzionalità**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Per spostare una funzionalità di SharePoint esistente

1. Aprire **Esplora pacchetti**, quindi eseguire una delle operazioni seguenti:

    - Trascinare una **funzionalità** da un progetto a un altro progetto.

    - Aprire il menu di scelta rapida per una funzionalità, scegliere **taglia**, aprire il menu di scelta rapida per il progetto in cui si desidera spostare la funzionalità, quindi scegliere **Incolla**.

    > [!NOTE]
    > Utilizzare questa procedura se nella soluzione sono presenti diversi progetti SharePoint.

## <a name="validate-a-feature-or-package"></a>Convalidare una funzionalità o un pacchetto
 È possibile identificare potenziali problemi nelle funzionalità e nei pacchetti di SharePoint convalidando i file. Gli avvisi e gli errori vengono visualizzati nella finestra di output e Elenco errori finestra.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Per convalidare una funzionalità o un pacchetto di SharePoint

1. Aprire **Esplora pacchetti**.

2. Aprire un menu di scelta rapida per una funzionalità o un pacchetto, quindi scegliere **convalida**.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
