---
title: Aggiungi attributo DebuggerDisplay
description: Informazioni su come aggiungere l'attributo DebuggerDisplay per controllare la modalità di visualizzazione di un oggetto, di una proprietà o di un campo nella finestra delle variabili del debugger.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871119"
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

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)