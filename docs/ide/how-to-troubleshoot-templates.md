---
title: Risolvere i problemi del modello di progetto e del caricamento dei modelli di elemento di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6d9a73cd45a0e497fb2ecc0f4b4697071e3b37
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-troubleshoot-templates"></a>Procedura: Risolvere i problemi relativi ai modelli

Se un modello non viene caricato nell'ambiente di sviluppo, sono disponibili diversi metodi per individuare il problema.

## <a name="validate-the-vstemplate-file"></a>Convalidare il file con estensione vstemplate

Se il file con estensione vstemplate di un modello non rispetta lo schema di modello di Visual Studio, è possibile che il modello non venga visualizzato nella finestra di dialogo **Nuovo progetto**.

### <a name="to-validate-the-vstemplate-file"></a>Per convalidare il file con estensione vstemplate

1. Individuare il file ZIP che contiene il modello.

1. Estrarre il file ZIP.

1. Nel menu **File** di Visual Studio scegliere **Apri** > **File**.

1. Selezionare il file con estensione vstemplate per il modello e fare clic su **Apri**.

1. Verificare che il codice XML del file con estensione vstemplate rispetti lo schema del modello. Per altre informazioni sullo schema del file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Per ottenere il supporto IntelliSense durante la creazione del file con estensione vstemplate, aggiungere un attributo `xmlns` all'elemento `VSTemplate` e assegnare all'attributo il valore http://schemas.microsoft.com/developer/vstemplate/2005.

1. Salvare e chiudere il file vstemplate.

1. Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e selezionare **Invia a** > **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.

1. Inserire il nuovo file con estensione zip nella stessa directory del file con estensione zip precedente.

1. Eliminare i file di modello estratti e il vecchio file di modello ZIP.

## <a name="monitor-the-event-log"></a>Monitorare il registro eventi

In Visual Studio vengono registrati gli errori rilevati durante l'elaborazione dei file con estensione zip dei modelli. Se un modello non viene visualizzato come previsto nella finestra di dialogo **Nuovo progetto**, è possibile usare il **Visualizzatore eventi** per risolvere il problema.

### <a name="to-locate-template-errors-in-event-viewer"></a>Per individuare gli errori dei modelli nel Visualizzatore eventi

1. Dal menu **Start** di Windows scegliere **Strumenti di amministrazione** > **Visualizzatore eventi**.

1. Nel riquadro a sinistra scegliere **Registri di Windows** > **Applicazione**.

1. Cercare gli eventi con il valore **Origine** uguale a `Visual Studio - VsTemplate`.

1. Per visualizzare un errore fare doppio clic su un evento del modello.

## <a name="enable-diagnostic-logging"></a>Abilitare la registrazione diagnostica

È possibile abilitare la registrazione diagnostica per l'individuazione dei modelli seguendo la procedura in [Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md)  
[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  
[Riferimento allo schema di modello](../extensibility/visual-studio-template-schema-reference.md)