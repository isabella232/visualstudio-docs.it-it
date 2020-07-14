---
title: Aggiungi intestazione file
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44cf9c34a69d665186a9f386e7ec34c5a59b8cdc
ms.sourcegitcommit: 8b1314ceab58e0d562cdbb1367fa738fdca7bf1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/13/2020
ms.locfileid: "86285381"
---
# <a name="add-file-header"></a>Aggiungi intestazione file

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** Aggiungere le intestazioni dei file a file, progetti e soluzioni esistenti usando un [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

**Quando:** Si desidera aggiungere facilmente un'intestazione di file a file, progetti e soluzioni.

**Motivo:** Il team richiede l'inclusione di un'intestazione di file per finalità di copyright. 

## <a name="how-to"></a>Procedure

1. Aggiungere un [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) a un progetto o a una soluzione se non ne è già presente uno.

2. Aggiungere la regola seguente al file EditorConfig: *file_header_template*.

3. Impostare il valore della regola su uguale al testo dell'intestazione che si desidera applicare.

    ![Regola di intestazione del file EditorConfig](media/add-file-header-rule.png)

> [!NOTE]
> Non è possibile avere più righe esplicite in un EditorConfig e sarà necessario usare il carattere di nuova riga UNIX per inserire nuove righe.

4. Posizionare il punto di inserimento sulla prima riga di un file C# o Visual Basic.

5. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

6. Selezionare **Aggiungi intestazione file**. 

    ![Regola di intestazione del file EditorConfig](media/add-file-header.png)

7. Per applicare l'intestazione del file a un intero progetto o a una soluzione, selezionare **progetto** o **soluzione** nell'opzione **Correggi tutte le occorrenze in:** .

8. Viene visualizzata la finestra di dialogo **Correggi tutte le occorrenze** in cui è possibile visualizzare in anteprima le modifiche.

    ![Correggi tutte le occorrenze (finestra di dialogo)](media/file-header-preview-changes.png)

8. Selezionare **applica** per applicare le modifiche.

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
