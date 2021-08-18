---
title: Events (VSPerfCmd) | Microsoft Docs
description: Controllare la registrazione di Event Tracing for Windows (ETW) usando l'opzione Events nello VSPerfCmd.exe della riga di comando. Esaminare i parametri della sintassi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 268efb7e76ea4b2357b0ef1047ee2076f340dc29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038994"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
LVSPerfCmd.exe **eventi di registrazione** controlla la registrazione ETW (Event Tracing for Windows). I dati ETW vengono salvati in un file ETL separato dal file di dati del profiler. I dati possono essere visualizzati in un report usando il comando di [VSPerfReport](../profiling/vsperfreport.md) /summary: ETW.

 L'opzione **Events** può essere chiamata in qualsiasi momento prima di chiamare il comando **Shutdown** di VSPerfCmd per arrestare la profilatura.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametri
 **On**&#124;**Off** Avvia o arresta la raccolta dei dati dell'evento.

 `Guid` GUID del controllo provider.

 `ProviderName` Nome del provider registrato con Strumentazione gestione Windows (WMI).

 `Flags` Valore di flag esadecimale con prefisso "0x" definito dal provider di eventi.

 `Level` Specifica la quantità di dati raccolti. `Level` è definito dal provider di eventi.

 L'opzione **Events** riconosce le seguenti parole chiave del kernel come nomi di provider:

 **Process** Eventi dei processi

 **Thread** Eventi dei thread

 **Image** Eventi di caricamento e scaricamento di immagini

 **Disk** Eventi di I/O dei dischi

 **File** Eventi di I/O dei file

 **Hardfault** Errori di pagina hardware

 **Pagefault** Errori di pagina software

 **Network** Eventi di rete

 **Registry** Eventi di accesso al Registro di sistema

 Si noti che il provider del Kernel può solo essere abilitato. Non può essere disattivato, né i relativi flag possono essere modificati, finché il monitor non viene chiuso.

## <a name="remarks"></a>Commenti

> [!NOTE]
> Quando sono abilitati gli eventi ETW di CLR i dati di avvio aggiuntivi vengono raccolti anche nel report della visualizzazione tracce. Per evitare che gli eventi di avvio vengano visualizzati nel report, usare il comando seguente:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Se non si escludono gli eventi di avvio, poiché non sono elencati nel file MOF (Managed Object Format), tali eventi vengono visualizzati come GUID nel report. Per altre informazioni, vedere la pagina [File di esempio Managed Object Format (MOF)](https://msdn.microsoft.com/library/default.aspx) nel sito Web Microsoft.

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
