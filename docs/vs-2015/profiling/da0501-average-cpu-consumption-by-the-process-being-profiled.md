---
title: 'DA0501: Consumo medio CPU del processo sottoposto a profilatura. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155781"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Consumo medio CPU del processo sottoposto a profilatura.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID regola | DA501 |  
| Categoria | Monitoraggio delle risorse |  
| Metodo di profilatura | Tutti |  
| Messaggio | Consumo medio della CPU da parte del processo sottofilato. |  
| Tipo di regola | Informazioni |  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo. In un computer con più processori il valore può essere maggiore del 100%.  
  
## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 Usare il valore della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di test diversi.
