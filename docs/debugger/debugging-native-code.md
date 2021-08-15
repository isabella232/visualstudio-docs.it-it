---
title: Debug di codice nativo | Microsoft Docs
description: Informazioni sui problemi di debug comuni e sulle tecniche di alto livello per le applicazioni native in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 68b671aecd885cbd5b317c71c0a5962752a86001f8c9567e73b855b7060867d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264064"
---
# <a name="debugging-native-code"></a>Debug del codice nativo
In questa sezione vengono discussi alcuni problemi di debug comuni, nonché varie tecniche per le applicazioni native. Le tecniche illustrate in questa sezione sono di alto livello. Per informazioni sull'uso del debugger Visual Studio, vedere [Prima di tutto il debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: Eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md) Fornisce suggerimenti per il debug di codice ottimizzato, in particolare, perché è consigliabile eseguire il debug di una versione non ottimizzata del programma, impostazioni di ottimizzazione predefinite per le configurazioni di debug e versione e suggerimenti per trovare bug che vengono visualizzati solo nel codice ottimizzato (attivando l'ottimizzazione in una configurazione di compilazione debug).

 [DebugBreak e __debugbreak](../debugger/debugbreak-and-debugbreak.md) Descrive la funzione Win32 e fornisce un collegamento al relativo `DebugBreak` argomento di riferimento in Platform SDK. Viene inoltre descritta la funzione intrinseca `__debugbreak`.

 [Asserzioni C/C++](../debugger/c-cpp-assertions.md) Vengono illustrate le istruzioni di asserzione, il loro funzionamento, i vantaggi dell'uso di tali istruzioni (rilevamento degli errori logici, controllo dei risultati di un'operazione e test delle condizioni di errore), interazione con e tipi di asserzioni supportati `_DEBUG` in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 [Procedura: Eseguire il debug del codice assembly inline](../debugger/how-to-debug-inline-assembly-code.md) Vengono fornite brevi istruzioni sull'uso della finestra Disassembly per visualizzare le istruzioni dell'assembly e della finestra Registri per visualizzare il contenuto della registrazione e vengono forniti collegamenti ad argomenti relativi a tali finestre.

 [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md) Collegamenti alle tecniche di debug per i programmi MFC, tra cui: afxDebugBreak, macro TRACE, rilevamento di perdite di memoria in MFC, asserzioni MFC e riduzione delle dimensioni delle compilazioni di debug MFC.

 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md) Collegamenti alle tecniche di debug per la libreria C Run-Time, tra cui l'uso della libreria di debug CRT, le macro per la creazione di report, le differenze tra malloc e _malloc_dbg, la scrittura di funzioni hook di debug e l'heap di debug CRT.

 [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md) Fornisce risposte alle domande frequenti sul debug di programmi C++

 [Debug com e ActiveX](../debugger/com-and-activex-debugging.md) Vengono fornite informazioni sul debug di applicazioni COM e ActiveX, inclusi gli strumenti che è possibile usare per com e ActiveX debug.

 [Procedura: Eseguire il debug del codice inserito](../debugger/how-to-debug-injected-code.md) Fornisce indicazioni sul debug del codice che usa gli attributi. Sono incluse istruzioni per l'attivazione del codice sorgente, la visualizzazione del codice inserito e del codice disassembly in corrispondenza del punto di esecuzione corrente.

 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) Viene descritto come usare le finestre degli strumenti **Attività in** parallelo e **Stack** paralleli per eseguire il debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate
 [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md) Vengono forniti collegamenti ad argomenti che descrivono come eseguire il debug dei tipi di progetto nativi creati dai modelli di progetto C++.

 [Debug di progetti DLL](../debugger/debugging-dll-projects.md) Fornisce informazioni su come eseguire il debug di DLL native e gestite.

 [Per prima cosa, esaminare il debugger](../debugger/debugger-feature-tour.md) Vengono forniti collegamenti alle sezioni più grandi della documentazione di debug. Vengono fornite informazioni sui seguenti argomenti: novità del debugger, impostazione e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice nativo, debug di SQL e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug in Visual Studio](../debugger/index.yml)