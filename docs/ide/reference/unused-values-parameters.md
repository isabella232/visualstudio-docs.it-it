---
title: Valori e parametri non usati
description: Informazioni sulle assegnazioni di valori, le variabili e i parametri non usati e su come vengono visualizzati nell'editor di codice in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3fcdd7703e6b367ba8649918ff346646982c4c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116942"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Assegnazioni, variabili e parametri di valori non usati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Dissolvenza dei parametri inutilizzati e genera un avviso per i valori di espressione non usati. Il compilatore esegue anche un'analisi del flusso per trovare tutte le assegnazioni di valori non usati. Le assegnazioni di valori non usati vanno in dissolvenza e viene visualizzata una lampadina con un'[Azione rapida](../quick-actions.md) per rimuovere l'assegnazione ridondante. Le variabili non usate con valori sconosciuti visualizzano invece un suggerimento [Azione rapida](../quick-actions.md) per l'uso di [variabili discard](/dotnet/csharp/discards). Le variabili discard sono variabili dummy temporanee intenzionalmente non usate nel codice dell'applicazione. Possono ridurre l'allocazione di memoria e migliorare la leggibilità del codice.

**Quando:** Si dispone di assegnazioni di valori, parametri o valori di espressione che non vengono mai usati.

**Perché:** A volte è difficile capire se un'assegnazione di valore, una variabile o un parametro non viene più usato. Applicando la dissolvenza a questi valori o generando un avviso si ottiene un'indicazione visiva del codice che è possibile eliminare.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostica per valori e parametri di espressione non usati

1. Considerare qualsiasi assegnazione di valore, variabile o parametro che non viene usato.
2. Il parametro o l'assegnazione di valori inutilizzati appare in dissolvenza. Il valore dell'espressione inutilizzata genera un avviso.

  ![Parametro non usato](media/unused-parameter.png)
  ![Valore non usato](media/unused-value.png)
  ![Assegnazione di valore non usata](media/unused-value-assignment.png)
  ![Variabile discard di valore non usato](media/unused-value-discard.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
