---
title: "Procedura: Personalizzare un'SharePoint funzionalità | Microsoft Docs"
description: Personalizzare SharePoint funzionalità in Visual Studio. Progettazione funzionalità viene aperto quando si aggiunge una nuova funzionalità in Esplora soluzioni o SharePoint Esplora pacchetti.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7f4df055447221d563d4725f2a49ccb826b23002
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093034"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Procedura: Personalizzare una SharePoint funzionalità
  È possibile creare e personalizzare SharePoint funzionalità usando Progettazione funzionalità in Visual Studio. Ad esempio, è possibile impostare l'ambito della funzionalità e aggiungere altre funzionalità come dipendenze. Per impostazione predefinita, Progettazione funzionalità viene aperto quando si aggiunge una nuova funzionalità in Esplora soluzioni o in Esplora SharePoint pacchetti.

## <a name="opening-the-feature-designer"></a>Apertura di Progettazione funzionalità
 È possibile aggiungere o rimuovere SharePoint di progetto a una funzionalità usando Progettazione funzionalità.

#### <a name="to-open-the-feature-designer"></a>Per aprire Progettazione funzionalità

1. In **Esplora soluzioni** espandere **Funzionalità**.

2. Fare doppio clic *sull'elemento Feature1* oppure aprire il menu di scelta rapida per la *voce Feature1* e quindi **scegliere Progettazione visualizzazioni**.

## <a name="view-the-packaged-manifest-file"></a>Visualizzare il file manifesto in pacchetto
 È possibile usare Progettazione funzionalità per modificare e generare il file manifesto in pacchetto per la funzionalità (*feature.xml*). È quindi possibile visualizzare il codice XML per questo file in Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Per visualizzare il file manifesto in pacchetto

1. In **Progettazione funzionalità** scegliere la **scheda** Manifesto .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto in pacchetto usando Esplora soluzioni

1. In **Esplora soluzioni** scegliere l'icona **Mostra tutti i** file.

2. Espandere Funzionalità, FeatureName, FeatureName.feature e quindi aprire il file *\<FeatureName>.Template.xml.*

    > [!NOTE]
    > Quando si apre il file XML del manifesto del modello di funzionalità, i file vengono convalidati automaticamente e gli avvisi visualizzati nella finestra Elenco errori possono essere ignorati.

## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto
 È possibile modificare il codice XML per il file manifesto della funzionalità nel riquadro Visual Studio editor XML o modello di manifesto. Tutte le modifiche apportate al codice XML vengono unite nel file manifesto in pacchetto per la funzionalità. Ad esempio, è possibile modificare il modello di manifesto per personalizzare una proprietà Feature.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto tramite l'editor XML

1. In **Progettazione funzionalità** scegliere la scheda **Manifesto,** espandere il **nodo Opzioni** di modifica e quindi scegliere il collegamento **Apri nell'editor XML.**

     Le modifiche al codice XML vengono unite nel file manifesto in pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto usando il riquadro Modello di manifesto

1. In **Progettazione funzionalità** scegliere la scheda  **Manifesto** , espandere il nodo Opzioni di modifica e quindi modificare il codice XML visualizzato nel riquadro Modello manifesto .

     Le modifiche al codice XML vengono visualizzate nel **riquadro Anteprima del manifesto in** pacchetto.

## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivere il file manifesto in pacchetto
 È possibile disabilitare Progettazione funzionalità e creare il file *feature.xml* manualmente. La prima volta che si esegue questa procedura, le impostazioni correnti in Progettazione funzionalità vengono salvate nel file XML del modello di funzionalità. È quindi possibile modificare o sovrascrivere il codice XML.

> [!NOTE]
> Se si aggiungono o rimuovono SharePoint di progetto nel file XML mentre Progettazione funzionalità è disabilitato, questi elementi di progetto non vengono in pacchetto.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto in pacchetto disabilitando la finestra di progettazione

1. In **Progettazione funzionalità** scegliere la **scheda** Manifesto .

2. Espandere il **nodo Opzioni** di modifica , scegliere il collegamento Sovrascrivi xml generato e modifica manifesto nell'editor **XML** e quindi scegliere **il pulsante** Sì .

     Il modello viene aggiornato con il file manifesto in pacchetto corrente.

## <a name="enable-the-feature-designer"></a>Abilitare Progettazione funzionalità
 È possibile ri abilitare Progettazione funzionalità per personalizzare il *feature.xml* file.

#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione

1. In **Progettazione funzionalità scegliere** rimuovi le **modifiche del manifesto e ribilita** il collegamento della finestra di progettazione, quindi scegliere **il pulsante** Sì.

2. Il modello viene aggiornato con il testo originale e tutte le modifiche apportate al codice XML andranno perse.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
