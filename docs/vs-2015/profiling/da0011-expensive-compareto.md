---
title: 'DA0011: Funzione CompareTo dispendiosa | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af5797a9e3939d3163d6d1cee9719f38036543ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720859"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Funzione compareTo dispendiosa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [DA0011 funzione: CompareTo dispendiosa](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) su docs.microsoft.com.  
  
|||  
|-|-|  
|ID regola|DA0011|  
|Category|Uso di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Memoria .NET|  
|Messaggio|Le funzioni CompareTo dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione CompareTo.|  
|Tipo regola|Avviso|  
  
## <a name="cause"></a>Causa  
 Il metodo CompareTo del tipo è dispendioso o alloca memoria.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi CompareTo dovrebbero essere efficienti e non allocare memoria.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ridurre la complessità del metodo CompareTo.

