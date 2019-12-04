---
title: CrossSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de982643a08e1af88073dde0fb0a9abc029900
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779454"
---
# <a name="crosssession"></a>CrossSession
L'opzione *CrossSession* di **VSPerfCmd.exe** consente al profiler di raccogliere dati da qualsiasi sessione della console. L'opzione **CrossSession** deve essere usata con l'opzione **Start**.

 È possibile usare l'abbreviazione **CS** al posto di **CrossSession**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametri
 nessuna

## <a name="valid-options"></a>Opzioni valide
 Per abilitare la profilatura in un'altra sessione, l'opzione **CrossSession** deve essere specificata con l'opzione **Start**. **CrossSession** deve essere specificata anche in tutti i comandi **Attach e Detach** di **VSPerfCmd**.

 **Start:** `Method` l'opzione **Start** Inizializza il profiler sul metodo di profilatura specificato.

 **Connetti:** _PID_[ **,** _PID_] avvia la profilatura dei processi specificati.

 **Detach**[ **:** _PID_[,_PID_]] Arresta la profilatura dei processi specificati.

## <a name="example"></a>Esempio
 In questo esempio l'opzione **CrossSession** viene usata per connettersi a un'applicazione che è stata avviata in un'altra sessione di console.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
