---
title: Timer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778115"
---
# <a name="timer"></a>Timer
L'opzione *Timer di * **VSPerfCmd.exe** imposta l'evento di profilatura campionato su cicli del clock del processore e, facoltativamente, modifica il numero di cicli in un intervallo di campionamento dal valore predefinito di 10.000.000. In un processore da 1 GH (un gigahertz), un valore di 10.000.000 cicli di clock è pari a circa 100 campioni al secondo. Il numero minimo di cicli che è possibile specificare è 50.000.

 L'opzione **Timer** può essere usata solo quando si usa il metodo di profilatura del campionamento e può essere usata solo in una riga di comando che include anche l'opzione **Launch** o **Attach**.

 Per impostazione predefinita, l'evento di campionamento del profiler è impostato sui cicli del clock del processore e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.

 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametri
 `Cycles` Valore intero che specifica il numero di cicli di clock del processore in un intervallo di campionamento. Se `Cycles` non è specificato, l'intervallo sarà impostato su 10.000.000. Specificare il valore senza virgole.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **Timer** può essere specificata solo in una riga di comando che include una delle opzioni seguenti.

 **Avvia:** `AppName` avvia il profiler e `AppName`l'applicazione specificata da .

 **Connetti:** `PID` connette il profiler al processo specificato dall'ID processo (`PID`).

## <a name="invalid-options"></a>Opzioni non valide
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **Timer**.

 **PF**[**:**`Events`] Imposta l'evento di campionamento su `Events`errori di pagina e, facoltativamente, imposta l'intervallo di campionamento su . L'intervallo PF predefinito è 10.

 **Sys**[**:**`Events`] Imposta l'evento di campionamento su `Events`chiamate del sistema operativo e, facoltativamente, imposta l'intervallo di campionamento su . L'intervallo Sys predefinito è 10.

 **Contatore**[**:**`Name,Reload,FriendlyName`] Imposta l'evento `Name` di campionamento sul `Reload`contatore delle prestazioni della CPU specificato da e imposta l'intervallo di campionamento su .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Raccoglie dati di memoria .NET. Per impostazione predefinita (**Allocazione**), i dati vengono raccolti a ogni evento di allocazione di memoria. Quando viene specificato il parametro **Lifetime,** i dati vengono raccolti anche a ogni evento di Garbage Collection.When the Lifetime parameter is specified, data is also collected at each garbage collection event.

## <a name="example"></a>Esempio
 Questo esempio illustra come impostare l'intervallo di campionamento del profiler su 1.000.000 cicli del processore.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
