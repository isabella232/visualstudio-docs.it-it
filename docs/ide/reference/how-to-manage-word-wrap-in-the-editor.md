---
title: "Procedura: gestire la modalità A capo automatico nell'editor"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a1419a473bc0edc9fbc68ab978feb776ed63636
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "42626588"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Procedura: gestire il ritorno a capo automatico nell'editor

È possibile selezionare e deselezionare l'opzione **A capo automatico**. Se questa opzione è selezionata, la parte di una riga che si estende oltre la larghezza corrente della finestra dell'Editor del codice viene visualizzata nella riga successiva. Se questa opzione è deselezionata, ad esempio per facilitare l'uso della numerazione delle righe, è possibile visualizzare la parte finale delle righe lunghe scorrendo la finestra verso destra.

## <a name="to-set-word-wrap-preferences"></a>Per impostare le preferenze del ritorno a capo automatico

1.  Scegliere **Opzioni** dal menu **Strumenti**.

2.  Per impostare l'opzione a livello globale, nella cartella **Editor di testo** scegliere le opzioni **Generale** nella sottocartella **Tutti i linguaggi**.

     oppure

     Scegliere le opzioni **Generale** nella sottocartella corrispondente al linguaggio di programmazione in uso.

3.  In **Impostazioni**selezionare o deselezionare l'opzione **A capo automatico**.

     Se l'opzione **A capo automatico** è selezionata, l'opzione **Mostra icone per ritorno a capo automatico** è abilitata.

4.  Selezionare l'opzione **Mostra icone per ritorno a capo automatico** se si preferisce visualizzare un indicatore freccia di ritorno a capo nei punti in cui una riga lunga va a capo. Deselezionare questa opzione per evitare di visualizzare questo indicatore.

    > [!NOTE]
    > Queste frecce di promemoria non vengono aggiunte al codice ma vengono solo visualizzate.

## <a name="known-issues"></a>Problemi noti

Se si ha familiarità con il ritorno a capo automatico in Notepad++, Sublime Text o Visual Studio Code, tenere presente i problemi seguenti per cui Visual Studio si comporta in modo diverso rispetto agli altri editor:

* [Il triplo clic non seleziona l'intera riga](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Il comando Taglia non elimina l'intera riga](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Premere il tasto FINE due volte non sposta il cursore alla fine della riga](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Vedere anche

- [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)
- [Editor di testo (finestra di dialogo Opzioni)](../../ide/reference/text-editor-options-dialog-box.md)
- [Funzionalità dell'editor del codice](../../ide/writing-code-in-the-code-and-text-editor.md)
