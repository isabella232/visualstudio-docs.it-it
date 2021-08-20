---
title: Come è possibile accedere ai codici di errore di Win32? | Microsoft Docs
description: Per cercare un codice di errore Win32, immetterlo in Watch o QuickWatch. Ad esempio, "0x80000004,hr". Le definizioni del codice di errore sono incluse in INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 570b36b67fffbc65f5622601260b30dfb80a95bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112227"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Come è possibile accedere ai codici di errore di Win32?
Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.

 È possibile cercare un codice di errore digitando tale codice nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**. Ad esempio:

`0x80000004,hr`

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)