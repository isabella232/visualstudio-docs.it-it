---
title: Controlli Run-Time controlli di personalizzazione | Microsoft Docs
description: Informazioni su come personalizzare il controllo in fase di esecuzione, tra cui specificare una destinazione del messaggio, scrivere una funzione di segnalazione degli errori ed eseguire query per ottenere informazioni sugli errori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 534e2d8616fb70ca0089cc2efa90c19ac97c62b7860723f64784549620111a85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239610"
---
# <a name="native-run-time-checks-customization"></a>Personalizzazione dei controlli runtime nativi
Quando si esegue la compilazione con **/RTC** (controlli di runtime) o si usa il pragma , la libreria di `runtime_checks` runtime C fornisce controlli runtime nativi. In alcuni casi può essere necessario personalizzare il controllo runtime:

- Per indirizzare i messaggi del controllo runtime a un file o una destinazione diversa da quella predefinita.

- Per specificare una destinazione di output dei messaggi del controllo runtime in un debugger di altri produttori.

- Per segnalare i messaggi del controllo runtime provenienti da un programma compilato con una versione di rilascio della libreria di runtime del linguaggio C. Nelle versioni di rilascio della libreria per segnalare gli errori di runtime non viene utilizzato `_CrtDbgReportW` e viene invece visualizzata una finestra di dialogo di **asserzione** per ciascun errore di runtime.

  Per personalizzare il controllo degli errori di runtime, è possibile utilizzare uno degli accorgimenti seguenti:

- Scrivere una funzione per la segnalazione degli errori di runtime. Per altre informazioni, vedere [Procedura: Scrivere una funzione Run-Time segnalazione errori](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Personalizzare la destinazione dei messaggi di errore.

- Eseguire una query per ottenere informazioni sugli errori rilevati dai controlli runtime.

## <a name="customize-the-error-message-destination"></a>Personalizzare la destinazione dei messaggi di errore
 Se si utilizza `_CrtDbgReportW` per la segnalazione degli errori, è possibile utilizzare `_CrtSetReportMode` per specificare la destinazione dei messaggi di errore.

 Se si utilizza una funzione di segnalazione degli errori personalizzata, utilizzare `_RTC_SetErrorType` per associare un tipo di report a ciascun errore.

## <a name="query-for-information-about-run-time-checks"></a>Eseguire una query per ottenere informazioni sui controlli runtime
 `_RTC_NumErrors` restituisce il numero di tipi di errore rilevati dai controlli degli errori di runtime. Per ottenere una breve descrizione di ciascun errore, è possibile creare un ciclo da 0 al valore restituito da `_RTC_NumErrors` passando il valore di iterazione a `_RTC_GetErrDesc` in ciascun ciclo. Per altre informazioni, vedere [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) e [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare controlli Run-Time nativi](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)