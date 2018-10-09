---
title: Typedef di Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba8987abf608d7f8d83a77c2e946f34941c1bec6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540693"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Typedef di Visual C++ in Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [typedef di Visual C++ in Progettazione classi](https://docs.microsoft.com/visualstudio/ide/visual-cpp-typedefs-in-class-designer).  
  
Le istruzioni typedef creano uno o più livelli di riferimento indiretto tra un nome e il relativo tipo sottostante. Progettazione classi supporta i tipi typedef di C++, che vengono dichiarati con la parola chiave `typedef`, ad esempio:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
 È quindi possibile usare questo tipo per dichiarare un'istanza:  
  
 `COORD OriginPoint;`  
  
 Sebbene sia possibile dichiarare un typedef senza nome, Progettazione classi non userà il nome del tag specificato, ma il nome generato da Visualizzazione classi. Ad esempio, la dichiarazione seguente è valida, ma appare in Visualizzazione classi e Progettazione classi come un oggetto denominato **__unnamed**:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```  
  
 Per altre informazioni sull'uso del tipo `typedef`, vedere [(NOTINBUILD)Identificatore typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1).  
  
 Una forma di typedef C++ ha la forma del tipo specificato nell'istruzione typedef. Ad esempio, se l'origine dichiara `typedef class`, la forma ha gli angoli arrotondati e l'etichetta **Class**. Per `typedef struct` la forma ha gli angoli quadrati e l'etichetta **Struct**.  
  
 Classi e strutture possono avere typedef annidati dichiarati all'interno, di conseguenza, le forme di classi e strutture possono visualizzare le dichiarazioni typedef annidate come forme annidate.  
  
 Le forme typedef supportano i comandi **Mostra come associazione** e **Mostra come associazione di raccolte** nel menu di scelta rapida.  
  
 Di seguito sono riportati alcuni esempi di tipi typedef supportati da Progettazione classi:  
  
 `typedef type name`  
  
 *name* : *type*  
  
 typedef  
  
 Disegna una linea di associazione per la connessione al tipo *name*, se possibile.  
  
 `typedef void (*func)(int)`  
  
 `func: void (*)(int)`  
  
 typedef  
  
 Typedef per puntatori a funzione. Non viene disegnata alcuna linea di associazione.  
  
 Progettazione classi non visualizza un typedef se il tipo di origine è un puntatore a funzione.  
  
```  
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
 `MyInt: int`  
  
 typedef  
  
 `A`  
  
 Classe  
  
 Disegna una linea di associazione che punta dalla forma del tipo di origine alla forma del tipo di destinazione.  
  
 `Class B {};`  
  
 `typedef B MyB;`  
  
 `B`  
  
 Classe  
  
 `MyB : B`  
  
 typedef  
  
 Se si fa clic su una forma di typedef con il pulsante destro del mouse e si fa clic su **Mostra come associazione**, vengono visualizzati il typedef o la classe e una linea **Alias di** che unisce le due forme (simile a una linea di associazione).  
  
 `typedef B MyB;`  
  
 `typedef MyB A;`  
  
 `MyBar : Bar`  
  
 typedef  
  
 Vedi sopra.  
  
```  
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
 `B`  
  
 Classe  
  
 `MyB : B`  
  
 typedef  
  
 `A`  
  
 Classe  
  
 `MyB` è una forma di typedef annidata.  
  
 `#include <vector>`  
  
 `...`  
  
 `using namespace std;`  
  
 `...`  
  
 `typedef vector<int> MyIntVect;`  
  
 Classe `vector<T>`  
  
 `MyIntVect : vector<int>`  
  
 typedef  
  
 `class B {};`  
  
 `typedef B MyB;`  
  
 `class A : MyB {};`  
  
 `MyB : B`  
  
 typedef  
  
 -> B  
  
 `B`  
  
 `A`  
  
 Classe  
  
 -> MyB  
  
 Progettazione classi non supporta la visualizzazione di questo tipo di relazione usando un comando di menu di scelta rapida.  
  
 `#include <vector>`  
  
 `Typedef MyIntVect std::vector<int>;`  
  
 `Class MyVect : MyIntVect {};`  
  
 `std::vector<T>`  
  
 Classe  
  
 `MyIntVect : std::vector<int>`  
  
 typedef  
  
 `MyVect`  
  
 Classe  
  
 -> MyIntVect  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del codice Visual C++ (Progettazione classi)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [(NOTINBUILD)Identificatore typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)


