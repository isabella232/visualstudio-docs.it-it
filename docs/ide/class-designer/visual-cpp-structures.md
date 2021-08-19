---
title: Strutture C++ in Progettazione classi
description: Informazioni su come Progettazione classi le strutture C++ dichiarate con lo struct della parola chiave.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: a3d05c4aac4b4d2962d27f4d5586d5fb289ac9aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078388"
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

## <a name="see-also"></a>Vedi anche

- [Uso del codice C++](working-with-visual-cpp-code.md)
- [Classi e struct](/cpp/cpp/classes-and-structs-cpp)
- [Struct](/cpp/cpp/struct-cpp)
