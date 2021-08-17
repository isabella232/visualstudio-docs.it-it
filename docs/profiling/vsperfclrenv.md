---
title: VSPerfCLREnv | Microsoft Docs
description: Informazioni su come viene usato lo strumento VSPerfCLREnv per impostare le variabili di ambiente necessarie per profilare un'.NET Framework applicazione.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c7c9edcb96b8fa1383abc6e00bc1573cf0dc112afc14abb8465c469d2c7153db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121353955"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Lo strumento VSPerfCLREnv viene utilizzato per impostare le variabili di ambiente che sono necessarie per profilare un'applicazione .NET Framework. Viene usata la sintassi seguente:

```cmd
VsPerfCLREnv [/option]
```

L'opzione scelta dipende da quale dei tre tipi di profilatura si vuole usare: campionamento, strumentazione o globale. È necessaria un'opzione distinta per includere i dati di interazione tra livelli nei dati di profilatura. Nelle tabelle seguenti è descritta la sintassi per ogni opzione.

> [!NOTE]
> Al termine della profilatura, eseguire **VSPerfCLREnv** con l'opzione **/off** o **/globaloff** per eliminare le variabili di ambiente necessarie per la profilatura. Per altre informazioni, vedere di seguito Opzioni di VSPerfCLREnv per l'eliminazione delle impostazioni di ambiente.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Opzioni di VSPerfCLREnv per l'inclusione dei dati di interazione tra livelli

> [!WARNING]
> I dati di profilatura dell'interazione tra livelli possono essere raccolti usando qualsiasi edizione di Visual Studio, ma possono essere visualizzati solo in Visual Studio Enterprise.

La profilatura di interazione tra livelli fornisce informazioni aggiuntive sulle query ADO.NET nelle applicazioni a più livelli. I dati vengono raccolti solo per le chiamate di funzione sincrone. I dati di interazione possono essere aggiunti a qualsiasi esecuzione di profilatura usando qualsiasi metodo di profilatura.

Le opzioni **InteractionOn** e **GlobalInteractionOn** consentono la raccolta di dati di interazione tra livelli. L'opzione di interazione deve essere impostata dopo l'impostazione della variabile di ambiente VSPerfCLREnv che è necessaria per la profilatura di un'applicazione.

L'esempio seguente include i dati di interazione tra livelli in un'esecuzione di profilatura che usa il metodo di campionamento:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

L'esempio seguente include i dati di interazione tra livelli in un'esecuzione di profilatura per un servizio Windows:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Opzioni di VSPerfCLREnv per la profilatura tramite strumentazione di processi

Nella tabella seguente sono descritte le opzioni di VSPerfCLREnv per la profilatura tramite strumentazione:

|Opzione|Descrizione|
|------------|-----------------|
|**TraceOn**|Abilita la profilatura tramite il metodo di strumentazione. Non abilita la profilatura dell'allocazione di memoria o la raccolta dei dati di durata degli oggetti.|
|**TraceGC**|Abilita la profilatura dell'allocazione di memoria con il metodo di strumentazione. Non abilita la raccolta dei dati di durata degli oggetti.|
|**TraceGCLife**|Abilita la profilatura dell'allocazione di memoria e la raccolta dei dati sulla durata degli oggetti usando il metodo di strumentazione.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Opzioni di VSPerfCLREnv per la profilatura tramite campionamento di processi

Nella tabella seguente sono descritte le opzioni di VSPerfCLREnv per la profilatura tramite campionamento:

|Opzione|Descrizione|
|------------|-----------------|
|**SampleOn**|Abilita la profilatura tramite il metodo di campionamento. Non abilita la profilatura dell'allocazione di memoria o la raccolta dei dati di durata degli oggetti.|
|**SampleGC**|Abilita la profilatura dell'allocazione di memoria con il metodo di campionamento. Non abilita la raccolta dei dati di durata degli oggetti.|
|**SampleGCLife**|Abilita la profilatura dell'allocazione di memoria con il metodo di campionamento. Abilita anche la raccolta dei dati di durata degli oggetti.|
|**SampleLineOff**|Disabilita la raccolta dei dati di profilatura a livello di riga .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Opzioni di VSPerfCLREnv per la profilatura globale

Per eseguire la profilatura di un servizio gestito, ad esempio un'applicazione Web ASP.NET avviata dal sistema operativo anziché dall'utente, usare le opzioni per la profilatura globale di VSPerfCLREnv. Nella tabella seguente sono descritte le versioni globali delle opzioni di VSPerfCLREnv. Queste opzioni impostano le variabili di ambiente appropriate nel Registro di sistema.

|Opzione|Descrizione|
|------------|-----------------|
|**GlobalTraceOn**|Abilita la profilatura globale tramite il metodo di strumentazione. Non raccoglie eventi di allocazione della memoria o dati sulla durata degli oggetti.|
|**GlobalTraceGC**|Abilita la profilatura dell'allocazione di memoria con il metodo di strumentazione. Non abilita la raccolta dei dati di durata degli oggetti.|
|**GlobalTraceGCLife**|Abilita la profilatura dell'allocazione di memoria con il metodo di strumentazione. Abilita anche la raccolta dei dati di durata degli oggetti.|
|**GlobalSampleOn**|Abilita la profilatura globale tramite il metodo di campionamento. Non abilita la raccolta di eventi di allocazione della memoria o dati sulla durata degli oggetti.|
|**GlobalSampleGC**|Abilita la profilatura dell'allocazione di memoria con il metodo di campionamento. Non abilita la raccolta dei dati di durata degli oggetti.|
|**GlobalSampleGCLife**|Abilita la profilatura dell'allocazione di memoria con il metodo di campionamento. Abilita anche la raccolta dei dati di durata degli oggetti.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Opzioni di VSPerfCLREnv per l'eliminazione delle impostazioni di ambiente

 Al termine della profilatura dell'applicazione gestita, usare una delle seguenti opzioni per eliminare le variabili di ambiente che sono state aggiunte da VSPerfCLREnv. Nella tabella seguente viene descritto come eliminare le variabili di ambiente locali e globali:

|Opzione|Descrizione|
|------------|-----------------|
|**Disattivato**|Elimina le variabili di ambiente per la profilatura .NET standard. Usare questa opzione quando sono state usate le opzioni di VSPerfClrEnv non globali per impostare le variabili di ambiente del profiler.|
|**GlobalOff**|Elimina le variabili di ambiente per la profilatura .NET globale. Usare questa opzione quando l'applicazione è stata avviata dal sistema operativo anziché dal profiler.|

## <a name="remarks"></a>Commenti

Queste opzioni non sono necessarie per la profilatura di un'applicazione gestita se l'applicazione viene avviata usando Esplora prestazioni nell'IDE. Esplora prestazioni imposta automaticamente tutte le impostazioni di ambiente necessarie.

Se non è stato impostato l'ambiente corretto durante la profilatura, sarà visualizzato un avviso durante l'analisi e la risoluzione dei nomi di funzione non verrà eseguita correttamente.

## <a name="see-also"></a>Vedi anche

[Usare gli strumenti per la profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
