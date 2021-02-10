---
title: Creazione di funzionalità di SharePoint | Microsoft Docs
description: Creare una funzionalità di SharePoint per raggruppare gli elementi del progetto SharePoint correlati per semplificare la distribuzione. Aggiungere funzionalità alla soluzione SharePoint. Utilizzare la finestra di progettazione delle funzionalità.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949116"
---
# <a name="create-sharepoint-features"></a>Creazione di funzionalità di SharePoint
  È possibile utilizzare una funzionalità di SharePoint per raggruppare gli elementi del progetto SharePoint correlati per semplificare la distribuzione. È possibile creare funzionalità, impostare gli ambiti e contrassegnare altre funzionalità come dipendenze tramite la finestra di progettazione delle funzionalità di SharePoint. La finestra di progettazione genera inoltre un manifesto, ovvero un file XML che descrive ogni funzionalità.

## <a name="add-features-to-the-sharepoint-solution"></a>Aggiungere funzionalità alla soluzione SharePoint
 È possibile aggiungere una funzionalità alla soluzione SharePoint usando Esplora soluzioni o packaging Explorer. Per aggiungere una funzionalità, è possibile utilizzare uno dei metodi seguenti.

- In **Esplora soluzioni** aprire il menu di scelta rapida per **funzionalità**, quindi scegliere **Aggiungi funzionalità**.

- In **Packaging Explorer** aprire il menu di scelta rapida per il pacchetto, quindi scegliere **Aggiungi funzionalità**.

## <a name="using-the-feature-designer"></a>Utilizzo di progettazione funzionalità
 Una soluzione SharePoint può contenere una o più funzionalità di SharePoint, raggruppate sotto il nodo della funzionalità in Esplora soluzioni. Ogni funzionalità dispone di una propria **finestra di progettazione delle funzionalità** che è possibile utilizzare per personalizzare le proprietà della funzionalità. Per altre informazioni, vedere [procedura: personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Per distinguere le funzionalità le une dalle altre, è possibile configurare le proprietà della funzionalità, ad esempio titolo, descrizione, versione e ambito.

### <a name="feature-designer-options"></a>Opzioni di progettazione funzionalità
 Dopo aver creato una funzionalità, è possibile utilizzare la finestra Progettazione funzionalità per personalizzarla.

 Nella tabella seguente vengono descritte le proprietà della funzionalità visualizzate nella finestra di progettazione della funzionalità.

|Proprietà|Descrizione|
|--------------|-----------------|
|Titolo|facoltativo. Il titolo predefinito della funzionalità è impostato su *SolutionName* *FeatureName*.|
|Descrizione|Facoltativa. Descrizione della funzionalità di SharePoint.|
|Ambito|Obbligatorio. Se una funzionalità viene creata tramite **Esplora soluzioni**, l'ambito viene impostato su Web per impostazione predefinita.<br /><br /> -Farm: attiva una funzionalità per un'intera server farm.<br /><br /> -Site: attiva una funzionalità per tutti i siti Web in una raccolta siti.<br /><br /> -Web: attiva una funzionalità per un sito Web specifico.<br /><br /> -WebApplication: attiva una funzionalità per tutti i siti Web in un'applicazione Web.|
|Elementi nella soluzione|Tutti gli elementi di SharePoint che possono essere aggiunti alla funzionalità.|
|Elementi della funzionalità|Elementi del progetto SharePoint aggiunti alla funzionalità.|

## <a name="add-and-remove-sharepoint-project-items"></a>Aggiunta e rimozione di elementi di progetto SharePoint
 È possibile selezionare gli elementi del progetto SharePoint a cui si desidera aggiungere una funzionalità di SharePoint per la distribuzione. Utilizzare **Progettazione funzionalità** per aggiungere e rimuovere elementi alle funzionalità e visualizzare il manifesto della funzionalità. Per altre informazioni, vedere [procedura: aggiungere e rimuovere elementi nelle funzionalità di SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Aggiungere dipendenze di funzionalità
 È possibile configurare il manifesto della funzionalità in modo che il server SharePoint attivi determinate funzionalità prima che la funzionalità venga attivata. Se, ad esempio, la funzionalità di SharePoint dipende da altre funzionalità per la funzionalità o i dati, il server SharePoint può innanzitutto provare ad attivare le funzionalità da cui dipende la funzionalità. Per altre informazioni, vedere [procedura: aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: aggiungere e rimuovere elementi nelle funzionalità di SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Procedura: aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
