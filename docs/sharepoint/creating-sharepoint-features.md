---
title: Creazione di funzionalità SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051317"
---
# <a name="create-sharepoint-features"></a>Creare funzionalità di SharePoint
  È possibile utilizzare una funzionalità di SharePoint per raggruppare gli elementi di progetto di SharePoint correlati per facilitare la distribuzione. È possibile creare funzionalità imposta ambiti di e contrassegnare altre funzionalità come dipendenze utilizzando la finestra di progettazione di funzionalità di SharePoint. La finestra di progettazione genera inoltre un manifesto, ovvero un file XML che descrive ogni funzionalità.

## <a name="add-features-to-the-sharepoint-solution"></a>Aggiungere funzionalità alla soluzione di SharePoint
 È possibile aggiungere una funzionalità per la soluzione SharePoint tramite Esplora soluzioni o Esplora pacchetti. È possibile usare uno dei metodi seguenti per aggiungere una funzionalità.

- In **Esplora soluzioni**, aprire il menu di scelta rapida **funzionalità**, quindi scegliere **Aggiungi funzionalità**.

- Nelle **Esplora pacchetti**, aprire il menu di scelta rapida per il pacchetto e quindi scegliere **Aggiungi funzionalità**.

## <a name="using-the-feature-designer"></a>Usando la finestra di progettazione di funzionalità
 Una soluzione di SharePoint può contenere uno o più funzionalità di SharePoint, vengono raggruppati sotto il nodo di funzionalità in Esplora soluzioni. Ogni funzionalità ha il proprio **Progettazione funzionalità** che è possibile usare per personalizzare le proprietà di funzionalità. Per altre informazioni, vedere [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Per distinguere le funzionalità uno da altro, è possibile configurare le proprietà della funzionalità, ad esempio il titolo, descrizione, versione e ambito.

### <a name="feature-designer-options"></a>Opzioni della finestra di progettazione delle funzionalità
 Dopo aver creato una funzionalità, è possibile utilizzare la finestra di progettazione di funzionalità per personalizzarla.

 Nella tabella seguente vengono descritte le proprietà di funzionalità che vengono visualizzate nella finestra di progettazione di funzionalità.

|Proprietà|Descrizione|
|--------------|-----------------|
|Titolo|Facoltativo. Il titolo predefinito della funzionalità è impostato su *SolutionName* *FeatureName*.|
|Descrizione|Facoltativo. La descrizione della funzionalità di SharePoint.|
|Ambito|Obbligatorio. Se una funzionalità viene creata usando **Esplora soluzioni**, l'ambito viene impostato su Web per impostazione predefinita.<br /><br /> -Farm: Attivare una funzionalità per un'intera server farm.<br /><br /> -Sito: Attivare una funzionalità per tutti i siti web in una raccolta siti.<br /><br /> -Web: Attivare una funzionalità per un sito web specifico.<br /><br /> -WebApplication: Attivare una funzionalità per tutti i siti web in un'applicazione web.|
|Elementi nella soluzione|Tutti gli elementi di SharePoint che può essere aggiunto alla funzionalità.|
|Elementi nella funzionalità|Gli elementi di progetto SharePoint che sono state aggiunte alla funzionalità.|

## <a name="add-and-remove-sharepoint-project-items"></a>Aggiungere e rimuovere elementi di progetto SharePoint
 È possibile selezionare gli elementi di progetto SharePoint che si desidera aggiungere una funzionalità di SharePoint per la distribuzione. Usare la **Progettazione funzionalità** per aggiungere e rimuovere elementi alle funzionalità e visualizzare il manifesto della funzionalità. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Aggiungere le dipendenze delle funzionalità
 È possibile configurare il manifesto della funzionalità in modo che il server SharePoint attiva determinate funzionalità prima che la funzionalità viene attivata. Ad esempio, se la funzionalità di SharePoint dipende da altre funzionalità per dati o funzionalità, il server SharePoint prima di tutto possibile provare a attivare le funzionalità che dipende la funzionalità. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Procedura: Aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
