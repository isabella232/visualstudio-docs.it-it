---
title: Aggiornare i modelli di elemento del progetto esistente
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591359"
---
# <a name="how-to-update-existing-templates"></a>Procedura: Aggiornare modelli esistenti

Dopo aver creato un modello e compresso i file in un file con estensione *zip*, può essere necessario modificare il modello. L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.

## <a name="use-the-export-template-wizard"></a>Usare l'Esportazione guidata modelli

In Visual Studio è disponibile l'**Esportazione guidata modelli** che può essere usata per aggiornare un modello esistente:

1. Scegliere **File** > **nuovo** > **progetto** dalla barra dei menu.

1. Selezionare il modello da aggiornare e procedere con i passaggi necessari per creare il nuovo progetto.

1. Modificare il progetto in Visual Studio. Ad esempio, modificare il tipo di output o aggiungere un nuovo file al progetto.

1. Scegliere **Esporta modello**dal menu **Progetto** .

    Verrà **visualizzata l'Esportazione guidata modelli.**

1. Seguire le istruzioni della procedura guidata per esportare il modello come file con estensione *zip*.

1. (Facoltativo) Inserire il file *ZIP* nella directory seguente: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*. È necessario eseguire questo passaggio se non è stata selezionata l'opzione **Importa automaticamente il modello in Visual Studio** nell'**Esportazione guidata modelli**.

1. Eliminare il file di modello precedente con estensione *zip*.

## <a name="manually-update-an-existing-template"></a>Aggiornare manualmente un modello esistente

È possibile aggiornare un modello esistente senza usare l'**Esportazione guidata modelli** modificando i file inclusi nel file con estensione *zip* compresso.

### <a name="to-manually-update-an-existing-template"></a>Per aggiornare manualmente un modello esistente

1. Individuare il file con estensione *zip* che contiene il modello. I modelli di progetto utente sono situati in *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

1. Estrarre il file *.zip.*

1. Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.

1. Aprire, modificare e salvare il file XML con estensione *vstemplate* per gestire il nuovo comportamento o i nuovi file.

    Per altre informazioni sullo schema *vstemplate*, vedere [Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md). Per ulteriori informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [Parametri del modello](../ide/template-parameters.md).

1. Selezionare i file nel modello e dal menu di scelta rapida o del pulsante destro del mouse, quindi scegliere **Invia a** > **cartella compressa (compressa).**

    I file selezionati vengono compressi in un file *.zip.*

1. Inserire il nuovo file *.zip* nella stessa directory del vecchio file *.zip.*

1. Eliminare i file di modello estratti e il file di modello precedente con estensione *zip*.

## <a name="see-also"></a>Vedere anche

- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Creare modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Parametri del modello](../ide/template-parameters.md)
