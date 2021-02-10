---
title: Aggiungi attributo DebuggerDisplay
description: Informazioni su come aggiungere l'attributo DebuggerDisplay per controllare la modalità di visualizzazione di un oggetto, di una proprietà o di un campo nella finestra delle variabili del debugger.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956724"
---
# <a name="add-debuggerdisplay-attribute"></a>Aggiungi attributo DebuggerDisplay

Questa generazione di codice si applica a:

- C#

**Cosa:** L' [attributo DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) controlla la modalità di visualizzazione di un oggetto, di una proprietà o di un campo nelle finestre delle variabili del debugger.

**Quando:** Si desidera [aggiungere le proprietà](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) all'interno del debugger a livello di codice.

**Motivo:** L'aggiunta di proprietà consente di ispezionare rapidamente gli oggetti in base alle relative proprietà, eseguendo la bubbling della proprietà nella parte superiore dell'elenco di proprietà dell'oggetto all'interno del debugger. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore su un tipo, un delegato, una proprietà o un campo. 

2. Premere **CTRL** + **.** per attivare il menu **azioni rapide e refactoring** e selezionare **Aggiungi attributo DebuggerDisplay**.

    ![Generare gli operatori di confronto](media/add-debugger-display-attribute.png)

3. L'attributo DebuggerDisplay viene aggiunto insieme a un metodo automatico che restituisce il valore predefinito ToString (). 

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)