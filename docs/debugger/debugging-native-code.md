---
title: Debug del codice nativo | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738160"
---
# <a name="debugging-native-code"></a>Debug del codice nativo
In questa sezione vengono discussi alcuni problemi di debug comuni, nonché varie tecniche per le applicazioni native. Le tecniche illustrate in questa sezione sono di alto livello. Per informazioni sui meccanismi di utilizzo del debugger di Visual Studio, vedere la pagina relativa alla [prima occhiata al debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md) Fornisce suggerimenti per il debug di codice ottimizzato, in particolare per i motivi per cui è consigliabile eseguire il debug di una versione non ottimizzata del programma, le impostazioni di ottimizzazione predefinite per le configurazioni di debug e di rilascio e suggerimenti per la ricerca di bug che vengono visualizzati solo nel codice ottimizzato (attivazione dell'ottimizzazione in una configurazione della build di debug

 [DebugBreak e __debugbreak](../debugger/debugbreak-and-debugbreak.md) Viene descritta la `DebugBreak` funzione Win32 e viene fornito un collegamento al relativo argomento di riferimento in Platform SDK. Viene inoltre descritta la funzione intrinseca `__debugbreak`.

 [Asserzioni C/C++](../debugger/c-cpp-assertions.md) Vengono illustrate le istruzioni di asserzione, il relativo funzionamento, i vantaggi derivanti dall'utilizzo di tali istruzioni (rilevamento di errori logici, controllo dei risultati di un'operazione e test delle condizioni di errore), interazione con `_DEBUG` e tipi di asserzioni supportati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 [Procedura: eseguire il debug di codice assembly inline](../debugger/how-to-debug-inline-assembly-code.md) Fornisce brevi istruzioni sull'utilizzo della finestra Disassembly per visualizzare le istruzioni di assembly e la finestra registri per visualizzare il contenuto del registro e fornisce collegamenti ad argomenti relativi a tali finestre.

 [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md) Collegamenti alle tecniche di debug per i programmi MFC, tra cui: afxDebugBreak, la macro TRACE, rilevamento di perdite di memoria in MFC, asserzioni MFC e riduzione delle dimensioni delle build di debug MFC.

 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md) Collegamenti alle tecniche di debug per la libreria di runtime del linguaggio C, tra cui l'uso della libreria di debug CRT, le macro per la creazione di report, le differenze tra malloc e _malloc_dbg, la scrittura di funzioni hook di debug e l'heap di debug CRT.

 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md) Fornisce risposte alle domande frequenti sul debug di programmi C++

 [Debug di com e ActiveX](../debugger/com-and-activex-debugging.md) Vengono fornite informazioni sul debug di applicazioni COM e ActiveX, inclusi gli strumenti che è possibile utilizzare per il debug COM e ActiveX.

 [Procedura: eseguire il debug di codice inserito](../debugger/how-to-debug-injected-code.md) Vengono fornite informazioni aggiuntive sul debug del codice che utilizza gli attributi. Sono incluse istruzioni per l'attivazione del codice sorgente, la visualizzazione del codice inserito e del codice disassembly in corrispondenza del punto di esecuzione corrente.

 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) Viene descritto come utilizzare le finestre degli strumenti **attività in parallelo** e **stack** in parallelo per eseguire il debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate
 [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md) Vengono forniti collegamenti ad argomenti in cui viene descritto come eseguire il debug dei tipi di progetto nativi creati dai modelli di progetto C++.

 [Debug di progetti DLL](../debugger/debugging-dll-projects.md) Vengono fornite informazioni su come eseguire il debug di DLL native e gestite.

 [Prima di tutto esaminare il debugger](../debugger/debugger-feature-tour.md) Vengono forniti collegamenti alle sezioni più grandi della documentazione di debug. Vengono fornite informazioni sui seguenti argomenti: novità del debugger, impostazione e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice nativo, debug di SQL e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug in Visual Studio](../debugger/index.yml)