---
title: Scoprire se i puntatori danneggiano un indirizzo di memoria | Microsoft Docs
description: Per determinare se il puntatore danneggia la memoria, è possibile cercare il danneggiamento dell'heap ed è possibile impostare un punto di interruzione dei dati per scoprire come viene modificato un valore.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5fd0e82aa4f66838025c5aa235a9ca9a6bfe6ec0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030789"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria?
## <a name="problem-description"></a>Descrizione del problema
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000. Come è possibile appurare cosa sta accadendo in tale posizione?

## <a name="solution"></a>Soluzione

#### <a name="check-for-heap-corruption"></a>Controllare l'integrità della memoria heap

- Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap. Provare a utilizzare l'utilità per i flag globali (gflags.exe) o pageheap.exe. Vedere [/windows-hardware/drivers/debugger/gflags-and-pageheap.](/windows-hardware/drivers/debugger/gflags-and-pageheap)

#### <a name="to-find-where-the-memory-address-is-modified"></a>Per individuare i punti in cui l'indirizzo di memoria è modificato

1. Impostare un punto di interruzione di dati all'indirizzo 0x00408000. Vedere [Impostare un punto di interruzione di modifica dei dati (solo C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Quando si raggiunge un punto di interruzione, usare la finestra **Memoria** per visualizzare il contenuto della memoria a partire dall'indirizzo 0x00408000. Per altre informazioni, vedere [Memory Windows](../debugger/memory-windows.md).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
