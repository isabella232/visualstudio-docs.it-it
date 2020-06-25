---
title: Aggiungi attributo DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290355"
---
# <a name="add-debuggerdisplay-attribute"></a>Aggiungi attributo DebuggerDisplay

Questa generazione di codice si applica a:

- C#

**Cosa:** L' [attributo DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) controlla la modalità di visualizzazione di un oggetto, di una proprietà o di un campo nelle finestre delle variabili del debugger.

**Quando:** Si desidera [aggiungere le proprietà](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips) all'interno del debugger a livello di codice.

**Motivo:** L'aggiunta di proprietà consente di ispezionare rapidamente gli oggetti in base alle relative proprietà, eseguendo la bubbling della proprietà nella parte superiore dell'elenco di proprietà dell'oggetto all'interno del debugger. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore su un tipo, un delegato, una proprietà o un campo. 

2. Premere **CTRL** + **.** per attivare il menu **azioni rapide e refactoring** e selezionare **Aggiungi attributo DebuggerDisplay**.

    ![Generare gli operatori di confronto](media/add-debugger-display-attribute.png)

3. L'attributo DebuggerDisplay viene aggiunto insieme a un metodo automatico che restituisce il valore predefinito ToString (). 

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
