---
title: 'DA0004: Utilizzo elevato del processore | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87f418c8f145d13dee575c9d45d192a59547e6a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920885"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Utilizzo elevato del processore

|||  
|-|-|  
|ID regola|DA0004|  
|Category|Uso degli strumenti di profilatura|  
|Metodi di profilatura|Strumentazione<br /><br /> Campionamento|  
|Messaggio|L'utilizzo del processore è costantemente superiore al 75%. Si consiglia di utilizzare la modalità di campionamento per le applicazioni basate sulla CPU.|  
|Tipo regola|Informazioni|  

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  

## <a name="cause"></a>Causa  
 L'utilizzo del processore (CPU) è elevato nei dati di profilatura raccolti usando il metodo di strumentazione. Si consiglia di usare il metodo di profilatura del campionamento per profilare applicazioni associate alla CPU.  

## <a name="rule-description"></a>Descrizione della regola  
 Durante l'esecuzione della profilatura, il processore o i processori sono stati occupati in modo coerente. Un utilizzo della CPU elevato può indicare un'applicazione basata sulla CPU. I profili instrumentati non rappresentano il modo più valido per esaminare gli scenari di utilizzo della CPU. Il campionamento è più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono istruzioni sul processore.  

## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ad eccezione dei casi in cui è necessaria la temporizzazione della funzione o si è più interessati a comprendere l'input/output che i colli di bottiglia del processore, è consigliabile eseguire nuovamente la profilatura dell'applicazione usando il metodo di campionamento anziché il metodo di strumentazione.