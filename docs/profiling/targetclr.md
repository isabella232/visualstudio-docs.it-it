---
title: TargetCLR | Microsoft Docs
description: Informazioni su come l'opzione TargetCLR specifica la versione del runtime di Common Language da profilare quando più di una versione di CLR viene caricata in un'applicazione.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 083f650992a931686e49d878df1e2c323bd45f3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141259"
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

 **Avviare:** `AppName` Avvia l'applicazione specificata e inizia a profilare.

 **Collega:** `PID` Inizia a profilare il processo specificato.

## <a name="example"></a>Esempio
 In questo esempio, l'opzione TargetCLR viene usata per assicurarsi che venga sottoposta a profilatura la versione di CLR 4.0.11003.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
