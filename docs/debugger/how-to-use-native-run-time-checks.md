---
title: Usare i controlli Run-Time native | Microsoft Docs
description: Usare i controlli di runtime nativi nel Visual Studio per rilevare errori di runtime comuni, ad esempio il danneggiamento del puntatore dello stack, i sovraccarichi di matrici locali e il danneggiamento dello stack.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 5189712cbaff2abd2fb814ee23dc6a87ae086fc7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051872"
---
# <a name="how-to-use-native-run-time-checks"></a>Procedura: utilizzare controlli runtime nativi
In un Visual Studio C++ è possibile usare [](/cpp/preprocessor/runtime-checks) il runtime_checks nativo per rilevare errori di runtime comuni, ad esempio:

- Errori del puntatore dello stack.

- Sovraccarichi di matrici locali.

- Errori dello stack.

- Dipendenze da variabili locali non inizializzate.

- Perdita di dati a causa dell'assegnazione a una variabile di lunghezza inferiore.

  Se si usa l'opzione **/RTC** con una build ottimizzata (**/O**), verrà restituito un errore del compilatore. Se si usa un pragma `runtime_checks` in una build ottimizzata, il pragma non avrà effetto.

  Durante il debug di un programma in cui sono attivi i controlli runtime, l'azione predefinita quando si verifica un errore di runtime è l'arresto del programma e il passaggio al debugger. Tale comportamento predefinito può essere modificato per qualsiasi controllo runtime. Per altre informazioni, vedere [Gestione delle eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md).

  Nelle procedure riportate di seguito viene descritto come attivare i controlli runtime nativi in una build di debug e come modificare il comportamento di tali controlli.

  Negli altri argomenti di questa sezione vengono fornite informazioni relative a:

- [Personalizzazione dei controlli runtime nativi](../debugger/native-run-time-checks-customization.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Per attivare i controlli runtime nativi in una build di debug

- Usare l'opzione **/RTC** e collegarsi alla versione di debug di una libreria di runtime del linguaggio C, ad esempio /MDd.

### <a name="to-modify-native-run-time-check-behavior"></a>Per modificare il comportamento dei controlli runtime nativi

- Usare il pragma `runtime_checks` .

## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Controllo degli errori di run-time](/cpp/c-runtime-library/run-time-error-checking)