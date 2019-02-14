---
title: 'Procedura: Problemi relativi ai modelli | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb2c708bfb6bfafe90b548ad2826e0cf11882a3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793206"
---
# <a name="how-to-troubleshoot-templates"></a>Procedura: risolvere i problemi relativi ai modelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se un modello non viene caricato nell'ambiente di sviluppo, sono disponibili diversi metodi per individuare il problema.  
  
## <a name="validating-the-vstemplate-file"></a>Convalida del file con estensione vstemplate  
 Se il file con estensione vstemplate in un modello non rispetta lo schema di modello [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile che il modello non venga visualizzato nella finestra di dialogo **Nuovo progetto**.  
  
#### <a name="to-validate-the-vstemplate-file"></a>Per convalidare il file con estensione vstemplate  
  
1.  Individuare il file ZIP che contiene il modello.  
  
2.  Estrarre il file ZIP.  
  
3.  Nel menu **File** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fare clic su **Apri** e quindi su **File**.  
  
4.  Selezionare il file con estensione vstemplate per il modello e fare clic su **Apri**.  
  
5.  Verificare che il codice XML del file con estensione vstemplate rispetti lo schema di modello [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni sullo schema del file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Per ottenere il supporto IntelliSense durante la creazione del file con estensione `xmlns`vstemplate`VSTemplate`, aggiungere un attributo http://schemas.microsoft.com/developer/vstemplate/2005 all'elemento  e assegnare all'attributo il valore .  
  
6.  Salvare e chiudere il file vstemplate.  
  
7.  Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e selezionare **Invia a** e fare clic su **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.  
  
8.  Inserire il nuovo file con estensione zip nella stessa directory del file con estensione zip precedente.  
  
9. Eliminare i file di modello estratti e il vecchio file di modello ZIP.  
  
## <a name="monitoring-the-event-log"></a>Monitoraggio del log eventi  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] registra gli errori rilevati durante l'elaborazione dei file con estensione zip dei modelli. Se un modello non viene visualizzato nella finestra di dialogo **Nuovo progetto** come previsto, è possibile usare il **Visualizzatore eventi** per risolvere il problema.  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>Per individuare gli errori dei modelli nel Visualizzatore eventi  
  
1.  In Windows fare clic sul pulsante **Start**, scegliere **Pannello di controllo**, fare doppio clic su **Strumenti di amministrazione** e quindi fare doppio clic su **Visualizzatore eventi**.  
  
2.  Nel riquadro sinistro fare clic su **Applicazione**.  
  
3.  Cercare gli eventi con il valore **Origine** uguale a `Visual Studio - VsTemplate`.  
  
4.  Fare doppio clic su un evento del modello per visualizzare l'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
