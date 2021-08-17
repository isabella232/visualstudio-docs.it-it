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
ms.openlocfilehash: 5e72c2ddba9bfbca2c3fdaa43ae1f278009e3960
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028033"
---
# <a name="add-debuggerdisplay-attribute"></a>Aggiungere l'attributo DebuggerDisplay

Questa generazione di codice si applica a:

- C#

**Cosa:** [L'attributo DebuggerDisplay controlla](../../debugger/using-the-debuggerdisplay-attribute.md) la modalità di visualizzazione di un oggetto, una proprietà o un campo nelle finestre delle variabili del debugger.

**Quando:** Si desidera aggiungere [le proprietà all'interno](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) del debugger a livello di codice nel codice.

**Perché:** L'aggiunta di proprietà consente di esaminare rapidamente gli oggetti in base alle relative proprietà tramite il bubbling di tale proprietà all'inizio dell'elenco delle proprietà dell'oggetto all'interno del debugger. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore su un tipo, un delegato, una proprietà o un campo. 

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring e** selezionare Aggiungi attributo **DebuggerVisual .**

    ![Generare gli operatori di confronto](media/add-debugger-display-attribute.png)

3. L'attributo DebuggerDisplay verrà aggiunto insieme a un metodo automatico che restituisce il valore Predefinito ToString(). 

## <a name="see-also"></a>Vedi anche

- [Generazione del codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)