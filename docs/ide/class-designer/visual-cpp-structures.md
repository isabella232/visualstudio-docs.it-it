---
title: Strutture Visual C++ in Progettazione classi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6daa85e9f8a3ea6f5fe68808cd46fc4414f77c17
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966361"
---
# <a name="visual-c-structures-in-class-designer"></a>Strutture Visual C++ in Progettazione classi

**Progettazione Classi** supporta le strutture C++, che vengono dichiarate con la parola chiave `struct`. Di seguito è riportato un esempio:

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

- [Uso del codice di Visual C++](working-with-visual-cpp-code.md)
- [Classi e struct](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)