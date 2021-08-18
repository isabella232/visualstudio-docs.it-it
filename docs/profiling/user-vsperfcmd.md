---
title: User (VSPerfCmd) | Microsoft Docs
description: Informazioni su come l'opzione Utente specifica il dominio e il nome utente dell'account proprietario del processo profilato.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 015cca1c11050f2bd34fa5b6eb8292b014b61856
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140797"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
L'opzione **User** specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda **Processi** di Gestione attività di Windows.

 L'opzione **User** può essere specificata solo in una riga di comando che contiene anche l'opzione **Start**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametri
 `Domain` Nome del dominio dell'utente.

 `UserName` Nome dell'utente.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **User** può essere usata solo con l'opzione **Start**.

 **Avvio:** `Method` Inizializza il profiler sul metodo di profilatura specificato.

## <a name="example"></a>Esempio
 L'esempio seguente illustra l'uso dell'opzione **User**.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
