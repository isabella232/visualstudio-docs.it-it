---
title: Opzioni, Editor di testo, F#, Correzioni del codice
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666276"
---
# <a name="options-text-editor--f--code-fixes"></a>Opzioni: editor di testo F# > > correzioni del codice

Usare la pagina delle opzioni Correzioni del codice per specificare le impostazioni che consentono di identificare gli errori del codice e offrono soluzioni. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **F#**  > **Correzioni del codice**.

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

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
