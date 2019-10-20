---
title: 'Procedura: Risolvere i problemi relativi ai modelli | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: acee84f582f2d6b8e2905e50db352cde794b73e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670607"
---
# <a name="how-to-troubleshoot-templates"></a>Procedura: risolvere i problemi relativi ai modelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se un modello non viene caricato nell'ambiente di sviluppo, sono disponibili diversi metodi per individuare il problema.

## <a name="validating-the-vstemplate-file"></a>Convalida del file con estensione vstemplate
 Se il file con estensione vstemplate in un modello non rispetta lo schema di modello [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile che il modello non venga visualizzato nella finestra di dialogo **Nuovo progetto**.

#### <a name="to-validate-the-vstemplate-file"></a>Per convalidare il file con estensione vstemplate

1. Individuare il file ZIP che contiene il modello.

2. Estrarre il file ZIP.

3. Nel menu **File** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fare clic su **Apri** e quindi su **File**.

4. Selezionare il file con estensione vstemplate per il modello e fare clic su **Apri**.

5. Verificare che il codice XML del file con estensione vstemplate rispetti lo schema di modello [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni sullo schema del file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Per ottenere il supporto IntelliSense durante la creazione del file con estensione vstemplate, aggiungere un attributo `xmlns` all'elemento `VSTemplate` e assegnare all'attributo il valore http://schemas.microsoft.com/developer/vstemplate/2005.

6. Salvare e chiudere il file vstemplate.

7. Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e selezionare **Invia a** e fare clic su **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.

8. Inserire il nuovo file con estensione zip nella stessa directory del file con estensione zip precedente.

9. Eliminare i file di modello estratti e il vecchio file di modello ZIP.

## <a name="monitoring-the-event-log"></a>Monitoraggio del log eventi
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] registra gli errori rilevati durante l'elaborazione dei file con estensione zip dei modelli. Se un modello non viene visualizzato nella finestra di dialogo **Nuovo progetto** come previsto, è possibile usare il **Visualizzatore eventi** per risolvere il problema.

#### <a name="to-locate-template-errors-in-event-viewer"></a>Per individuare gli errori dei modelli nel Visualizzatore eventi

1. In Windows fare clic sul pulsante **Start**, scegliere **Pannello di controllo**, fare doppio clic su **Strumenti di amministrazione** e quindi fare doppio clic su **Visualizzatore eventi**.

2. Nel riquadro sinistro fare clic su **Applicazione**.

3. Cercare gli eventi con il valore **Origine** uguale a `Visual Studio - VsTemplate`.

4. Fare doppio clic su un evento del modello per visualizzare l'errore.

## <a name="see-also"></a>Vedere anche
 [Personalizzazione dei modelli](../ide/customizing-project-and-item-templates.md) [creazione di progetti e modelli di elemento](../ide/creating-project-and-item-templates.md) [riferimenti allo schema](../extensibility/visual-studio-template-schema-reference.md) dei modelli di Visual Studio
