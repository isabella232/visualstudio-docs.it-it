---
title: Valori e parametri non usati
description: Informazioni sulle assegnazioni di valori, le variabili e i parametri non usati e sul modo in cui vengono visualizzati nell'editor di codice in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd0b6e936f4478cb4b74a3f004e69d77dbad7fbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960611"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Assegnazioni, variabili e parametri di valori non usati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Dissolve i parametri inutilizzati e genera un avviso per i valori delle espressioni non utilizzate. Il compilatore esegue anche un'analisi del flusso per trovare tutte le assegnazioni di valori non usati. Le assegnazioni di valori non usati vanno in dissolvenza e viene visualizzata una lampadina con un'[Azione rapida](../quick-actions.md) per rimuovere l'assegnazione ridondante. Le variabili non usate con valori sconosciuti visualizzano invece un suggerimento [Azione rapida](../quick-actions.md) per l'uso di [variabili discard](/dotnet/csharp/discards). Le variabili discard sono variabili dummy temporanee intenzionalmente non usate nel codice dell'applicazione. Possono ridurre l'allocazione di memoria e migliorare la leggibilità del codice.

**Quando:** Sono disponibili assegnazioni di valore, parametri o valori di espressione che non vengono mai utilizzati.

**Motivo:** Talvolta è difficile stabilire se un'assegnazione di valore, una variabile o un parametro non viene più utilizzato. Applicando la dissolvenza a questi valori o generando un avviso si ottiene un'indicazione visiva del codice che è possibile eliminare.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostica per valori e parametri di espressione non usati

1. Considerare qualsiasi assegnazione di valore, variabile o parametro che non viene usato.
2. L'assegnazione del valore o il parametro non usato viene visualizzato come sbiadito. Il valore dell'espressione non utilizzata genera un avviso.

  ![Parametro non usato](media/unused-parameter.png)
  ![Valore non usato](media/unused-value.png)
  ![Assegnazione di valore non usata](media/unused-value-assignment.png)
  ![Variabile discard di valore non usato](media/unused-value-discard.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../csharp-developer-productivity.md)
