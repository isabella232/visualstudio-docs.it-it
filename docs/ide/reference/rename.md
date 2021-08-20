---
title: Refactoring con ridenominazione
description: Informazioni su come usare la funzionalità Refactoring Rinomina per rinominare gli identificatori per i simboli di codice, ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f71587d86bc1b4fc722abeee31a0e8e7ce8ae7cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123840"
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

## <a name="remarks"></a>Commenti

- A partire da Visual Studio 2019 versione 16.3, quando si rinomina un tipo che corrisponde al nome del file in cui si trova, viene visualizzata una casella di controllo che consente di rinominare il file contemporaneamente. Questa opzione viene visualizzata quando si rinomina una classe, un'interfaccia o un'enumerazione. Questa opzione non è supportata per i tipi parziali con più definizioni.

   ![Rinominare l'animazione con il file - C #](media/rename-with-file-animated-cs.gif)

- Se si usa un nome già esistente che causerebbe un conflitto, nella finestra di dialogo **Rinomina** verrà visualizzato un avviso.

   ![Conflitto di ridenominazione](media/rename-conflict-cs.png)

- Un altro modo per rinominare un simbolo consiste nel modificare il nome nell'editor. Quindi, con il cursore nel nome del simbolo, premere **CTRL** + **.** o semplicemente espandere il menu icona a forma di lampadina visualizzato e scegliere **Rinomina \<old name> in \<new name>**.

   ![Rinominare nell'editor](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
