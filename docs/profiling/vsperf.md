---
title: VSPerf | Microsoft Docs
description: Informazioni su come usare lo strumento da riga di comando VsPerf per profilare le app UWP dalla riga di comando quando Visual Studio non è installato nel dispositivo.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b95493e94da7a64603ae8330b742b35b8ffeb276
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140609"
---
# <a name="vsperf"></a>VSPerf
Usare lo strumento della riga di comando **VsPerf** per:

1. Eseguire la profilatura di app UWP dalla riga di comando quando Visual Studio non è installato nel dispositivo.

2. Eseguire la profilatura di applicazioni desktop Windows 8 e applicazioni Windows Server 2012 usando il metodo di profilatura di campionamento.

   Per altre informazioni sulle opzioni di profilatura, vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Solo app UWP
 Queste opzioni si applicano solo alle app UWP.

|Opzione|Descrizione|
|-|-|
|**/app:{AppName}**|Avvia il profiler e attende che l'app specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare i valori Name e PackageFullName delle app installate.|
|**/package:{PackageFullName}**|Avvia il profiler e attende che l'app specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare i valori Name e PackageFullName delle app installate.|
|**/js**|Obbligatorio per la profilatura delle app JavaScript.<br /><br /> Raccogliere dati sulle prestazioni dalle app JavaScript.<br /><br /> Usare solo con /package o /attach.|
|**/noclr**|facoltativo. Non raccogliere dati CLR.<br /><br /> Usare solo con /package o /attach.<br /><br /> Ottimizzazione, non verrà eseguita la risoluzione di simboli gestiti.|
|**/listapps**|Elencare i valori Name e PackageFullName delle app installate.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Solo applicazioni desktop Windows 8 e applicazioni Windows Server 2012
 Queste opzioni non funzionano per le app UWP.

|Opzione|Descrizione|
|-|-|
|**/launch:{Executable}**|Avvia il file eseguibile specificato e ne esegue la profilatura.|
|**/args:{ExecutableArguments}**|Specifica gli argomenti della riga di comando da passare alla destinazione **/launch**.|
|**/console**|Esegue la destinazione **/launch** in una nuova finestra di comando.|

## <a name="all-applications"></a>Tutte le applicazioni
 Queste opzioni si applicano a tutte le applicazioni Windows 8 o Windows Server 2012.

|Opzione|Descrizione|
|-|-|
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Raccoglie dati dai processi specificati.<br /><br /> Usare Gestione attività per visualizzare l'ID processo (PID) e i nomi dei processi delle app in esecuzione.|
|**/file:{ReportName}**|facoltativo. Specifica il file di output (sovrascrive il file esistente).<br /><br /> Usare solo con /package o /attach.|
|**/pause**|Sospendere la raccolta dei dati.|
|**/resume**|Riprendere la raccolta dei dati.|
|**/stop**|Interrompere la raccolta dei dati e terminare i processi di destinazione.|
|**/detach**|Interrompere la raccolta dei dati, senza arrestare l'esecuzione dei processi di destinazione.|
|**/status**|Visualizzare lo stato del profiler.|

## <a name="see-also"></a>Vedi anche
- [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Usare gli strumenti per la profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
