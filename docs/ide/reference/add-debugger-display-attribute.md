---
title: Aggiungere l'attributo DebuggerDisplay
description: Informazioni su come aggiungere l'attributo DebuggerDisplay per controllare il modo in cui la finestra delle variabili del debugger visualizza un oggetto, una proprietà o un campo.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 6525da8cd530d6e0b0ab14655e26ddd42c5813977efd0c42a222bc5fea1dcef6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412342"
---
# <a name="add-debuggerdisplay-attribute"></a>Aggiungere l'attributo DebuggerDisplay

Questa generazione di codice si applica a:

- C#

**Cosa:** [L'attributo DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) controlla la modalità di visualizzazione di un oggetto, una proprietà o un campo nelle finestre delle variabili del debugger.

**Quando:** Si vogliono aggiungere [le proprietà all'interno](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) del debugger a livello di codice nel codice.

**Perché:** L'aggiunta di proprietà consente di esaminare rapidamente gli oggetti in base alle relative proprietà tramite il bubbling di tale proprietà all'inizio dell'elenco delle proprietà dell'oggetto all'interno del debugger. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore su un tipo, un delegato, una proprietà o un campo. 

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring e** selezionare Aggiungi **debuggerAttribuito visualizzato.**

    ![Generare gli operatori di confronto](media/add-debugger-display-attribute.png)

3. L'attributo DebuggerDisplay verrà aggiunto insieme a un metodo auto che restituisce il valore ToString() predefinito. 

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)