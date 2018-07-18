---
title: 'Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Esplora pacchetti | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7875401dee07961d63de6c7b71a97e647c21a0b7
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755612"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Esplora pacchetti
  Per configurare un pacchetto per distribuire gli elementi di SharePoint e le funzionalità, è possibile usare Esplora pacchetti. È possibile regolare i elementi di progetto SharePoint e le funzionalità all'interno del file con estensione wsp.  
  
 In alternativa, è possibile utilizzare la finestra di progettazione di creazione di pacchetti per visualizzare e riordinare le funzionalità per modificare l'ordine di attivazione. Per altre informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="open-the-packaging-explorer"></a>Aprire Esplora pacchetti  
 È possibile utilizzare la procedura seguente per aprire l'Explorer di creazione dei pacchetti, se la soluzione di Visual Studio contiene almeno un progetto SharePoint. In alternativa, Esplora pacchetti viene aperto automaticamente quando si visualizza una finestra di progettazione di funzionalità o un pacchetto. Dopo aver chiuso tutte le finestre di progettazione di funzionalità e del pacchetto, viene chiusa anche Esplora pacchetti.  
  
#### <a name="to-open-the-packaging-explorer"></a>Per aprire Esplora pacchetti  
  
1.  Nella barra dei menu, scegliere **View** > **Other Windows** > **Esplora pacchetti**.  
  
     Il **Esplora pacchetti** viene visualizzato nei **della casella degli strumenti**.  
  
## <a name="adding-a-feature-to-a-package"></a>Aggiunta di una funzionalità a un pacchetto  
 È possibile aggiungere le funzionalità nuove ed esistenti a un pacchetto usando Esplora pacchetti.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Per aggiungere una funzionalità di SharePoint
  
1.  Aprire il **Esplora pacchetti**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Aggiungi funzionalità**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Per spostare una funzionalità di SharePoint esistente  
  
1.  Aprire il **Esplora pacchetti**e quindi effettuare una delle operazioni seguenti:  
  
    -   Trascinare un **funzionalità** da un progetto a un altro progetto.  
  
    -   Aprire il menu di scelta rapida per una funzionalità, scegliere **tagliare**, aprire il menu di scelta rapida per il progetto a cui si desidera spostare la funzionalità e quindi scegliere **Incolla**.  
  
    > [!NOTE]  
    >  Utilizzare questa procedura se nella soluzione sono presenti diversi progetti SharePoint.  
  
## <a name="validate-a-feature-or-package"></a>Convalidare una funzionalità o un pacchetto  
 È possibile identificare problemi potenziali nella funzionalità di SharePoint e i pacchetti tramite la convalida i file. Errori e avvisi vengono visualizzati nella finestra di Output e finestra Elenco errori.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Per convalidare un pacchetto o una funzionalità SharePoint
  
1.  Aprire il **Esplora pacchetti**.  
  
2.  Aprire un menu di scelta rapida per una funzionalità o un pacchetto e quindi scegliere **Validate**.  
  
## <a name="see-also"></a>Vedere anche
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
