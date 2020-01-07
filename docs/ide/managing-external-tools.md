---
title: Gestire strumenti esterni
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f22c687f88c7736d5c088ebc28ff490c4c16b8f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591294"
---
# <a name="manage-external-tools"></a>Gestire strumenti esterni

È possibile chiamare strumenti esterni direttamente in Visual Studio usando il menu **Strumenti**. Alcuni strumenti predefiniti sono disponibili nel menu **Strumenti** ed è possibile personalizzare il menu aggiungendo altri file eseguibili personalizzati.

## <a name="tools-available-on-the-tools-menu"></a>Strumenti disponibili nel menu Strumenti

Il menu **Strumenti** include alcuni comandi predefiniti, tra cui:

::: moniker range="vs-2017"

* **Estensioni e aggiornamenti** per [Gestire le estensioni di Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Gestione frammenti di codice** per [Organizzare i frammenti di codice](code-snippets.md)
* **Personalizza** per [Personalizzare menu e barre degli strumenti](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opzioni** per [Impostare un'ampia gamma di opzioni per l'IDE di Visual Studio e altri strumenti](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Gestione frammenti di codice** per [Organizzare i frammenti di codice](code-snippets.md)
* **Personalizza** per [Personalizzare menu e barre degli strumenti](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opzioni** per [Impostare un'ampia gamma di opzioni per l'IDE di Visual Studio e altri strumenti](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Aggiungere nuovi strumenti al menu Strumenti

È possibile aggiungere uno strumento esterno per visualizzarlo nel menu **Strumenti**.

1. Aprire la finestra di dialogo **Strumenti esterni** scegliendo **Strumenti** > **Strumenti esterni**.

1. Fare clic su **Aggiungi** e quindi compilare le informazioni. L'immissione seguente consente ad esempio a **Windows Explorer** di aprire la cartella dove si trova il file attualmente aperto in Visual Studio:

   * Titolo: `Open File Location`

   * Comando: `explorer.exe`

   * Argomenti: `/root, "$(ItemDir)"`

   ![Finestra di dialogo Strumenti esterni](media/external-tools-dialog.png)

Di seguito è riportato un elenco completo di argomenti che possono essere usati per la definizione di uno strumento esterno:

|Name|Argomento|Descrizione|
|----------|--------------|-----------------|
|Percorso elemento|$(ItemPath)|Nome file completo del file corrente (unità + percorso + nome file).|
|Directory elemento|$(ItemDir)|Directory del file corrente (unità + percorso).|
|Nome file elemento|$(ItemFilename)|Nome del file corrente (nome file).|
|Estensione di elemento|$(ItemExt)|Estensione del nome del file corrente.|
|Riga corrente|$(CurLine)|Posizione della riga corrente del cursore nella finestra del codice.|
|Colonna corrente|$(CurCol)|Posizione della colonna corrente del cursore nella finestra del codice.|
|Testo corrente|$(CurText)|Testo selezionato.|
|Percorso di destinazione|$(TargetPath)|Nome file completo dell'elemento da compilare (unità + percorso + nome file).|
|Target Directory|$(TargetDir)|Directory dell'elemento da compilare.|
|Nome di destinazione|$(TargetName)|Nome file dell'elemento da compilare.|
|Estensione di destinazione|$(TargetExt)|Estensione di file dell'elemento da compilare.|
|Directory binaria|$(BinDir)|Posizione finale del file binario in fase di compilazione (definita come unità + percorso).|
|Directory del progetto|$(ProjectDir)|Directory del progetto corrente (unità + percorso).|
|Nome del file di progetto|$(ProjectFileName)|Nome file del progetto corrente (unità + percorso + nome file).|
|Directory soluzione|$(SolutionDir)|Directory della soluzione corrente (unità + percorso).|
|Nome del file della soluzione|$(SolutionFileName)|Nome file della soluzione corrente (unità + percorso + nome file).|

> [!NOTE]
> La barra di stato dell'IDE visualizza le variabili di **Riga corrente** e **Colonna corrente** per indicare dove si trova il punto di inserimento nell'**Editor codice** attivo. La variabile di **Testo corrente** restituisce il testo o codice selezionato in quella posizione.

## <a name="see-also"></a>Vedere anche

- [Strumenti per la compilazione in C/C++](/cpp/build/reference/c-cpp-build-tools)
