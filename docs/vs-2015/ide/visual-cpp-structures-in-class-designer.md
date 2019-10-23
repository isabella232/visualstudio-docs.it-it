---
title: Strutture Visual C++ in Progettazione classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646758"
---
# <a name="visual-c-structures-in-class-designer"></a>Strutture Visual C++ in Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Progettazione classi supporta le strutture C++, che vengono dichiarate con la parola chiave `struct`, come nell'esempio seguente:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Per altre informazioni sull'uso del tipo `struct`, vedere [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Una forma struttura C++ in un diagramma classi è simile per aspetto e funzionamento a una forma classe, ad eccezione del fatto che l'etichetta della forma struttura è **Struct** ed è contraddistinta da angoli squadrati anziché arrotondati.

|Elemento del codice|Visualizzazione di Progettazione classi|
|------------------|-------------------------|
|`struct StructureName {};`|**NomeStruttura**<br /><br /> Struct|

## <a name="see-also"></a>Vedere anche
 [Utilizzo del codice C++ visuale (Progettazione classi) ](../ide/working-with-visual-cpp-code-class-designer.md) [Classes e struct ](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
