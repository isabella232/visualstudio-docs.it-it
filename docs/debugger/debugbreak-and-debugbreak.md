---
title: DebugBreak e __debugbreak | Microsoft Docs
description: Informazioni su come usare la funzione DebugBreak e il __debugbreak intrinseco per fare in modo che il programma si interrompa, proprio come se fosse stato impostato un punto di interruzione.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559771"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak e __debugbreak
È possibile chiamare la funzione Win32 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) o il [__debugbreak](/cpp/intrinsics/debugbreak) intrinseco in qualsiasi punto del codice. `DebugBreak` e `__debugbreak` hanno lo stesso effetto dell'impostazione di un punto di interruzione nella stessa posizione.

 Poiché `DebugBreak` è una chiamata a una funzione di sistema, è necessario che siano installati i simboli di debug del sistema per garantire che vengano visualizzate le informazioni corrette sullo stack di chiamate dopo l'interruzione. In alternativa, le informazioni sullo stack di chiamate visualizzate dal debugger possono essere spostate di un frame. Se si usa `__debugbreak`, i simboli non sono obbligatori.

## <a name="see-also"></a>Vedere anche
- [Intrinseci del compilatore](/cpp/intrinsics/compiler-intrinsics)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
