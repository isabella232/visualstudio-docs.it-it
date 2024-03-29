---
title: 'Packaging Explorer: aggiungere & rimuovere funzionalità & elementi al pacchetto'
titleSuffix: ''
description: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto SharePoint usando Packaging Explorer in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0b40b21377c0ab566bb33adf3ac0d0f617f0c53c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625128"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Packaging Explorer
  Per configurare un pacchetto per distribuire SharePoint e funzionalità, è possibile usare Packaging Explorer. È possibile modificare gli elementi SharePoint progetto e le funzionalità all'interno del file con estensione wsp.

 In alternativa, è possibile usare Packaging Designer per visualizzare e riordinare le funzionalità per modificare l'ordine di attivazione. Per altre informazioni, [vedere Procedura: Aggiungere e rimuovere funzionalità ed](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)elementi in un pacchetto tramite Progettazione pacchetti.

## <a name="open-the-packaging-explorer"></a>Aprire Packaging Explorer
 È possibile usare la procedura seguente per aprire Packaging Explorer, se la soluzione Visual Studio ha almeno un progetto SharePoint pacchetto. In alternativa, Packaging Explorer viene aperto automaticamente quando si visualizza una finestra di progettazione di funzionalità o pacchetti. Dopo aver chiuso tutte le finestre di progettazione delle funzionalità e dei pacchetti, viene chiuso anche Packaging Explorer.

#### <a name="to-open-the-packaging-explorer"></a>Per aprire Packaging Explorer

1. Sulla barra dei menu scegliere **Visualizza altro**  >  **Windows**  >  **Packaging Explorer.**

     Packaging **Explorer viene** visualizzato nella casella degli **strumenti.**

## <a name="adding-a-feature-to-a-package"></a>Aggiunta di una funzionalità a un pacchetto
 È possibile aggiungere funzionalità nuove ed esistenti a un pacchetto usando Packaging Explorer.

#### <a name="to-add-a-sharepoint-feature"></a>Per aggiungere una SharePoint funzionalità

1. Aprire **Packaging Explorer,** aprire il menu di scelta rapida per il progetto e quindi scegliere **Aggiungi funzionalità.**

#### <a name="to-move-an-existing-sharepoint-feature"></a>Per spostare una funzionalità SharePoint esistente

1. Aprire **Packaging Explorer** e quindi eseguire una delle operazioni seguenti:

    - Trascinare **una funzionalità** da un progetto a un altro progetto.

    - Aprire il menu di scelta rapida per una funzionalità, scegliere Taglia **,** aprire il menu di scelta rapida per il progetto in cui si desidera spostare la funzionalità e quindi scegliere **Incolla.**

    > [!NOTE]
    > Utilizzare questa procedura se nella soluzione sono presenti diversi progetti SharePoint.

## <a name="validate-a-feature-or-package"></a>Convalidare una funzionalità o un pacchetto
 È possibile identificare potenziali problemi nelle SharePoint e nei pacchetti convalidando i file. Gli avvisi e gli errori vengono visualizzati nella finestra Output e nella finestra Elenco errori.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Per convalidare una SharePoint o un pacchetto

1. Aprire **Packaging Explorer.**

2. Aprire un menu di scelta rapida per una funzionalità o un pacchetto e quindi scegliere **Convalida.**

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
