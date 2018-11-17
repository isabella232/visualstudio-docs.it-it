---
title: 'DA0002: VSPerfCorProf.dll mancante | Microsoft Docs'
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
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1359b525b286dbc88cbd3d8eecaef27060ab23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809467"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll mancante
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0002 |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodi di profilatura | Profilatura tramite gli strumenti da riga di comando VSPerfCmd e VSPerfASPNETCmd |  
| Messaggio | Sembra che il file è stato raccolto senza impostare correttamente le variabili di ambiente con VSPerfCLREnv. cmd. I simboli per i file binari gestiti non possono essere risolti. |  
| Tipo di regola | Informazioni |  
  
## <a name="cause"></a>Causa  
 Il profiler non è in grado di trovare VSPerfCorProf.dll durante l'esecuzione della profilatura. Questo avviso si verifica quando vengono usati gli strumenti da riga di comando per la raccolta di dati del profiler senza usare lo strumento VSPerfCLREnv.cmd per inizializzare le variabili di ambiente necessarie. L'avviso può essere generato anche se un altro profiler è in esecuzione all'avvio degli strumenti di profilatura.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Prima di eseguire la profilatura è necessario impostare variabili di ambiente specifiche per consentire al profiler di risolvere i simboli nei file binari di .NET Framework. Questo avviso indica che lo strumento VSPerfCLREnv.cmd non è stato eseguito prima della raccolta dei dati di profilatura. È possibile che i simboli per i file binari gestiti non vengano risolti. Per altre informazioni sull'uso degli strumenti di profilatura dalla riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Quando si profilano applicazioni gestite usando gli strumenti da riga di comando negli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eseguire lo strumento da riga di comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) prima di iniziare la raccolta dei dati.



