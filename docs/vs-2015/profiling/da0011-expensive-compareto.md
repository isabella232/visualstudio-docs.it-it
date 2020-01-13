---
title: 'DA0011: Funzione CompareTo dispendiosa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ed433612498a6b7d4b87291311d7fd6efcb0974
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918381"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Funzione compareTo dispendiosa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [DA0011: CompareTo costoso](/visualstudio/profiling/da0011-expensive-compareto).  
  
|||  
|-|-|  
|ID regola|DA0011|  
|Categoria|Uso di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Memoria .NET|  
|Messaggio|Le funzioni CompareTo dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione CompareTo.|  
|Tipo regola|Avviso|  
  
## <a name="cause"></a>Causa  
 Il metodo CompareTo del tipo è dispendioso o alloca memoria.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi CompareTo dovrebbero essere efficienti e non allocare memoria.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ridurre la complessità del metodo CompareTo.
