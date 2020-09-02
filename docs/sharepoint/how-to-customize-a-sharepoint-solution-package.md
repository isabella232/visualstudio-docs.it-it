---
title: 'Procedura: personalizzare un pacchetto della soluzione SharePoint | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77b66160d489f711b5588fdcdd024d13769d734f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016875"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Procedura: personalizzare un pacchetto della soluzione SharePoint
  È possibile utilizzare Progettazione pacchetti per creare e personalizzare un pacchetto (con*estensione wsp*). Ad esempio, è possibile aggiungere elementi e funzionalità di progetto SharePoint, specificare se il server Web viene reimpostato al momento della distribuzione della soluzione e impostare il tipo di server di distribuzione.

## <a name="open-the-package-designer"></a>Aprire Progettazione pacchetti

#### <a name="to-open-the-package-designer"></a>Per aprire Progettazione pacchetti

- In **Esplora soluzioni**fare doppio clic su **pacchetto**oppure scegliere **Progettazione viste** dal menu di scelta rapida per il **pacchetto**.

## <a name="view-the-packaged-manifestffile"></a>Visualizzare il manifestfFile in pacchetto
 È possibile utilizzare Progettazione pacchetti per modificare e generare il file manifesto del pacchetto. Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Per visualizzare il file di origine XML

1. In **Progettazione pacchetti**scegliere **manifesto**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto del pacchetto tramite Esplora soluzioni

1. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

2. Espandere pacchetto, espandere Package. Package, quindi aprire il file di *Package.Template.xml* .

    > [!NOTE]
    > Quando si apre il file XML del manifesto per il modello di pacchetto, i file vengono convalidati automaticamente ed è possibile ignorare gli avvisi visualizzati nella finestra di Elenco errori.

## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto
 È possibile modificare il codice XML per il file manifesto del pacchetto nell'editor XML di Visual Studio o nel riquadro modello di manifesto. Qualsiasi modifica apportata al codice XML viene unita nel file manifesto del pacchetto per il pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto mediante l'editor XML

1. In **Progettazione pacchetti**scegliere la scheda **manifesto** , espandere il nodo **Opzioni di modifica** , quindi scegliere il collegamento **Apri in editor XML** .

     Le modifiche apportate al codice XML vengono unite nel file manifesto del pacchetto.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto utilizzando il riquadro modello manifesto

1. In **Progettazione pacchetti**scegliere la scheda **manifesto** , espandere il nodo **Opzioni di modifica** e quindi modificare il codice XML visualizzato nel riquadro modello di manifesto.

     Le modifiche apportate al codice XML vengono visualizzate nell' **anteprima del riquadro manifesto del pacchetto** .

## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivi il file manifesto del pacchetto
 È possibile disabilitare la finestra di progettazione del pacchetto e creare manualmente il file di *manifest.xml* . La prima volta che si esegue questa procedura, le impostazioni correnti nella finestra di progettazione del pacchetto vengono salvate nel file XML del modello di pacchetto. Quindi, è possibile modificare o sovrascrivere il codice XML.

> [!NOTE]
> Se si aggiungono o rimuovono le funzionalità e gli elementi del progetto SharePoint nel file XML mentre la finestra di progettazione dei pacchetti è disabilitata, questi elementi e funzionalità di progetto non sono inclusi nel pacchetto.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto del pacchetto disabilitando la finestra di progettazione

1. In **Progettazione pacchetti**scegliere la scheda **manifesto** .

2. Espandere il nodo **Opzioni di modifica** , scegliere il collegamento **Sovrascrivi XML e modifica manifesto nel collegamento dell'editor XML** , quindi scegliere il pulsante **Sì** .

     Il modello viene aggiornato con il file manifesto del pacchetto corrente.

## <a name="enable-the-package-designer"></a>Abilitare progettazione pacchetti
 È possibile riabilitare la finestra di progettazione dei pacchetti per personalizzare il file di *manifest.xml* .

#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione

1. In **Progettazione pacchetti**scegliere il collegamento Annulla **modifiche manifesto e riattivare la finestra di progettazione** , quindi scegliere il pulsante **Sì** .

     Il modello viene aggiornato con il testo originale e tutte le modifiche apportate al codice XML vengono perse.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
