---
title: Strutture Visual C++ in Progettazione classi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8e81ee25e081a324a8520317fa57a1314ccd0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954530"
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