---
title: Opzioni, Editor di testo, F#, Correzioni del codice
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bb9daee86fec058fca68740eaea3b9436e5570d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778541"
---
# <a name="options-text-editor-f-code-fixes"></a>Opzioni, Editor di testo, F#, Correzioni del codice

Usare la pagina delle opzioni **Correzioni del codice** per specificare le impostazioni che consentono di identificare gli errori del codice e offrono soluzioni. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **F#** > **Correzioni del codice**.

## <a name="code-fixes"></a>Correzioni del codice

- **Semplifica nomi (rimuovi qualificatori non necessari)**

   Se questa casella di controllo è selezionata, i nomi completi vengono semplificati quando non sono necessarie elementi di qualificazione, come per un membro di uno spazio dei nomi usato di frequente.

- **Inserisci sempre le istruzioni OPEN al primo livello**

   Se questa casella di controllo è selezionata e si digita un'istruzione OPEN nel codice, viene posizionata al primo livello.

- **Rimuovi istruzioni OPEN inutilizzate**

   Se questa casella di controllo è selezionata, vengono rimosse le istruzioni OPEN inutilizzate nel file corrente.

- **Analyze and suggest fixes for unused values** (Analizza e suggerisci correzioni per i valori inutilizzati)

   Se questa casella di controllo è selezionata, lo strumento riconosce un valore che non viene usato nel codice. Quindi, al passaggio del mouse sul valore inutilizzato, vengono consigliati i modi in cui è possibile usare il valore.

## <a name="see-also"></a>Vedere anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)