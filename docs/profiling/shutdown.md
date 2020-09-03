---
title: Shutdown | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64bad66491588178dc7d80655a8e517d6daed053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330995"
---
# <a name="shutdown"></a>Shutdown
L'opzione **Shutdown** attende il termine o la disconnessione di qualsiasi processo in corso di profilatura, quindi disattiva il profiler e chiude il file di dati di profilatura. L'opzione **Shutdown** deve essere l'ultimo comando di un'esecuzione di profilatura.

 Se non si specifica un parametro di timeout, l'opzione **Shutdown** attende per un tempo illimitato. Se si specifica un parametro di timeout, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati.

 L'opzione **Shutdown** deve essere l'unica opzione specificata nella riga di comando.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametri
`Timeout`
- (Facoltativo) Se specificata, l'opzione restituisce il controllo dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati di profilatura.

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
