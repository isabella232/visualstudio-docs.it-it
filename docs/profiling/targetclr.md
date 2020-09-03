---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74771601"
---
# <a name="targetclr"></a>TargetCLR
L'opzione **TargetCLR** specifica la versione di Common Language Runtime (CLR) da sottoporre a profilatura quando in un'applicazione è caricata più di una versione di CLR.

 Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono applicati alla prima versione di CLR caricata dall'applicazione.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametri
 `ClrVersion` Numero di versione del CLR. Usare il formato di versione **vN.N.NNNNN**.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **TargetCLR** può essere usata solo con le opzioni **Launch** o **Attach**.

 **Avvia:** `AppName` Avvia l'applicazione specificata e inizia a eseguire la profilatura.

 **Connetti:** `PID` Inizia a profilare il processo specificato.

## <a name="example"></a>Esempio
 In questo esempio, l'opzione TargetCLR viene usata per assicurarsi che venga sottoposta a profilatura la versione di CLR 4.0.11003.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
