---
title: 'Procedura: Personalizzare un pacchetto SharePoint soluzione | Microsoft Docs'
description: Usare Progettazione pacchetti per creare e personalizzare un pacchetto SharePoint soluzione (con estensione wsp). Visualizzare o sovrascrivere il file manifesto in pacchetto. Modificare il modello di manifesto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: ca3341b252f94a4415904744840f24cb05b56b56
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636899"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Procedura: Personalizzare un pacchetto SharePoint soluzione
  È possibile usare Progettazione pacchetti per creare e personalizzare un pacchetto (*.wsp*). Ad esempio, è possibile aggiungere SharePoint di progetto e funzionalità, specificare se il server Web viene reimpostato quando viene distribuita la soluzione e impostare il tipo di server di distribuzione.

## <a name="open-the-package-designer"></a>Aprire Progettazione pacchetti

#### <a name="to-open-the-package-designer"></a>Per aprire Progettazione pacchetti

- In **Esplora soluzioni** fare doppio clic su **Pacchetto** oppure scegliere Progettazione visualizzazioni **dal** menu di scelta rapida per **Pacchetto**.

## <a name="view-the-packaged-manifestffile"></a>Visualizzare il file manifesto in pacchettofFile
 È possibile usare Progettazione pacchetti per modificare e generare il file manifesto in pacchetto. È quindi possibile visualizzare il codice XML per questo file in Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Per visualizzare il file di origine XML

1. In **Progettazione pacchetti** scegliere **Manifesto.**

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto in pacchetto usando Esplora soluzioni

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

2. Espandere Pacchetto, espandere Package.package e quindi aprire il file *Package.Template.xml* file.

    > [!NOTE]
    > Quando si apre il file XML del manifesto per il modello di pacchetto, i file vengono convalidati automaticamente ed è possibile ignorare gli avvisi visualizzati nella finestra Elenco errori .

## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto
 È possibile modificare il codice XML per il file manifesto in pacchetto nell'editor XML Visual Studio o nel riquadro Modello manifesto . Tutte le modifiche apportate al codice XML vengono unite nel file manifesto del pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto tramite l'editor XML

1. In **Progettazione pacchetti** scegliere la scheda **Manifesto,** espandere il **nodo Opzioni** di modifica e quindi scegliere il collegamento **Apri nell'editor XML.**

     Le modifiche al codice XML vengono unite nel file manifesto in pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto usando il riquadro Modello di manifesto

1. In **Progettazione pacchetti** scegliere la scheda  **Manifesto** , espandere il nodo Opzioni di modifica e quindi modificare il codice XML visualizzato nel riquadro Modello manifesto .

     Le modifiche al codice XML vengono visualizzate nel **riquadro Anteprima del manifesto in** pacchetto.

## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivere il file manifesto in pacchetto
 È possibile disabilitare Progettazione pacchetti e creare il file *manifest.xml* manualmente. La prima volta che si esegue questa procedura, le impostazioni correnti in Progettazione pacchetti vengono salvate nel file XML del modello di pacchetto. È quindi possibile modificare o sovrascrivere il codice XML.

> [!NOTE]
> Se si aggiungono o rimuovono SharePoint elementi di progetto e funzionalità nel file XML mentre Progettazione pacchetti è disabilitato, questi elementi di progetto e funzionalità non vengono in pacchetto.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto in pacchetto disabilitando la finestra di progettazione

1. In **Progettazione pacchetti** scegliere la **scheda** Manifesto .

2. Espandere il **nodo Opzioni** di modifica , scegliere il collegamento Sovrascrivi xml generato e modifica manifesto nell'editor **XML** e quindi scegliere **il pulsante** Sì .

     Il modello viene aggiornato con il file manifesto in pacchetto corrente.

## <a name="enable-the-package-designer"></a>Abilitare Progettazione pacchetti
 È possibile ri abilitare Progettazione pacchetti per personalizzare il *manifest.xml* file.

#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione

1. In **Progettazione pacchetti** scegliere rimuovi le **modifiche del manifesto e ribilita** il collegamento della finestra di progettazione, quindi scegliere **il pulsante** Sì.

     Il modello viene aggiornato con il testo originale e tutte le modifiche apportate al codice XML andranno perse.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
