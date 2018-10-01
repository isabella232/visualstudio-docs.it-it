---
title: Enumerazioni Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d4bc1385c934d9858cef19f8ffe73ad6a0baaf0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530815"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumerazioni Visual C++ in Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [enumerazioni Visual C++ in Progettazione classi](https://docs.microsoft.com/visualstudio/ide/visual-cpp-enumerations-in-class-designer).  
  
Progettazione classi supporta C++ `enum` e i tipi `enum class` con ambito. Di seguito è riportato un esempio:  
  
```  
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
  
 Per altre informazioni sull'uso del tipo `enum`, vedere [Enumerazioni](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del codice Visual C++ (Progettazione classi)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Enumerazioni](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)



