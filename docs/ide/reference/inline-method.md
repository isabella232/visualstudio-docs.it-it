---
title: Metodo inline
description: Informazioni su come usare il menu Azioni rapide e refactoring in Visual Studio per eseguire il refactoring delle dichiarazioni di metodi inline e fornire una sintassi più chiara.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2c474c43451006121f940da5eed66dfb9277806a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101206"
---
# <a name="inline-method"></a>Metodo inline

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Refactoring del metodo inline. 

**Quando:** Si desidera sostituire gli utilizzi di un metodo statico, di un'istanza e di un metodo di estensione all'interno di un singolo corpo di istruzione con un'opzione per rimuovere la dichiarazione del metodo originale.

**Perché:**  Questo refactoring fornirà una sintassi più chiara.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sull'utilizzo del metodo .

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti: 
    
   Selezionare **Inline `<QualifiedMethodName>`** (NomeMetodo inline) per rimuovere la dichiarazione del metodo inline: 

    ![Screeenshot del menu Azioni rapide e refactoring in Visual Studio con l'opzione Convert 'Inline 'CreateWidget()' selezionata e le modifiche al codice C# visualizzate.](media/inline-method-remove-declaration.png)

   Selezionare **Inline and keep `<QualifiedMethodName>`** (NomeMetodo inline e mantieni) per mantenere la dichiarazione del metodo originale: 

    ![Screeenshot del menu Azioni rapide e refactoring in Visual Studio con Convert 'Inline and keep 'CreateWidget()' selected (Azioni rapide e refactoring) in Visual Studio con Convert 'Inline and keep 'CreateWidget()' selected and C# code changes shown (Converti inline e mantieni selezionato 'CreateWidget()' e le modifiche al codice C#).](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
