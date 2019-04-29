---
title: Determinare se i puntatori danneggiato un indirizzo di memoria | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5e61c1433ee05954a85537cd5e30bb9683642f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894938"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria?
## <a name="problem-description"></a>Descrizione del problema
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000. Come è possibile appurare cosa sta accadendo in tale posizione?

## <a name="solution"></a>Soluzione

#### <a name="check-for-heap-corruption"></a>Controllare l'integrità della memoria heap

- Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap. Provare a utilizzare l'utilità per i flag globali (gflags.exe) o pageheap.exe. Visualizzare [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Per individuare i punti in cui l'indirizzo di memoria è modificato

1. Impostare un punto di interruzione di dati all'indirizzo 0x00408000. Vedere [Impostare un punto di interruzione di modifica dei dati (solo C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Quando si raggiunge un punto di interruzione, usare la finestra **Memoria** per visualizzare il contenuto della memoria a partire dall'indirizzo 0x00408000. Per altre informazioni, vedere [memoria Windows](../debugger/memory-windows.md).

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)