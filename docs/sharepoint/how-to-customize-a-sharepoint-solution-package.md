---
title: 'Procedura: Personalizzare un pacchetto della soluzione di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85140f8d85c90d2b58df10a63f50c117e10eb8bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835396"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Procedura: Personalizzare un pacchetto della soluzione SharePoint
  È possibile usare la finestra di progettazione del pacchetto per creare e personalizzare un pacchetto (*wsp*). Ad esempio, è possibile aggiungere elementi di progetto SharePoint e le funzionalità, specificare se il server Web viene reimpostato quando viene distribuita la soluzione e impostare il tipo di server di distribuzione.  
  
## <a name="open-the-package-designer"></a>Aprire la finestra di progettazione del pacchetto  
  
#### <a name="to-open-the-package-designer"></a>Per aprire la finestra di progettazione del pacchetto
  
-   Nelle **Esplora soluzioni**, fare doppio clic su **pacchetto**, oppure scegliere **Visualizza finestra di progettazione** nel menu di scelta rapida per **pacchetto**.  
  
## <a name="view-the-packaged-manifestffile"></a>Visualizzare il manifestfFile nel pacchetto  
 È possibile utilizzare la finestra di progettazione del pacchetto per modificare e generare il file manifesto nel pacchetto. Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Per visualizzare il file di origine XML  
  
1.  Nel **Progettazione pacchetti**, scegliere **manifesto**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto nel pacchetto tramite Esplora soluzioni  
  
1.  In **Esplora soluzioni** scegliere **Mostra tutti i file**.  
  
2.  Pacchetto espandere, espandere package. package e quindi aprire il *Package.Template.xml* file.  
  
    > [!NOTE]  
    >  Quando si apre il file manifesto XML per il modello di pacchetto, i file vengono convalidati automaticamente, ed è possibile ignorare gli avvisi visualizzati nella finestra Elenco errori.  
  
## <a name="change-the-manifest-template"></a>Modificare il modello di manifesto  
 È possibile modificare il codice XML per il file manifesto nel pacchetto nell'Editor XML di Visual Studio o nel riquadro modello di manifesto. Tutte le modifiche al codice XML vengono unite nel file manifesto nel pacchetto per il pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto usando l'Editor XML  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda, quindi espandere il **opzioni di modifica** nodo e quindi scegliere il **aperto nell'Editor XML** collegamento.  
  
     Le modifiche al codice XML vengono unite nel file manifesto nel pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto usando il riquadro modello di manifesto  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda, quindi espandere il **opzioni di modifica** nodo e quindi modificare il codice XML che viene visualizzato nel riquadro modello di manifesto.  
  
     Le modifiche al codice XML visualizzato nei **Preview del manifesto nel pacchetto** riquadro.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Sovrascrivere il file manifesto nel pacchetto  
 È possibile disabilitare la finestra di progettazione pacchetti e creare il *manifest* file manualmente. La prima volta che si esegue questa procedura, le impostazioni correnti nella finestra di progettazione pacchetti vengono salvate al file XML del modello di pacchetto. Quindi, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiunge o rimuove elementi di progetto SharePoint e le funzionalità nel file XML, mentre la finestra di progettazione del pacchetto è disabilitato, non prevedono questi elementi di progetto e le funzionalità.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto, disabilitare la finestra di progettazione  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda.  
  
2.  Espandere la **opzioni di modifica** nodo, scegliere il **Sovrascrivi XML e modifica manifesto generato nell'editor XML** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il file manifesto nel pacchetto corrente.  
  
## <a name="enable-the-package-designer"></a>Abilitare la finestra di progettazione del pacchetto  
 È possibile riabilitare la progettazione di pacchetti per personalizzare il *manifest* file.  
  
#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione  
  
1.  Nel **Progettazione pacchetti**, scegliere il **variabile Discard modifiche al manifesti e abilitare di nuovo la finestra di progettazione** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il testo originale e le modifiche al codice XML vengono perse.  
  
## <a name="see-also"></a>Vedere anche
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
