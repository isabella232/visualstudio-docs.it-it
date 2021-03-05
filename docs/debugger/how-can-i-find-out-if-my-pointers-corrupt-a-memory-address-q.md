---
title: Individuare se i puntatori danneggiano un indirizzo di memoria | Microsoft Docs
description: Per determinare se il puntatore danneggia la memoria, è possibile cercare il danneggiamento dell'heap ed è possibile impostare un punto di interruzione dei dati per scoprire come viene modificato un valore.
ms.custom: SEO-VS-2020, seodec18
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
ms.workload:
- multiple
ms.openlocfilehash: d95e38c6393d6576f2867aad5d1224940f33cebc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155200"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria?
## <a name="problem-description"></a>Descrizione del problema
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000. Come è possibile appurare cosa sta accadendo in tale posizione?

## <a name="solution"></a>Soluzione

#### <a name="check-for-heap-corruption"></a>Controllare l'integrità della memoria heap

- Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap. Provare a utilizzare l'utilità per i flag globali (gflags.exe) o pageheap.exe. Vedere [/Windows-Hardware/Drivers/debugger/gflags-and-Pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Per individuare i punti in cui l'indirizzo di memoria è modificato

1. Impostare un punto di interruzione di dati all'indirizzo 0x00408000. Vedere [Impostare un punto di interruzione di modifica dei dati (solo C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Quando si raggiunge un punto di interruzione, usare la finestra **Memoria** per visualizzare il contenuto della memoria a partire dall'indirizzo 0x00408000. Per altre informazioni, vedere [finestre di memoria](../debugger/memory-windows.md).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
