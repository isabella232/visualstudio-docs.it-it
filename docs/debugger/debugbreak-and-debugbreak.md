---
title: DebugBreak e __debugbreak | Microsoft Docs
description: Informazioni su come usare la funzione DebugBreak e la funzione __debugbreak intrinseca per causare l'interruzione del programma, proprio come se fosse stato impostato un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 707c660b658a4f1c34ab0faf345ff64c5063dc8f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626508"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak e __debugbreak
È possibile chiamare la [funzione Win32 DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) o __debugbreak [intrinseca](/cpp/intrinsics/debugbreak) in qualsiasi punto del codice. `DebugBreak` e `__debugbreak` hanno lo stesso effetto dell'impostazione di un punto di interruzione nella stessa posizione.

 Poiché `DebugBreak` è una chiamata a una funzione di sistema, è necessario che siano installati i simboli di debug del sistema per garantire che vengano visualizzate le informazioni corrette sullo stack di chiamate dopo l'interruzione. In alternativa, le informazioni sullo stack di chiamate visualizzate dal debugger possono essere spostate di un frame. Se si usa `__debugbreak`, i simboli non sono obbligatori.

## <a name="see-also"></a>Vedi anche
- [Intrinseci del compilatore](/cpp/intrinsics/compiler-intrinsics)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
