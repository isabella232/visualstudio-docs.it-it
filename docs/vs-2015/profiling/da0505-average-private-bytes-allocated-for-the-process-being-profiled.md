---
title: 'DA0505: Byte privati medi allocati per il processo sottoposto a profilatura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69a7eaeecd65ffdfbd575b59fbea15c476d0fbeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850871"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Byte privati medi allocati per il processo sottoposto a profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID regola | DA0505 |  
| Categoria | Gestione delle risorse |  
| Metodo di profilatura | Tutti |  
| Messaggio | Queste informazioni sono state raccolte a soli fini informativi. Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi. Il valore indicato corrisponde al valore medio calcolato per tutti gli intervalli di misurazione.|  
| Tipo di regola | Informazioni |  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo messaggio indica la quantità media di memoria virtuale che il processo ha attualmente allocato in byte (byte privati). I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.  
  
 Per i processi a 32 bit in esecuzione in un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Tramite l'opzione di Boot.ini [/3GB](https://msdn.microsoft.com/library/ff556232.aspx) i processi a 32 bit possono acquisire fino a 3 GB di memoria virtuale. Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.  
  
 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.  
  
 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.  
  
 Per altre informazioni sugli spazi degli indirizzi del processo, vedere [Virtual Address Space](https://msdn.microsoft.com/library/aa366912.aspx) (Spazio degli indirizzi virtuali) nella documentazione relativa alla gestione della memoria di Windows.  
  
## <a name="how-to-use-rule-data"></a>Come usare i dati della regola  
 Usare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.
