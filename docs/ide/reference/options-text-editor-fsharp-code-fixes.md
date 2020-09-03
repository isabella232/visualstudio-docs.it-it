---
title: Opzioni, Editor di testo, F#, Correzioni del codice
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770937"
---
# <a name="options-text-editor--f--code-fixes"></a>Opzioni: editor di testo > le correzioni del codice > F #

Usare la pagina delle opzioni Correzioni del codice per specificare le impostazioni che consentono di identificare gli errori del codice e offrono soluzioni. Per accedere a questa pagina di opzioni, scegliere **strumenti**  >  **Opzioni**e quindi scegliere **editor di testo**  >  **F #**  >  **correzioni del codice**.

## <a name="code-fixes"></a>Correzioni del codice

- **Semplifica nomi (rimuovi qualificatori non necessari)**

  Se questa casella di controllo è selezionata, i nomi completi vengono semplificati quando non sono necessarie elementi di qualificazione, come per un membro di uno spazio dei nomi usato di frequente.

- **Inserisci sempre le istruzioni OPEN al primo livello**

  Se questa casella di controllo è selezionata e si digita un'istruzione `open` nel codice, viene posizionata al primo livello.

- **Rimuovi istruzioni OPEN inutilizzate**

  Se questa casella di controllo è selezionata, i documenti vengono analizzati per le istruzioni `open` inutilizzate e viene visualizzata una lampadina [Azione rapida](../quick-actions.md) con un'azione per rimuovere tutte le istruzioni `open` inutilizzate.

- **Analyze and suggest fixes for unused values** (Analizza e suggerisci correzioni per i valori inutilizzati)

  Se questa casella di controllo è selezionata, lo strumento riconosce un valore che non viene usato nel codice. Quindi, al passaggio del mouse sul valore inutilizzato, vengono consigliati i modi in cui è possibile usare il valore.

## <a name="see-also"></a>Vedere anche

- [Generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
