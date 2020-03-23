---
title: Valori e parametri non usati
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531869"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Assegnazioni, variabili e parametri di valori non usati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Dissolve i parametri inutilizzati e genera un avviso per i valori di espressione inutilizzati. Il compilatore esegue anche un'analisi del flusso per trovare tutte le assegnazioni di valori non usati. Le assegnazioni di valori non usati vanno in dissolvenza e viene visualizzata una lampadina con un'[Azione rapida](../quick-actions.md) per rimuovere l'assegnazione ridondante. Le variabili non usate con valori sconosciuti visualizzano invece un suggerimento [Azione rapida](../quick-actions.md) per l'uso di [variabili discard](/dotnet/csharp/discards). Le variabili discard sono variabili dummy temporanee intenzionalmente non usate nel codice dell'applicazione. Possono ridurre l'allocazione di memoria e migliorare la leggibilità del codice.

**Quando:** Si dispone di assegnazioni di valori, parametri o valori di espressione che non vengono mai utilizzati.

**Perché:** A volte è difficile stabilire se un'assegnazione di valore, una variabile o un parametro non viene più utilizzato. Applicando la dissolvenza a questi valori o generando un avviso si ottiene un'indicazione visiva del codice che è possibile eliminare.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostica per valori e parametri di espressione non usati

1. Considerare qualsiasi assegnazione di valore, variabile o parametro che non viene usato.
2. L'assegnazione o il parametro del valore inutilizzato appare sbiadito. Il valore dell'espressione inutilizzata genera un avviso.

  ![Parametro non usato](media/unused-parameter.png)
  ![Valore non usato](media/unused-value.png)
  ![Assegnazione di valore non usata](media/unused-value-assignment.png)
  ![Variabile discard di valore non usato](media/unused-value-discard.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
