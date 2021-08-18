---
title: Aggiungere l'intestazione del file
description: Informazioni su come usare un file EditorConfig per aggiungere intestazioni di file a file, progetti e soluzioni esistenti.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: f902d90de1260b1dde17bb4570a4841bd73bbe42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094347"
---
# <a name="add-file-header"></a>Aggiungere l'intestazione del file

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** Aggiungere intestazioni di file a file, progetti e soluzioni esistenti usando [Un EditorConfig.](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

**Quando:** Si vuole aggiungere facilmente un'intestazione di file a file, progetti e soluzioni.

**Perché:** Il team richiede di includere un'intestazione di file ai fini del copyright. 

## <a name="how-to"></a>Procedure

1. Aggiungere un [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) a un progetto o a una soluzione, se non è già disponibile.

2. Aggiungere la regola seguente al file EditorConfig: *file_header_template*.

3. Impostare il valore della regola in modo che sia uguale al testo dell'intestazione che si vuole applicare. È possibile usare `{fileName}` come segnaposto per il nome del file.

    ![Screenshot del file EditorConfig che mostra il file_header_template predefinito.](media/add-file-header-rule.png)

    > [!NOTE]
    > Non è possibile avere più righe esplicite in Un EditorConfig e sarà necessario usare il carattere di nuova riga Unix per inserire nuove righe.

4. Posizionare il punto di interruzione nella prima riga di qualsiasi file C# o Visual Basic file.

5. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

6. Selezionare **Aggiungi intestazione file**. 

    ![Screenshot dell'opzione Aggiungi intestazione file.](media/add-file-header.png)

7. Per applicare l'intestazione del file a un intero progetto o soluzione, **selezionare Project** o **Soluzione** nell'opzione **Correggi tutte le occorrenze in:** .

8. Verrà **visualizzata la finestra di dialogo Correggi** tutte le occorrenze in cui è possibile visualizzare in anteprima le modifiche.

    ![Finestra di dialogo Correggi tutte le occorrenze](media/file-header-preview-changes.png)

8. Selezionare **Applica** per applicare le modifiche.

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)