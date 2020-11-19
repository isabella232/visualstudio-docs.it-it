---
title: 'Procedura: personalizzare una funzionalità di SharePoint | Microsoft Docs'
description: Personalizzare le funzionalità di SharePoint in Visual Studio. La finestra Progettazione funzionalità viene visualizzata quando si aggiunge una nuova funzionalità in Esplora soluzioni o in SharePoint Package Explorer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4846d79af7a031970e8870626f88450e8a3e647
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903663"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Procedura: personalizzare una funzionalità di SharePoint
  È possibile creare e personalizzare le funzionalità di SharePoint usando progettazione funzionalità in Visual Studio. Ad esempio, è possibile impostare l'ambito della funzionalità e aggiungere altre funzionalità come dipendenze. Per impostazione predefinita, la finestra di progettazione funzionalità viene aperta quando si aggiunge una nuova funzionalità in Esplora soluzioni o in SharePoint Package Explorer.

## <a name="opening-the-feature-designer"></a>Apertura di progettazione funzionalità
 È possibile aggiungere o rimuovere elementi di progetto SharePoint in una funzionalità utilizzando Progettazione funzionalità.

#### <a name="to-open-the-feature-designer"></a>Per aprire Progettazione funzionalità

1. In **Esplora soluzioni** espandere **funzionalità**.

2. Fare doppio clic sull'elemento *Feature1* o aprire il menu di scelta rapida per l'elemento *Feature1* , quindi scegliere **Visualizza finestra di progettazione**.

## <a name="view-the-packaged-manifest-file"></a>Visualizzare il file manifesto del pacchetto
 È possibile utilizzare la finestra Progettazione funzionalità per modificare e generare il file manifesto del pacchetto per la funzionalità (*feature.xml*). Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Per visualizzare il file manifesto del pacchetto

1. In **Progettazione funzionalità** scegliere la scheda **manifesto** .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto del pacchetto tramite Esplora soluzioni

1. In **Esplora soluzioni** scegliere l'icona **Mostra tutti i file** .

2. Espandere funzionalità, espandere FeatureName, espandere FeatureName. feature, quindi aprire il file di *\<FeatureName>.Template.xml* .

    > [!NOTE]
    > Quando si apre il file XML del manifesto del modello di funzionalità, i file vengono convalidati automaticamente e gli avvisi visualizzati nella finestra di Elenco errori possono essere ignorati.

## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto
 È possibile modificare il codice XML per il file manifesto della funzionalità nell'editor XML di Visual Studio o nel riquadro modello di manifesto. Qualsiasi modifica apportata al codice XML viene unita nel file manifesto del pacchetto per la funzionalità. Ad esempio, potrebbe essere necessario modificare il modello di manifesto per personalizzare una proprietà della funzionalità.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto mediante l'editor XML

1. In **Progettazione funzionalità** scegliere la scheda **manifesto** , espandere il nodo **Opzioni di modifica** , quindi scegliere il collegamento **Apri in editor XML** .

     Le modifiche apportate al codice XML vengono unite nel file manifesto del pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto utilizzando il riquadro modello manifesto

1. In **Progettazione funzionalità** scegliere la scheda **manifesto** , espandere il nodo **Opzioni di modifica** e quindi modificare il codice XML visualizzato nel riquadro modello di manifesto.

     Le modifiche apportate al codice XML vengono visualizzate nell' **anteprima del riquadro manifesto del pacchetto** .

## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivi il file manifesto del pacchetto
 È possibile disabilitare la finestra Progettazione funzionalità e creare manualmente il file di *feature.xml* . La prima volta che si esegue questa procedura, le impostazioni correnti in progettazione funzionalità vengono salvate nel file XML del modello di funzionalità. Quindi, è possibile modificare o sovrascrivere il codice XML.

> [!NOTE]
> Se si aggiungono o rimuovono elementi di progetto SharePoint nel file XML mentre la finestra Progettazione funzionalità è disabilitata, questi elementi del progetto non vengono inclusi nel pacchetto.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto del pacchetto disabilitando la finestra di progettazione

1. In **Progettazione funzionalità** scegliere la scheda **manifesto** .

2. Espandere il nodo **Opzioni di modifica** , scegliere il collegamento **Sovrascrivi XML e modifica manifesto nel collegamento dell'editor XML** , quindi scegliere il pulsante **Sì** .

     Il modello viene aggiornato con il file manifesto del pacchetto corrente.

## <a name="enable-the-feature-designer"></a>Abilitare la finestra di progettazione delle funzionalità
 È possibile riabilitare la finestra Progettazione funzionalità per personalizzare il file di *feature.xml* .

#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione

1. In **Progettazione funzionalità** scegliere il collegamento Annulla **modifiche manifesto e riattivare la finestra di progettazione** , quindi scegliere il pulsante **Sì** .

2. Il modello viene aggiornato con il testo originale e tutte le modifiche apportate al codice XML vengono perse.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
