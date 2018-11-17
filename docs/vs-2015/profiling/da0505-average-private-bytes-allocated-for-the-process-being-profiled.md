---
title: 'DA0505: Byte privati medi allocati per il processo sottoposto a profilatura | Microsoft Docs'
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
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60f1bce7fe6f0199928e68dcc86b5062e327209a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789954"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Byte privati medi allocati per il processo sottoposto a profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0505 |  
| Categoria | Gestione delle risorse |  
| Metodo di profilatura | Tutti i |  
| Messaggio | Dati raccolti a solo scopo informativo. Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi. Il valore restituito viene calcolata la media per tutti gli intervalli di misurazione. |  
| Tipo di regola | Informazioni |  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo messaggio indica la quantità media di memoria virtuale che il processo ha attualmente allocato in byte (byte privati). I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.  
  
 Per i processi a 32 bit in esecuzione in un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Tramite l'opzione di Boot.ini [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) i processi a 32 bit possono acquisire fino a 3 GB di memoria virtuale. Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.  
  
 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.  
  
 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.  
  
 Per altre informazioni sugli spazi degli indirizzi del processo, vedere [Virtual Address Space](http://go.microsoft.com/fwlink/?LinkId=177832) (Spazio degli indirizzi virtuali) nella documentazione relativa alla gestione della memoria di Windows.  
  
## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 Usare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.



