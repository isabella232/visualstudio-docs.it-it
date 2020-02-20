---
title: Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476772"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrizione del problema  
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000. Come è possibile appurare cosa sta accadendo in tale posizione?  
  
## <a name="solution"></a>Soluzione  
  
#### <a name="check-for-heap-corruption"></a>Controllare l'integrità della memoria heap  
  
- Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap. Provare a utilizzare l'utilità per i flag globali (gflags.exe) o pageheap.exe. Vedere [gflags e Pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap) e [come usare l'utilità Pageheap per rilevare errori di memoria in un progetto visuale C++ Microsoft](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft).
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Per individuare i punti in cui l'indirizzo di memoria è modificato  
  
1. Impostare un punto di interruzione di dati all'indirizzo 0x00408000. Vedere [Impostare un punto di interruzione di modifica dei dati (solo C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2. Quando si raggiunge un punto di interruzione, usare la finestra **Memoria** per visualizzare il contenuto della memoria a partire dall'indirizzo 0x00408000. Per altre informazioni, vedere [finestre di memoria](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
