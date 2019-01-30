---
title: Enumerazioni Visual C++ in Progettazione classi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d5f02d899c9d81c8dd19aac879bed7ac9c1acdb8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946828"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumerazioni Visual C++ in Progettazione classi

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

- [Uso del codice di Visual C++](working-with-visual-cpp-code.md)
- [Enumerazioni](/cpp/cpp/enumerations-cpp)