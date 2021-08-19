---
title: Sys (VSPerfCmd) | Microsoft Docs
description: Informazioni su come lVSPerfCmd.exe Sys imposta l'evento di profilatura campionato sugli eventi di chiamata di sistema.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c5f1f0908e3696f2f1172b50fb793b030100a9a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157072"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*L'opzioneVSPerfCmd.exe* **Sys** imposta l'evento di profilatura campionato in eventi di chiamata di sistema (chiamate di funzione dall'applicazione profilata al sistema operativo) e, facoltativamente, modifica il numero di chiamate di sistema in un intervallo di campionamento dal valore predefinito 10.

 L'opzione **Sys** può essere usata solo in una riga di comando che contiene anche l'opzione **Launch** o l'opzione **Attach**.

 Per impostazione predefinita, l'evento di campionamento del profiler è impostato sui cicli del clock del processore e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.

 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametri
 `Events` Valore intero che specifica il numero di eventi di chiamata di sistema in un intervallo di campionamento. Se non si specifica `Events`, l'intervallo viene impostato su 10.

## <a name="required-options"></a>Opzioni obbligatorie
 **Sys** richiede una delle opzioni seguenti.

 **Avviare:** `AppName` Avvia il profiler e l'applicazione specificata da `AppName` .

 **Collega:** `PID` Collega il profiler al processo specificato da `PID` .

## <a name="invalid-options"></a>Opzioni non valide
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **Sys**.

 **PF**[**:** `Events` ] Imposta l'evento di campionamento su errori di pagina e facoltativamente imposta l'intervallo di campionamento su `Events` . L'intervallo PF predefinito è 10.

 **Timer**[**:** `Cycles` ] Imposta l'evento di campionamento su cicli di clock del processore e facoltativamente imposta l'intervallo di campionamento su `Cycles` . L'intervallo Timer predefinito è 10.000.000.

 **Contatore:** `Name` [ `,Reload` [ `,FriendlyName` ]] Imposta l'evento di campionamento sul contatore delle prestazioni CPU specificato da `Name` e imposta l'intervallo di campionamento su `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Raccoglie dati di memoria .NET. Per impostazione predefinita (**Allocazione**), i dati vengono raccolti a ogni evento di allocazione della memoria. Quando si **specifica il parametro Lifetime,** i dati vengono raccolti anche a ogni evento di Garbage Collection.

## <a name="example"></a>Esempio
 Questo esempio illustra come impostare l'evento di campionamento del profiler sulle chiamate del sistema e come impostare l'intervallo di campionamento su 20 chiamate per campione.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
