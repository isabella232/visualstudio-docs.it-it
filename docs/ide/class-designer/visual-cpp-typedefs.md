---
title: C++Typedef in Progettazione classi
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 94dc4a6687a2aaede7fc901884c5d3acc6fbf56f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748004"
---
# <a name="c-typedefs-in-class-designer"></a>C++typedef in Progettazione classi

Le istruzioni [typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) creano uno o più livelli di riferimento indiretto tra un nome e il relativo tipo sottostante. **Progettazione classi** supporta i tipi typedef di C++, che vengono dichiarati con la parola chiave `typedef`, ad esempio:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

È quindi possibile usare questo tipo per dichiarare un'istanza:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Forme di classi e struct

In **Progettazione classi** un typedef di C++ ha la forma del tipo specificato nel typedef. Se l'origine dichiara `typedef class`, la forma ha gli angoli arrotondati e l'etichetta **Class**. Per `typedef struct` la forma ha gli angoli quadrati e l'etichetta **Struct**.

Classi e strutture possono avere typedef dichiarati annidati all'interno di essi. In **Progettazione classi** le forme di classi e strutture possono visualizzare le dichiarazioni typedef annidate come forme annidate.

Le forme typedef supportano i comandi **Mostra come associazione** e **Mostra come associazione di raccolte** nel menu di scelta rapida.

### <a name="class-typedef-example"></a>Esempio di typedef di classe

```cpp
class B {};
typedef B MyB;
```

![Typedef di classe C++ in Progettazione classi](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Esempio di typedef di struct

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef di struct C++ in Progettazione classi](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Typedef senza nome

Sebbene sia possibile dichiarare un typedef senza nome, **Progettazione classi** non usa il nome del tag specificato. **Progettazione classi** usa il nome generato da **Visualizzazione classi**. Ad esempio, la dichiarazione seguente è valida, ma appare in **Visualizzazione classi** e **Progettazione classi** come un oggetto denominato **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Progettazione classi** non visualizza i typedef il cui tipo di origine è un puntatore a funzione.

## <a name="see-also"></a>Vedere anche

- [Usare il C++ codice](working-with-visual-cpp-code.md)
- [Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)