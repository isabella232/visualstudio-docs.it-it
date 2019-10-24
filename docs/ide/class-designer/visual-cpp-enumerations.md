---
title: C++Enumerazioni in Progettazione classi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747984"
---
# <a name="c-enumerations-in-class-designer"></a>C++enumerazioni in Progettazione classi

**Progettazione classi** supporta i tipi `enum` e `enum class` con ambito in C++. Di seguito è riportato un esempio:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Una forma di enumerazione C++ in un diagramma classi viene visualizzata e funziona come una forma di struttura, tranne per il fatto che l'etichetta **Enum** o **Enum class** è di colore rosa anziché blu e ha un bordo colorato sui margini sinistro e superiore. Entrambe le forme di enumerazione e struttura hanno angoli quadrati.

Per altre informazioni sull'uso del tipo `enum`, vedere [Enumerazioni](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Vedere anche

- [Utilizzo del C++ codice](working-with-visual-cpp-code.md)
- [Enumerazioni](/cpp/cpp/enumerations-cpp)