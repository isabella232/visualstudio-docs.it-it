---
title: 'DA0010: Funzione GetHashCode dispendiosa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 111e3204224f1124476ab2a324df7be2b6ef2525
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354830"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Funzione GetHashCode dispendiosa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [DA0010 funzione: GetHashCode dispendiosa](https://docs.microsoft.com/visualstudio/profiling/da0010-expensive-gethashcode) su docs.microsoft.com.  

  

|||  
|-|-|  
|ID regola|DA0010|  
|Category|Uso di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Memoria .NET|  
|Messaggio|Le funzioni GetHashCode dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione di codice hash.|  
|Tipo messaggio|Avviso|  
  
## <a name="cause"></a>Causa  
 Le chiamate al metodo GetHashCode del tipo rappresentano una percentuale significativa dei dati di profilatura o il metodo alloca memoria.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Hash è una tecnica per individuare rapidamente un particolare elemento in una raccolta di grandi dimensioni. Poiché possono avere dimensioni molto grandi e devono supportare frequenze di accesso molto elevate, le tabelle hash devono essere estremamente efficienti. Per questa ragione, i metodi GetHashCode in .NET Framework non devono allocare memoria. L'allocazione di memoria aumenta il carico del Garbage Collector ed espone il metodo a possibili ritardi se diventa necessario eseguire l'operazione di Garbage Collection in seguito alla richiesta di allocazione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ridurre la complessità del metodo.
