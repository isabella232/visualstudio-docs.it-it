---
title: Strutture di C, in Progettazione classi
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
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590684"
---
# <a name="c-structures-in-class-designer"></a>Strutture di C, in Progettazione classi

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

- [Lavorare con il codice C](working-with-visual-cpp-code.md)
- [Classi e struct](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
