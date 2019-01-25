---
title: Opzioni, Editor di testo, F#, Correzioni del codice
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.FSharp.Code_Fixes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bbe6b49d7b80138c7fc465e1c86aa13e6bc5e92d
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398433"
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