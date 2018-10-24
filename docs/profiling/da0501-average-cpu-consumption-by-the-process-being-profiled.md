---
title: 'DA0501: Consumo medio CPU del processo sottoposto a profilatura. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9612c895f7453d250b4f37c06e3630901602685
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847112"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Consumo medio CPU del processo sottoposto a profilatura.

|||  
|-|-|  
|ID regola|DA501|  
|Category|Monitoraggio risorse|  
|Metodo di profilatura|Tutti|  
|Messaggio|Consumo medio CPU del processo sottoposto a profilatura.|  
|Tipo regola|Informazioni|  

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  

## <a name="rule-description"></a>Descrizione della regola  
 In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo. In un computer con più processori il valore può essere maggiore del 100%.  

## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 Usare il valore della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di test diversi.