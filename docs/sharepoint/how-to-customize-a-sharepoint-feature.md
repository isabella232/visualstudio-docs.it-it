---
title: 'Procedura: personalizzare una funzionalità di SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be9ba70bb94e743a788db11b55c188275bcad64
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118897"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Procedura: personalizzare una funzionalità SharePoint
  È possibile creare e personalizzare le funzionalità di SharePoint usando la finestra di progettazione di funzionalità in Visual Studio. Ad esempio, è possibile impostare l'ambito di funzionalità e aggiungere altre funzionalità come dipendenze. Per impostazione predefinita, la finestra di progettazione di funzionalità viene aperto quando si aggiunge una nuova funzionalità in Esplora soluzioni o Esplora pacchetti di SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Aprire la finestra di progettazione di funzionalità  
 È possibile aggiungere o rimuovere elementi del progetto SharePoint a una funzionalità tramite la finestra di progettazione di funzionalità.  
  
#### <a name="to-open-the-feature-designer"></a>Per aprire la finestra di progettazione di funzionalità
  
1.  Nelle **Esplora soluzioni**, espandere **funzionalità**.  
  
2.  Fare doppio clic sui *Feature1* elemento n o aprire il menu di scelta rapida per il *Feature1* elemento e quindi scegliere **Progettazione viste**.  
  
## <a name="view-the-packaged-manifest-file"></a>Visualizzare il file manifesto nel pacchetto  
 È possibile usare la finestra di progettazione di funzionalità per modificare e generare il file manifesto nel pacchetto per la funzionalità (*feature. XML*). Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Per visualizzare il file manifesto nel pacchetto  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto nel pacchetto tramite Esplora soluzioni  
  
1.  Nelle **Esplora soluzioni**, scegliere il **Mostra tutti i file** icona.  
  
2.  Espandere le funzionalità espandere FeatureName, espandere FeatureName.feature e quindi aprire il  *\<FeatureName >. Template* file.  
  
    > [!NOTE]  
    >  Quando si apre il file XML manifesto di funzionalità modello, i file vengono convalidati automaticamente e possono essere ignorati gli avvisi visualizzati nella finestra Elenco errori.  
  
## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto  
 È possibile modificare il codice XML per il file manifesto della funzionalità nell'Editor XML di Visual Studio o nel riquadro modello di manifesto. Tutte le modifiche al codice XML viene unito al file manifesto nel pacchetto per la funzionalità. Ad esempio, è possibile modificare il modello di manifesto per personalizzare una proprietà della funzionalità.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto usando l'Editor XML  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda, quindi espandere il **opzioni di modifica** nodo e quindi scegliere il **aperto nell'Editor XML** collegamento.  
  
     Le modifiche al codice XML vengono unite nel file manifesto nel pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto usando il riquadro modello di manifesto  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda, quindi espandere il **opzioni di modifica** nodo e quindi modificare il codice XML che viene visualizzato nel riquadro modello di manifesto.  
  
     Le modifiche al codice XML visualizzato nei **Preview del manifesto nel pacchetto** riquadro.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivere il file manifesto nel pacchetto  
 È possibile disabilitare la finestra di progettazione di funzionalità e creare il *feature. XML* file manualmente. La prima volta che si esegue questa procedura, vengono salvate le impostazioni correnti nella finestra di progettazione di funzionalità al file XML del modello di funzione. Quindi, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiunge o rimuove elementi di progetto SharePoint nel file XML, mentre la finestra di progettazione di funzionalità è disabilitata, questi elementi di progetto non sono inclusi nel pacchetto.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto, disabilitare la finestra di progettazione  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda.  
  
2.  Espandere la **opzioni di modifica** nodo, scegliere il **Sovrascrivi XML e modifica manifesto generato nell'editor XML** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il file manifesto nel pacchetto corrente.  
  
## <a name="enable-the-feature-designer"></a>Abilitare la finestra di progettazione di funzionalità  
 È possibile abilitare nuovamente la finestra di progettazione di funzionalità per personalizzare il *feature. XML* file.  
  
#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione  
  
1.  Nel **Progettazione funzionalità**, scegliere il **variabile Discard modifiche al manifesti e abilitare di nuovo la finestra di progettazione** collegamento e quindi scegliere il **Sì** pulsante.  
  
2.  Il modello viene aggiornato con il testo originale e le modifiche al codice XML vengono perse.  
  
## <a name="see-also"></a>Vedere anche
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
