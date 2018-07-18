---
title: Come è possibile accedere ai codici di errore di Win32? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecddd2a8ca87d4c86b3cdf776fcf2e475efb8836
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056924"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Come è possibile accedere ai codici di errore di Win32?
Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.  
  
 È possibile cercare un codice di errore digitando il codice nel **Watch** finestra o il **controllo immediato** nella finestra di dialogo. Ad esempio:  
  
`0x80000004,hr` 

  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)