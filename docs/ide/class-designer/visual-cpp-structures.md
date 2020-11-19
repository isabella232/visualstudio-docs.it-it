---
title: Strutture C++ in Progettazione classi
description: Informazioni su come Progettazione classi supporta le strutture C++ dichiarate con la parola chiave struct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d22ff6be694de69f105897821aba1b587955f748
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903429"
---
# <a name="c-structures-in-class-designer"></a>Strutture C++ in Progettazione classi

**Progettazione Classi** supporta le strutture C++, che vengono dichiarate con la parola chiave `struct`. Di seguito è illustrato un esempio:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Per altre informazioni sull'uso del tipo `struct`, vedere [struct](/cpp/cpp/struct-cpp).

Una forma struttura C++ in un diagramma classi è simile per aspetto e funzionamento a una forma classe, ad eccezione del fatto che l'etichetta della forma struttura è **Struct** ed è contraddistinta da angoli squadrati anziché arrotondati.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------| - |
|`struct StructureName {};`|**NomeStruttura**<br /><br /> Struct|

## <a name="see-also"></a>Vedere anche

- [Uso del codice C++](working-with-visual-cpp-code.md)
- [Classi e struct](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
