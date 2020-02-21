---
title: Genera campo privato dal costruttore
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527661"
---
# <a name="generate-private-field-from-constructor"></a>Genera campo privato dal costruttore

Questo refactoring si applica a: 

- C# 

**Cosa:** Genera un campo privato da un costruttore. 

**Quando:** Si desidera aggiungere rapidamente un campo privato da un costruttore.

**Motivo:** La scrittura di campi privati può richiedere molto tempo e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.

## <a name="how-to"></a>Procedura 

1. Posizionare il cursore sul nome del parametro all'interno del costruttore.

2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
   
3. Selezionare l'opzione per **creare e inizializzare il campo**.

   ![Genera campo privato dal costruttore](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md)
