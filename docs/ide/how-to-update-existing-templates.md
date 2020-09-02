---
title: Aggiornare i modelli di elemento del progetto esistente
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d5d9726ecbf3cb7c403f682aadb197a26b0dc26b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283918"
---
# <a name="how-to-update-existing-templates"></a>Procedura: Aggiornare modelli esistenti

Dopo aver creato un modello e compresso i file in un file con estensione *zip*, può essere necessario modificare il modello. L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.

## <a name="use-the-export-template-wizard"></a>Usare l'Esportazione guidata modelli

In Visual Studio è disponibile l'**Esportazione guidata modelli** che può essere usata per aggiornare un modello esistente:

1. Scegliere **file**  >  **nuovo**  >  **progetto** dalla barra dei menu.

1. Selezionare il modello da aggiornare e procedere con i passaggi necessari per creare il nuovo progetto.

1. Modificare il progetto in Visual Studio. Ad esempio, modificare il tipo di output o aggiungere un nuovo file al progetto.

1. Scegliere **Esporta modello**dal menu **progetto** .

    Verrà visualizzata l' **esportazione guidata modelli** .

1. Seguire le istruzioni della procedura guidata per esportare il modello come file con estensione *zip*.

1. Opzionale Inserire il file *zip* nella directory seguente: *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates* per renderlo disponibile per la selezione. È necessario eseguire questo passaggio se non è stata selezionata l'opzione **Importa automaticamente il modello in Visual Studio** nell'**Esportazione guidata modelli**.

1. Eliminare il file di modello precedente con estensione *zip*.

## <a name="manually-update-an-existing-template"></a>Aggiornare manualmente un modello esistente

È possibile aggiornare un modello esistente senza usare l'**Esportazione guidata modelli** modificando i file inclusi nel file con estensione *zip* compresso.

### <a name="to-manually-update-an-existing-template"></a>Per aggiornare manualmente un modello esistente

1. Individuare il file con estensione *zip* che contiene il modello. I modelli di progetto utente si trovano in *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*.

1. Estrarre il file *zip* .

1. Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.

1. Aprire, modificare e salvare il file XML con estensione *vstemplate* per gestire il nuovo comportamento o i nuovi file.

    Per altre informazioni sullo schema *vstemplate*, vedere [Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md). Per ulteriori informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [parametri di modello](../ide/template-parameters.md).

1. Selezionare i file nel modello e fare clic con il pulsante destro del mouse o dal menu di scelta rapida e scegliere **Invia a**  >  **cartella compressa**.

    I file selezionati vengono compressi in un file con *estensione zip* .

1. Inserire il nuovo file *zip* nella stessa directory del vecchio file *zip* .

1. Eliminare i file di modello estratti e il file di modello precedente con estensione *zip*.

## <a name="see-also"></a>Vedere anche

- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametri di modelli](../ide/template-parameters.md)
