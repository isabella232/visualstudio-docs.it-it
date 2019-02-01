---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a32de469c5b58ca2bf58901e30b81cfb70ed84b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803527"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare lo strumento della riga di comando **VsPerf** per:  
  
1. Eseguire la profilatura di app di Windows Store dalla riga di comando quando Visual Studio non è installato nel dispositivo.  
  
2. Eseguire la profilatura di applicazioni desktop Windows 8 e applicazioni Windows Server 2012 usando il metodo di profilatura di campionamento.  
  
   Per altre informazioni sulle opzioni di profilatura, vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 In questo argomento vengono descritte le opzioni che è possibile usare con lo strumento della riga di comando `vsperf.exe`. Di seguito sono elencate le diverse sezioni di questo argomento:  
  
 [Solo app di Windows Store](#BKMK_windows_store_apps_only)  
  
 [Solo applicazioni desktop Windows 8 e applicazioni Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Tutte le applicazioni](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Solo app di Windows Store  
 Queste opzioni si applicano solo alle app di Windows Store.  
  
|||  
|-|-|  
|**/app:{AppName}**|Avvia il profiler e attende che l'app specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare i valori Name e PackageFullName delle app installate.|  
|**/package:{PackageFullName}**|Avvia il profiler e attende che l'app specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare i valori Name e PackageFullName delle app installate.|  
|**/js**|Obbligatorio per la profilatura delle app JavaScript.<br /><br /> Raccogliere dati sulle prestazioni dalle app JavaScript.<br /><br /> Usare solo con /package o /attach.|  
|**/noclr**|Facoltativo. Non raccogliere dati CLR.<br /><br /> Usare solo con /package o /attach.<br /><br /> Ottimizzazione, non verrà eseguita la risoluzione di simboli gestiti.|  
|**/listapps**|Elencare i valori Name e PackageFullName delle app installate.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Solo applicazioni desktop Windows 8 e applicazioni Windows Server 2012  
 Queste opzioni non funzionano per le app di Windows Store.  
  
|||  
|-|-|  
|**/launch:{Executable}**|Avvia il file eseguibile specificato e ne esegue la profilatura.|  
|**/args:{ExecutableArguments}**|Specifica gli argomenti della riga di comando da passare alla destinazione **/launch**.|  
|**/console**|Esegue la destinazione **/launch** in una nuova finestra di comando.|  
  
##  <a name="BKMK_All_applications"></a> Tutte le applicazioni  
 Queste opzioni si applicano a tutte le applicazioni Windows 8 o Windows Server 2012.  
  
|||  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Raccoglie dati dai processi specificati.<br /><br /> Usare Gestione attività per visualizzare l'ID processo (PID) e i nomi dei processi delle app in esecuzione.|  
|**/file:{ReportName}**|Facoltativo. Specifica il file di output (sovrascrive il file esistente).<br /><br /> Usare solo con /package o /attach.|  
|**/pause**|Sospendere la raccolta dei dati.|  
|**/resume**|Riprendere la raccolta dei dati.|  
|**/stop**|Interrompere la raccolta dei dati e terminare i processi di destinazione.|  
|**/detach**|Interrompere la raccolta dei dati, senza arrestare l'esecuzione dei processi di destinazione.|  
|**/status**|Visualizzare lo stato del profiler.|  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
