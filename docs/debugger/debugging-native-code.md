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
ms.openlocfilehash: 5a7cf0b150c45037941010bf7e611f4bc21252c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851901"
---
# <a name="debugging-native-code"></a>Debug del codice nativo
In questa sezione vengono discussi alcuni problemi di debug comuni, nonché varie tecniche per le applicazioni native. Le tecniche illustrate in questa sezione sono di alto livello. Per i meccanismi di uso del debugger di Visual Studio, vedere [innanzitutto osservare il debugger](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>In questa sezione
 [Procedura: Eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md) vengono forniti suggerimenti per il debug del codice ottimizzato, in particolare, motivo per cui è necessario eseguire il debug di una versione non ottimizzata del programma, impostazioni di ottimizzazione predefinite per le configurazioni di Debug e rilascio e vengono forniti suggerimenti per ricerca di bug che solo vengono visualizzati nel codice ottimizzato (attivando l'ottimizzazione in una configurazione di build di Debug).

 [DebugBreak e DebugBreak](../debugger/debugbreak-and-debugbreak.md) descrive Win32 `DebugBreak` funzione e viene fornito un collegamento all'argomento di riferimento in Platform SDK. Viene inoltre descritta la funzione intrinseca `__debugbreak`.

 [C /C++ asserzioni](../debugger/c-cpp-assertions.md) vengono illustrate le istruzioni di asserzione, il loro funzionamento, i vantaggi dell'uso li (rilevamento di errori per la logica, verifica i risultati di un'operazione e verifica delle condizioni di errore), l'interazione con `_DEBUG`e i tipi di asserzioni supportati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Procedura: Eseguire il debug di codice Assembly Inline](../debugger/how-to-debug-inline-assembly-code.md) fornisce brevi istruzioni sull'utilizzo della finestra Disassembly per visualizzare le istruzioni dell'assembly e la finestra registri per visualizzare il contenuto del registro e vengono forniti collegamenti ad argomenti relativi a tali finestre.

 [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md) possibile collegarsi alle tecniche di debug per programmi MFC, tra cui: afxDebugBreak, la macro TRACE, rilevamento memoria perdite in MFC, MFC asserzioni e riduzione delle dimensioni di Debug di MFC compila.

 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md) possibile collegarsi alle tecniche di debug per la libreria Run-Time di C, incluso l'uso della libreria di Debug CRT, macro per la creazione di report, le differenze tra malloc e malloc_dbg, scrittura di funzioni hook di debug e heap di debug CRT.

 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md) vengono fornite le risposte alle domande frequenti sul debug visivo C++ programmi

 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md) vengono fornite informazioni sul debug di applicazioni COM e ActiveX, inclusi strumenti che è possibile usare per COM e ActiveX di debug.

 [Procedura: Eseguire il debug del codice inserito](../debugger/how-to-debug-injected-code.md) fornisce materiale sussidiario sul debug del codice che usa gli attributi. Sono incluse istruzioni per l'attivazione del codice sorgente, la visualizzazione del codice inserito e del codice disassembly in corrispondenza del punto di esecuzione corrente.

 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) descrive come usare il **attività in parallelo** e **stack in parallelo** finestre degli strumenti di debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate
 [Visual C++ tipi di progetto](../debugger/debugging-preparation-visual-cpp-project-types.md) vengono forniti collegamenti ad argomenti che descrivono come eseguire il debug di tipi di progetto nativi creati dall'oggetto visivo C++ modelli di progetto.

 [Debug di progetti DLL](../debugger/debugging-dll-projects.md) fornisce informazioni su come eseguire il debug di DLL native che gestite.

 [Presentazione di debugger](../debugger/debugger-feature-tour.md) vengono forniti collegamenti a sezioni più ampie della documentazione sul debug. Vengono fornite informazioni sui seguenti argomenti: novità del debugger, impostazione e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice nativo, debug di SQL e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug in Visual Studio](../debugger/index.md)