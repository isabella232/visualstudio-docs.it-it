---
title: Creazione SharePoint funzionalità | Microsoft Docs
description: Creare una funzionalità SharePoint per raggruppare elementi SharePoint progetto correlati per semplificare la distribuzione. Aggiungere funzionalità alla soluzione SharePoint personalizzata. Usare la finestra di progettazione delle funzionalità.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4eaf4a9541834215c0c66aed7bb9271faa79a1e3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635651"
---
# <a name="create-sharepoint-features"></a>Creare SharePoint funzionalità
  È possibile usare una funzionalità SharePoint per raggruppare gli elementi SharePoint progetto per semplificare la distribuzione. È possibile creare funzionalità, impostare ambiti e contrassegnare altre funzionalità come dipendenze usando progettazione SharePoint funzionalità. La finestra di progettazione genera anche un manifesto, ovvero un file XML che descrive ogni funzionalità.

## <a name="add-features-to-the-sharepoint-solution"></a>Aggiungere funzionalità alla soluzione SharePoint
 È possibile aggiungere una funzionalità alla soluzione SharePoint usando Esplora soluzioni o Packaging Explorer. È possibile usare uno dei metodi seguenti per aggiungere una funzionalità.

- In **Esplora soluzioni** aprire il menu di scelta rapida per **Funzionalità** e quindi scegliere **Aggiungi funzionalità.**

- In **Packaging Explorer** aprire il menu di scelta rapida per il pacchetto e quindi scegliere Aggiungi **funzionalità.**

## <a name="using-the-feature-designer"></a>Uso della finestra di progettazione delle funzionalità
 Una SharePoint può contenere una o più funzionalità SharePoint, raggruppate nel nodo Funzionalità in Esplora soluzioni. Ogni funzionalità ha una propria **finestra di progettazione delle** funzionalità che è possibile usare per personalizzare le proprietà della funzionalità. Per altre informazioni, vedere [Procedura: Personalizzare una SharePoint funzionalità](../sharepoint/how-to-customize-a-sharepoint-feature.md). Per distinguere le funzionalità l'una dall'altra, è possibile configurare le proprietà della funzionalità, ad esempio titolo, descrizione, versione e ambito.

### <a name="feature-designer-options"></a>Opzioni di Progettazione funzionalità
 Dopo aver creato una funzionalità, è possibile usare Feature Designer per personalizzarla.

 Nella tabella seguente vengono descritte le proprietà delle funzionalità visualizzate in Progettazione funzionalità.

|Proprietà|Descrizione|
|--------------|-----------------|
|Titolo|facoltativo. Il titolo predefinito della funzionalità è impostato su *SolutionName* *FeatureName*.|
|Descrizione|Facoltativa. Descrizione della funzionalità SharePoint funzionalità.|
|Ambito|Obbligatorio. Se una funzionalità viene creata usando **Esplora soluzioni**, l'ambito è impostato su Web per impostazione predefinita.<br /><br /> - Farm: attivare una funzionalità per un'intera server farm.<br /><br /> - Sito: attivare una funzionalità per tutti i siti Web in una raccolta siti.<br /><br /> - Web: attivare una funzionalità per un sito Web specifico.<br /><br /> - WebApplication: attiva una funzionalità per tutti i siti Web in un'applicazione Web.|
|Elementi nella soluzione|Tutti SharePoint elementi che possono essere aggiunti alla funzionalità.|
|Elementi nella funzionalità|Il SharePoint elementi del progetto che sono stati aggiunti alla funzionalità.|

## <a name="add-and-remove-sharepoint-project-items"></a>Aggiungere e rimuovere elementi SharePoint progetto
 È possibile selezionare gli SharePoint di progetto a cui si vuole aggiungere una funzionalità SharePoint per la distribuzione. Usare Progettazione **funzionalità per** aggiungere e rimuovere elementi in Funzionalità e visualizzare il manifesto della funzionalità. Per altre informazioni, [vedere Procedura: Aggiungere e rimuovere elementi in SharePoint funzionalità.](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)

## <a name="add-feature-dependencies"></a>Aggiungere dipendenze di funzionalità
 È possibile configurare il manifesto della funzionalità in modo che il server SharePoint attivi determinate funzionalità prima dell'attivazione della funzionalità. Ad esempio, se la funzionalità di SharePoint dipende da altre funzionalità per funzionalità o dati, il server SharePoint può prima provare ad attivare una delle funzionalità da cui dipende la funzionalità. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere dipendenze di funzionalità.](../sharepoint/how-to-add-and-remove-feature-dependencies.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare una funzionalità SharePoint personalizzata](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi in SharePoint funzionalità](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Procedura: Aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
