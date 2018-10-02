---
title: 'DA0008: Numero ridotto di campioni raccolti | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205bedf2baa7c9fa1e1c5f40ccbaa4041427074b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540865"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Numero ridotto di campioni raccolti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DA0008 numero ridotto: numero ridotto di campioni raccolti](https://docs.microsoft.com/visualstudio/profiling/da0008-few-samples-collected).  
  
Id regola | DA0008 NUMERO RIDOTTO |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodo di profilatura | Campionamento |  
| Messaggio | Sono stati raccolti solo pochi campioni. Prendere in considerazione una frequenza di campionamento più veloce o esecuzione più lungo per ottenere risultati più significativi. |  
| Tipo di regola | Informazioni |  
  
## <a name="cause"></a>Causa  
 Durante l'esecuzione della profilatura sono stati raccolti solo alcuni campioni.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando viene usato il metodo di campionamento, è necessario raccogliere un numero di campioni statisticamente significativo per assicurarsi che i dati siano rappresentativi dell'effettivo comportamento del programma. Per ridurre al minimo gli errori di campionamento, provare a raccogliere almeno 1000 campioni di comportamento dell'esecuzione delle istruzioni del programma. Se non si raccoglie un numero sufficiente di campioni è possibile che l'analisi dei dati di profilatura porti a conclusioni fuorvianti.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 È consigliabile profilare un'esecuzione più lunga dell'applicazione o usare una frequenza di campionamento più elevata per ottenere risultati significativi a livello statistico. Per informazioni su come modificare la frequenza di campionamento nell'IDE di Visual Studio, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md). Per altre informazioni sulla modifica della frequenza di campionamento quando si usa la riga di comando degli strumenti di profilatura, vedere [Timer](../profiling/timer.md) nel riferimento di [VSPerfCmd](../profiling/vsperfcmd.md).



