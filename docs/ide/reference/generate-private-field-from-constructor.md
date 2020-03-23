---
title: Generare un campo privato dal costruttore
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094029"
---
# <a name="generate-private-field-from-constructor"></a>Generare un campo privato dal costruttore

Questo refactoring si applica a: 

- C# 

- Visual Basic

**Cosa:** Generare un campo privato da un costruttore. 

**Quando:** Si desidera aggiungere rapidamente un campo privato da un costruttore.

**Perché:** La scrittura di campi privati può richiedere molto tempo e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore sul nome del parametro all'interno del costruttore.

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   
3. Selezionare l'opzione **Crea e inizializza campo**.

   ![Generare un campo privato dal costruttore](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md)
