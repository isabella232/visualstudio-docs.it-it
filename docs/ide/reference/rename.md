---
title: Refactoring con ridenominazione
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8d5b3d32b23b336dc86a92c33bcb97d02312f2dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182957"
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactoring con ridenominazione di un simbolo di codice

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rinominare gli identificatori per i simboli del codice, ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi.

**Quando:** si vuole rinominare un elemento in modo sicuro senza dover trovare tutte le istanze e copiare/incollare il nuovo nome.

**Perché:** è probabile che copiare e incollare il nuovo nome in un intero progetto causi errori. Questo strumento di refactoring eseguirà in modo accurato l'azione di ridenominazione.

## <a name="how-to"></a>Procedure

1. Evidenziare o posizionare il cursore del testo all'interno dell'elemento da rinominare:

   - C#:

       ![Codice evidenziato - C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/rename-highlight-vb.png)

2. Usare quindi la tastiera o il mouse come indicato di seguito:

   - **Tastiera**
      - Premere **CTRL+R** e quindi **CTRL+R**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
   - **Mouse**
      - Selezionare **Modifica > Refactoring > Rinomina**.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere **Rinomina**.

3. Rinominare l'elemento semplicemente digitando il nuovo nome.

   - C#:

      ![Animazione della ridenominazione - C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Ridenominazione - VB](media/rename-rename-vb.png)

   > [!TIP]
   > È anche possibile aggiornare i commenti e altre stringhe per l'uso del nuovo nome e [visualizzare in anteprima le modifiche](../../ide/preview-changes.md) prima del salvataggio usando le caselle di controllo della finestra di dialogo **Rinomina** visualizzata in alto a destra nell'editor.

4. Quando si è soddisfatti della modifica, scegliere il pulsante **Applica** o premere **INVIO**. Verrà eseguito il commit delle modifiche.

## <a name="remarks"></a>Osservazioni

- A partire da Visual Studio 2019 versione 16,3, quando si rinomina un tipo che corrisponde al nome del file in, viene visualizzata una casella di controllo che consente di rinominare il file nello stesso momento. Questa opzione viene visualizzata quando si rinomina una classe, un'interfaccia o un'enumerazione. Questa opzione non è supportata per i tipi parziali con più definizioni.

   ![Rinominare l'animazione con file-C #](media/rename-with-file-animated-cs.gif)

- Se si usa un nome già esistente che causerebbe un conflitto, nella finestra di dialogo **Rinomina** verrà visualizzato un avviso.

   ![Conflitto di ridenominazione](media/rename-conflict-cs.png)

- Un altro modo per rinominare un simbolo consiste nel modificare il nome nell'editor. Quindi, con il cursore nel nome del simbolo, premere **CTRL** + **.** in alternativa, è sufficiente espandere il menu icona lampadina visualizzato e **scegliere \<old name> Rinomina \<new name> a **.

   ![Rinominare nell'editor](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
