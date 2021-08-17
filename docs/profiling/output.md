---
title: Output | Microsoft Docs
description: Informazioni su come l'opzione Output specifica il nome del file di dati di profilatura per la sessione di prestazioni. L'opzione Output deve essere usata con l'opzione Start.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c521362ecde12a5b996062f6f1e0d07992e26e06
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107108"
---
# <a name="output"></a>Output
L'opzione **Output** specifica il nome del file di dati di profilatura per la sessione di prestazioni. L'opzione **Output** deve essere usata con l'opzione **Start**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametri
 `FileName` Nome del file di dati. Sono accettati percorsi completi e parziali. Se non viene specificato un percorso, il file viene creato nella directory corrente.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **Output** deve essere usata con l'opzione **Start**.

 **Avvio:** `Method` Specifica il nome del file di output.

## <a name="example"></a>Esempio
 Nell'esempio seguente il file di dati di profilatura viene creato nella directory corrente.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
