---
title: Shutdown | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9b8848399ea88b5f4ce7ebf30f970e2091e6406
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54784599"
---
# <a name="shutdown"></a>Arresta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **Shutdown** attende il termine o la disconnessione di qualsiasi processo in corso di profilatura, quindi disattiva il profiler e chiude il file di dati di profilatura. L'opzione **Shutdown** deve essere l'ultimo comando di un'esecuzione di profilatura.  
  
 Se non si specifica un parametro di timeout, l'opzione **Shutdown** attenderà per un tempo illimitato. Se si specifica un parametro di timeout, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati.  
  
 L'opzione **Shutdown** deve essere l'unica opzione specificata nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Timeout`  
 -   (Facoltativo) Se specificata, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati di profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)
