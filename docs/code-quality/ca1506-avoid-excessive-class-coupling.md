---
title: 'CA1506: Evitare un numero eccessivo di accoppiamenti | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 018abf05181be812bcf01fc9cb910745dc085bcf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitare un numero eccessivo di accoppiamenti di classi
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo o metodo è associata a molti altri tipi.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.  
  
 Tipi e metodi che presentano un elevato livello di accoppiamenti di classi possono essere difficili da gestire. È consigliabile disporre di tipi e metodi che presentano accoppiamento bassa e coesione elevata.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere questa violazione, provare a riprogettare il tipo o un metodo per ridurre il numero di tipi a cui è associata.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere questo avviso quando il tipo o metodo è considerata accettabile, nonostante il numero elevato di dipendenze da altri tipi.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)   
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)