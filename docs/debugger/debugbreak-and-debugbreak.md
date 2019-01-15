---
title: DebugBreak e DebugBreak | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db3af2a2bef69a9329a20523ad5bed4444631410
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933849"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak e __debugbreak
È possibile chiamare la funzione Win32 DebugBreak o la funzione intrinseca [__debugbreak](/cpp/intrinsics/debugbreak) in qualunque punto del codice. `DebugBreak` e `__debugbreak` hanno lo spesso effetto dell'impostazione di un punto di interruzione nella stessa posizione.  
  
 Poiché `DebugBreak` è una chiamata a una funzione di sistema, è necessario che siano installati i simboli di debug del sistema per garantire che vengano visualizzate le informazioni corrette sullo stack di chiamate dopo l'interruzione. In alternativa, le informazioni sullo stack di chiamate visualizzate dal debugger possono essere spostate di un frame. Se si usa `__debugbreak`, i simboli non sono obbligatori.  
  
## <a name="see-also"></a>Vedere anche  
 [Intrinseci del compilatore](/cpp/intrinsics/compiler-intrinsics)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)