---
title: Opzioni, Editor di testo, C#, IntelliSense
description: Informazioni su come usare la pagina IntelliSense nella sezione C# per modificare le impostazioni che influiscono sul comportamento di IntelliSense per C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e727fad6d3cb15f70cf630b1077170d16d28b7f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039744"
---
# <a name="options-text-editor-c-intellisense"></a>Opzioni, Editor di testo, C#, IntelliSense

Usare la pagina delle opzioni **IntelliSense** per modificare le impostazioni che hanno effetto sul comportamento di IntelliSense per C#. Per accedere a questa pagina di opzioni, scegliere **strumenti**  >  **Opzioni** e quindi scegliere **editor di testo**  >  **C#**  >  **IntelliSense**.

La pagina delle opzioni **IntelliSense** include le opzioni seguenti:

## <a name="completion-lists"></a>Elenchi di completamento

- Mostra elenco di completamento dopo la digitazione di un carattere*

   Quando questa opzione è selezionata, IntelliSense visualizza automaticamente l'elenco di completamento quando si inizia a digitare. Quando questa opzione non è selezionata, il completamento di IntelliSense è ancora disponibile tramite il menu **IntelliSense** o premendo **CTRL**+**BARRA SPAZIATRICE**.

- Mostra elenco di completamento dopo l'eliminazione di un carattere

- Evidenzia le parti corrispondenti di voci dell'elenco di completamento

- Mostra i filtri per le voci di completamento

## <a name="snippets-behavior"></a>Comportamento dei frammenti

- Non includere mai i frammenti

   Quando questa opzione è selezionata, IntelliSense non aggiunge mai gli alias per i frammenti di codice C# all'elenco di completamento.

- Includi sempre i frammenti

   Quando questa opzione è selezionata, IntelliSense aggiunge gli alias per i frammenti di codice C# all'elenco di completamento. Se l'alias del frammento di codice corrisponde a una parola chiave, ad esempio [class](/dotnet/csharp/language-reference/keywords/class), la parola chiave viene sostituita dal collegamento. Per altre informazioni, vedere [Frammenti di codice C#](../../ide/visual-csharp-code-snippets.md).

- Includi i frammenti quando si digita ?+TAB dopo un identificatore

   Quando questa opzione è selezionata, IntelliSense aggiunge gli alias per i frammenti di codice C# all'elenco di completamento quando **?** + Viene premuto **Tab** dopo un identificatore

## <a name="enter-key-behavior"></a>Comportamento del tasto INVIO

- Non aggiungere mai una nuova riga dopo INVIO

   Specifica che non viene mai aggiunta automaticamente una nuova riga dopo aver selezionato un elemento nell'elenco di completamento e premuto **INVIO**.

- Aggiungi una nuova riga dopo INVIO alla fine della parola digitata

   Specifica che se si digitano tutti i caratteri di una voce dell'elenco di completamento e quindi si preme **INVIO**, viene aggiunta automaticamente una nuova riga e il cursore si sposta nella nuova riga.

   Ad esempio, se si digita `else` e quindi si preme **INVIO**, nell'editor viene visualizzato quanto segue:

   `else`

   `|` (posizione del cursore)

   Tuttavia, se si digita solo `el` e quindi si preme **INVIO**, nell'editor viene visualizzato quanto segue:

   `else|` (posizione del cursore)

- Aggiungi sempre una nuova riga dopo INVIO

   Specifica che se si digita *qualsiasi* carattere di una voce dell'elenco di completamento e quindi si preme **INVIO**, viene creata automaticamente una nuova riga e il cursore si sposta nella nuova riga.

## <a name="show-name-suggestions"></a>Mostra suggerimenti per nomi

Esegue il completamento automatico dei nomi degli oggetti per i membri selezionati recentemente.

## <a name="see-also"></a>Vedere anche

- [Generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
- [Utilizzo di IntelliSense](../../ide/using-intellisense.md)
