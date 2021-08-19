---
title: Gestire strumenti esterni
description: Informazioni su come aggiungere e gestire nuovi strumenti esterni a cui è possibile accedere tramite il menu Strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9b7db6b407c92aee112301cedd34f93b6b2a91fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085923"
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

1. Aprire la **finestra di dialogo** Strumenti esterni scegliendo **Strumenti**  >  **Strumenti esterni**.

1. Fare clic su **Aggiungi** e quindi compilare le informazioni. Ad esempio, la voce seguente **Windows Explorer** viene aperto nella directory del file attualmente aperto in Visual Studio:

   * Titolo: `Open File Location`

   * Comando: `explorer.exe`

   * Argomenti: `/root, "$(ItemDir)"`

   ![Strumenti esterni - finestra di dialogo](media/external-tools-dialog.png)

Di seguito è riportato un elenco completo di argomenti che possono essere usati per la definizione di uno strumento esterno:

|NOME|Argomento|Descrizione|
|----------|--------------|-----------------|
|Percorso elemento|$(ItemPath)|Nome file completo del file corrente (unità + percorso + nome file).|
|Directory elemento|$(ItemDir)|Directory del file corrente (unità + percorso).|
|Nome file elemento|$(ItemFilename)|Nome del file corrente (nome file).|
|Estensione di elemento|$(ItemExt)|Estensione del nome del file corrente.|
|Riga corrente|$(CurLine)|Posizione della riga corrente del cursore nella finestra del codice.|
|Colonna corrente|$(CurCol)|Posizione della colonna corrente del cursore nella finestra del codice.|
|Testo corrente|$(CurText)|Testo selezionato.|
|Percorso di destinazione|$(TargetPath)|Nome file completo dell'elemento da compilare (unità + percorso + nome file).|
|Directory di destinazione|$(TargetDir)|Directory dell'elemento da compilare.|
|Nome destinazione|$(TargetName)|Nome file dell'elemento da compilare.|
|Estensione di destinazione|$(TargetExt)|Estensione di file dell'elemento da compilare.|
|Directory binaria|$(BinDir)|Posizione finale del file binario in fase di compilazione (definita come unità + percorso).|
|Directory del progetto|$(ProjectDir)|Directory del progetto corrente (unità + percorso).|
|Nome file progetto|$(ProjectFileName)|Nome file del progetto corrente (unità + percorso + nome file).|
|Directory soluzione|$(SolutionDir)|Directory della soluzione corrente (unità + percorso).|
|Nome file soluzione|$(SolutionFileName)|Nome file della soluzione corrente (unità + percorso + nome file).|

> [!NOTE]
> La barra di stato dell'IDE visualizza **le variabili Riga** corrente e Colonna corrente per indicare dove si trova il punto di inserimento nell'editor di codice **attivo.**  La **variabile Testo** corrente restituisce il testo o il codice selezionato in tale posizione.

## <a name="see-also"></a>Vedi anche

- [Strumenti di compilazione C/C++](/cpp/build/reference/c-cpp-build-tools)
