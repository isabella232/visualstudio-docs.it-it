---
title: Eseguire il refactoring del codice per sostituire var con un tipo esplicito
description: Informazioni su come usare Azioni rapide per sostituire var in un'espressione di variabile locale con un tipo esplicito.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: de79490c0dd343cf1bd0e9b120def07aa548799a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048882"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactoring per sostituire var con un tipo esplicito

Usare questo refactoring per sostituire [var](/dotnet/csharp/language-reference/keywords/var) in una dichiarazione di variabile locale con un tipo esplicito.

Questo refactoring si applica a:

- C#

## <a name="why-to-use-an-explicit-type"></a>Motivi per usare un tipo esplicito

Di seguito sono riportati alcuni motivi per dichiarare una variabile con un tipo esplicito:

- Per migliorare la leggibilità del codice.

- Quando non si vuole inizializzare la variabile nella dichiarazione.

Tuttavia, [var](/dotnet/csharp/language-reference/keywords/var) deve essere usato quando una variabile viene inizializzata con un tipo anonimo e si accede alle proprietà dell'oggetto in un momento successivo. Per altre informazioni, vedere [Variabili locali tipizzate in modo implicito (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Modo d'uso

1. Posizionare il cursore sulla parola chiave `var`.

1. Premere  + **CTRL+ .** oppure fare clic sull'icona a forma di cacciavite ![icona cacciavite](../media/screwdriver-icon.png) nel margine del file di codice.

   ![Menu delle azioni rapide Usare un tipo esplicito](media/use-explicit-type.png)

1. Selezionare **Usare un tipo esplicito**. In alternativa, selezionare **Anteprima modifiche** per aprire la finestra di dialogo [Anteprima modifiche](../../ide/preview-changes.md) e quindi selezionare **Applica**.

## <a name="see-also"></a>Vedi anche

- [Variabili tipizzate in modo implicito (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
