---
title: Enumerazioni Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: b9d88cb954e89cfd6401f674fbbbc901ac634982
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236359"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumerazioni Visual C++ in Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



