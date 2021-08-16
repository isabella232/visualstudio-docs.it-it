---
title: VSPerfMon | Microsoft Docs
description: Informazioni su come usare lo strumento VSPerfMon per raccogliere dati sulle prestazioni per un'applicazione. Questo strumento viene in genere avviato da VSPerfCmd.exe.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d7874686dc9a3ccb1774520d7521cfd557cf9b2d48b2c324f18bac78f420de7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367850"
---
# <a name="vsperfmon"></a>VSPerfMon
È possibile usare lo strumento VSPerfMon per raccogliere dati sulle prestazioni per un'applicazione. In genere, questo strumento viene avviato da *VSPerfCmd.exe*. VSPerfMon visualizza informazioni aggiuntive sul collegamento o lo scollegamento di processi che non sono disponibili tramite lo strumento VSPerfCmd. Per visualizzare queste informazioni, avviare VSPerfMon in una finestra separata. Per richiamare VSPerfMon, usare la sintassi seguente:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Nella tabella seguente vengono descritte le opzioni dello strumento VSPerfMon:

|Opzioni|Descrizione|
|-------------|-----------------|
|**U**|L'output di console reindirizzato viene scritto come Unicode.  Deve essere la prima opzione specificata.|
|**OUTPUT:** `<` *nome file*`>`|Reindirizza l'output nel nome file specificato.|
|**Traccia**|Avvia il monitoraggio delle prestazioni per la profilatura instrumentata.|
|**SAMPLE**|Avvia il monitoraggio delle prestazioni per la profilatura tramite campionamento.|
|**Copertura**|Avvia il monitoraggio delle prestazioni per la raccolta dei dati di code coverage.|
|**Concorrenza**|Avvia il monitoraggio delle prestazioni per la profilatura dei conflitti di risorse.|
|**UTENTE:** `[` *dominio* `\]` *nome utente*|Consente l'accesso client al monitoraggio delle prestazioni dall'account specificato.|
|**CROSSSESSION**|Abilita la profilatura tra sessioni.|
|**COUNTER**`:cfg`|Quando viene usato il metodo di profilatura tramite strumentazione (TRACE), specifica un contatore CPU da raccogliere a ogni punto di strumentazione. È possibile raccogliere i dati di più contatori specificando più opzioni Counter.<br /><br /> Usare la seguente sintassi per specificare i dati del contatore (*cfg*):<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** è il nome di un contatore restituito dal comando VSPerfCmd /QueryCounters.<br />-   **Reload** è l'intervallo di campionamento degli eventi del contatore. Non usare *Reload* con il metodo di strumentazione.<br />Quando specificato, **FriendlyName** sostituisce **CounterName** nei nomi di colonna dei report degli strumenti di profilatura.|
|**WINCOUNTER**`:path`|Specifica un contatore delle prestazioni di Windows da includere con i dati contrassegnati. `path` è una stringa del contatore delle prestazioni di Windows nel formato del percorso del contatore PDH. Esempio:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK**`:n`|Specifica l'intervallo di tempo (in millisecondi) tra i contrassegni automatici quando si usa /WINCOUNTER. Arrotondato per eccesso al più vicino multiplo di 500 ms.<br /><br /> Usare 0 per disabilitare i contrassegni automatici. Se non si specifica alcun valore, l'impostazione predefinita è 500 ms.|

## <a name="see-also"></a>Vedi anche
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Visualizzazioni dei report di prestazioni](../profiling/performance-report-views.md)
