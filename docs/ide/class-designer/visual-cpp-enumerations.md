---
title: Enumerazioni C++ in Progettazione classi
description: Informazioni su come Progettazione classi supporta i tipi di classe enum C++ e con ambito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: b4ab0dc47f9113e17b36617b432df1ffe5f0153e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109500"
---
# <a name="c-enumerations-in-class-designer"></a>Enumerazioni C++ in Progettazione classi

**Progettazione classi** supporta C++ `enum` e i tipi con `enum class` ambito. Di seguito è illustrato un esempio:

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

## <a name="see-also"></a>Vedi anche

- [Uso del codice C++](working-with-visual-cpp-code.md)
- [Enumerazioni](/cpp/cpp/enumerations-cpp)
