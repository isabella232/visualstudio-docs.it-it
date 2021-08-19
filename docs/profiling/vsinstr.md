---
title: VSInstr | Microsoft Docs
description: Informazioni su come viene usato lo strumento VSInstr per instrumentare i file binari e su altre diverse opzioni dello strumento VSInstr.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dfa8e4fda1200a9e364ef689c8eef32d2771baf7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156812"
---
# <a name="vsinstr"></a>VSInstr
Lo strumento VSInstr viene usato per instrumentare i file binari. Viene richiamato tramite la sintassi seguente:

```cmd
VSInstr [/U] filename [/options]
```

 Nella tabella seguente vengono descritte le opzioni dello strumento VSInstr:

|Opzioni|Descrizione|
|-------------|-----------------|
|**Guida** o **?**|Visualizza la Guida.|
|**U**|Scrive l'output di console reindirizzato come Unicode. Deve essere la prima opzione specificata.|
|`@filename`|Specifica il nome di un file di risposta che contiene un'opzione di comando per riga.  Non usare virgolette.|
|**OutputPath**`:path`|Specifica una directory di destinazione per l'immagine instrumentata. Se non si specifica un percorso di output, il file binario originale viene rinominato aggiungendo "Orig" al nome del file nella stessa directory e viene instrumentata una copia del file binario.|
|**Escludi:**`funcspec`|Indica una specifica di funzione da escludere dalla strumentazione tramite probe. È utile quando l'inserimento di probe di profilatura in una funzione causa risultati imprevedibili o indesiderati.<br /><br /> Non usare opzioni **Exclude** e **Include** che fanno riferimento a funzioni nello stesso file binario.<br /><br /> È possibile specificare più specifiche di funzione con opzioni **Exclude** distinte.<br /><br /> `funcspec` è definito come:<br /><br /> [spazio dei nomi \<separator1> ] [classe \<separator2> ] Funzione<br /><br /> \<separator1> è `::` per il codice nativo e per il codice `.` gestito.<br /><br /> \<separator2> è sempre `::`<br /><br /> L'opzione **Exclude** è supportata con il code coverage.<br /><br /> È supportato il carattere jolly \*. Ad esempio, per escludere tutte le funzioni in uno spazio dei nomi, usare:<br /><br /> MyNamespace::\*<br /><br /> È possibile usare **VSInstr /DumpFuncs** per ottenere un elenco dei nomi completi delle funzioni nel file binario specificato.|
|**Include:** `funcspec`|Indica una specifica di funzione in un file binario da instrumentare tramite probe. Tutte le altre funzioni nei file binari non vengono instrumentate.<br /><br /> È possibile specificare più specifiche di funzione con opzioni **Include** distinte.<br /><br /> Non usare opzioni **Include** ed **Exclude** che fanno riferimento a funzioni nello stesso file binario.<br /><br /> L'opzione **Include** non è supportata con il code coverage.<br /><br /> `funcspec` è definito come:<br /><br /> [spazio dei nomi \<separator1> ] [classe \<separator2> ] Funzione<br /><br /> \<separator1> è `::` per il codice nativo e per il codice `.` gestito.<br /><br /> \<separator2> è sempre `::`<br /><br /> È supportato il carattere jolly \*. Ad esempio, per includere tutte le funzioni in uno spazio dei nomi, usare:<br /><br /> MyNamespace::\*<br /><br /> È possibile usare **VSInstr /DumpFuncs** per ottenere un elenco dei nomi completi delle funzioni nel file binario specificato.|
|**DumpFuncs**|Elenca le funzioni nell'immagine specificata. Non viene eseguita alcuna strumentazione.|
|**ExcludeSmallFuncs**|Esclude dalla strumentazione le funzioni piccole, ovvero funzioni brevi che non effettuano alcuna chiamata di funzione. L'opzione **ExcludeSmallFuncs** riduce il sovraccarico di strumentazione, aumentando la velocità di strumentazione.<br /><br /> L'esclusione delle piccole funzioni riduce anche la dimensione del file con estensione *vsp* e il tempo necessario per l'analisi.|
|**Mark:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname,markid`|Inserisce un contrassegno del profilo (un identificatore usato per delimitare i dati nei report) che è possibile usare per identificare l'inizio o la fine di un intervallo di dati nel file di report con estensione vsp.<br /><br /> **Before** - Subito prima dell'ingresso nella funzione di destinazione.<br /><br /> **After** - Subito dopo l'uscita dalla funzione di destinazione.<br /><br /> **Top:** immediatamente dopo la voce della funzione di destinazione.<br /><br /> **Bottom** - Subito prima di ogni restituzione del controllo nella funzione di destinazione.<br /><br /> `funcname` - Nome della funzione di destinazione.<br /><br /> `Markid` - Numero intero positivo (long) da usare come identificatore del contrassegno del profilo.|
|**Copertura**|Esegue la strumentazione di tipo code coverage. Può essere usato solo con le opzioni seguenti: **Verbose**, **OutputPath**, **Exclude** e **Logfile**.|
|**Verbose**|L'opzione **Verbose** consente di visualizzare informazioni dettagliate sul processo di strumentazione.|
|**NoWarn**`[:[Message Number[;Message Number]]]`|Elimina tutti gli avvisi o avvisi specifici.<br /><br /> `Message Number` - Numero di avviso. Se `Message Number` viene omesso, vengono eliminati tutti gli avvisi.<br /><br /> Per altre informazioni, vedere [Avvisi di VSInstr](../profiling/vsinstr-warnings.md).|
|**Controllo:** `{` **Thread** \| **Processo** \| **Globale**`}`|Specifica il livello di profilatura delle seguenti opzioni di controllo della raccolta dei dati di VSInstr:<br /><br /> **Inizia**<br /><br /> **StartOnly**<br /><br /> **Sospendi**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** -Specifica le funzioni di controllo della raccolta dei dati a livello di thread. La profilatura viene avviata o arrestata solo per il thread corrente. Lo stato di profilatura degli altri thread non è interessato. Il valore predefinito è Thread.<br /><br /> **Process** -Specifica le funzioni di controllo della raccolta dei dati di profilatura a livello di processo. La profilatura viene avviata o arrestata per tutti i thread nel processo corrente. Lo stato di profilatura di altri processi non è interessato.<br /><br /> **Global** -Specifica le funzioni di controllo della raccolta dei dati (su diversi processi) a livello globale.<br /><br /> Se non si specifica il livello di profilatura, si verifica un errore.|
|**Avvio:** `{` **All'interno** \| **Esterno**`},funcname`|Limita la raccolta dei dati alla funzione di destinazione e alle funzioni figlio chiamate da tale funzione.<br /><br /> **Inside** - Inserisce la funzione StartProfile subito dopo l'ingresso nella funzione di destinazione. Inserisce la funzione StopProfile subito prima di ogni restituzione nella funzione di destinazione.<br /><br /> **Outside** - Inserisce la funzione StartProfile subito prima di ogni chiamata alla funzione di destinazione. Inserisce la funzione StopProfile subito dopo ogni chiamata alla funzione di destinazione.<br /><br /> `funcname` - Nome della funzione di destinazione.|
|**Sospendi:** `{` **All'interno** \| **Esterno**`},funcname`|Esclude la raccolta dei dati per la funzione di destinazione e le funzioni figlio chiamate dalla funzione.<br /><br /> **Inside** - Inserisce la funzione SuspendProfile subito dopo l'ingresso nella funzione di destinazione. Inserisce la funzione ResumeProfile subito prima di ogni restituzione nella funzione di destinazione.<br /><br /> **Outside** - Inserisce la funzione SuspendProfile subito prima dell'ingresso nella funzione di destinazione. Inserisce la funzione ResumeProfile subito dopo l'uscita dalla funzione di destinazione.<br /><br /> `funcname` - nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StartProfile, la funzione SuspendProfile viene inserita prima. Se la funzione di destinazione contiene una funzione StartProfile, la funzione ResumeProfile viene inserita dopo.|
|**StartOnly:** `{` **Prima** \| **Dopo** \| **In alto** \| **In basso**`},funcname`|Avvia la raccolta dei dati durante un'esecuzione di profilatura. Inserisce la funzione API StartProfile nella posizione specificata.<br /><br /> **Prima:** immediatamente prima della voce della funzione di destinazione.<br /><br /> **Dopo** : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top** - subito dopo l'ingresso nella funzione di destinazione.<br /><br /> **Inferiore:** immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname` - nome della funzione di destinazione.|
|**StopOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Interrompe la raccolta dei dati durante un'esecuzione di profilatura. Inserisce la funzione StopProfile nella posizione specificata.<br /><br /> **Prima:** immediatamente prima della voce della funzione di destinazione.<br /><br /> **Dopo** : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top** - subito dopo l'ingresso nella funzione di destinazione.<br /><br /> **Inferiore:** immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname` - nome della funzione di destinazione.|
|**SuspendOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Interrompe la raccolta dei dati durante un'esecuzione di profilatura. Inserisce l'API SuspendProfile nella posizione specificata.<br /><br /> **Prima:** immediatamente prima della voce della funzione di destinazione.<br /><br /> **Dopo** : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top** - subito dopo l'ingresso nella funzione di destinazione.<br /><br /> **Inferiore:** immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname` - nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StartProfile, la funzione SuspendProfile viene inserita prima.|
|**ResumeOnly:**{**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Avvia o riprende la raccolta dei dati durante un'esecuzione di profilatura.<br /><br /> In genere, viene usato per avviare la profilatura dopo che un'opzione **SuspendOnly** ha terminato la profilatura. Inserisce un'API ResumeProfile nella posizione specificata.<br /><br /> **Prima:** immediatamente prima della voce della funzione di destinazione.<br /><br /> **Dopo** : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top** - subito dopo l'ingresso nella funzione di destinazione.<br /><br /> **Inferiore:** immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname` - nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StartProfile, la funzione ResumeProfile viene inserita dopo.|

## <a name="see-also"></a>Vedi anche
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Avvisi di VSInstr](../profiling/vsinstr-warnings.md)
- [Visualizzazioni dei report di prestazioni](../profiling/performance-report-views.md)
