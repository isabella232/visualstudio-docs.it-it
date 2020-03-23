---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778180"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
L'opzione *Sys di * **VSPerfCmd.exe** imposta l'evento di profilatura campionato per gli eventi di chiamata del sistema (chiamate di funzione dall'applicazione profilata al sistema operativo) e, facoltativamente, modifica il numero di chiamate del sistema in un intervallo di campionamento rispetto al valore predefinito 10.

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

 **Avvia:** `AppName` avvia il profiler e `AppName`l'applicazione specificata da .

 **Connetti:** `PID` connette il profiler al processo `PID`specificato da .

## <a name="invalid-options"></a>Opzioni non valide
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **Sys**.

 **PF**[**:**`Events`] Imposta l'evento di campionamento su `Events`errori di pagina e, facoltativamente, imposta l'intervallo di campionamento su . L'intervallo PF predefinito è 10.

 **Timer**[**:**`Cycles`] Imposta l'evento di campionamento su `Cycles`cicli di clock del processore e, facoltativamente, imposta l'intervallo di campionamento su . L'intervallo Timer predefinito è 10.000.000.

 **Contatore:** `Name``,Reload``,FriendlyName`[ [ ]] Imposta l'evento `Name` di campionamento sul `Reload`contatore delle prestazioni della CPU specificato da e imposta l'intervallo di campionamento su .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Raccoglie dati di memoria .NET. Per impostazione predefinita (**Allocazione**), i dati vengono raccolti a ogni evento di allocazione di memoria. Quando viene specificato il parametro **Lifetime,** i dati vengono raccolti anche a ogni evento di Garbage Collection.When the Lifetime parameter is specified, data is also collected at each garbage collection event.

## <a name="example"></a>Esempio
 Questo esempio illustra come impostare l'evento di campionamento del profiler sulle chiamate del sistema e come impostare l'intervallo di campionamento su 20 chiamate per campione.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
