---
title: Come è possibile accedere ai codici di errore di Win32? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86735dae123d0fdedc59f4205af349b86cc6efd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519994"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Come è possibile accedere ai codici di errore di Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [in cui è possibile cercare i codici di errore Win32?](https://docs.microsoft.com/visualstudio/debugger/where-can-i-look-up-win32-error-codes-q).  
  
Il file WINERROR.H nella directory INCLUDE della directory di installazione di sistema predefinita contiene le definizioni dei codici di errore per le funzioni API Win32.  
  
 È possibile cercare un codice di errore digitando il codice nel **Watch** finestra o il **controllo immediato** nella finestra di dialogo. Ad esempio:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



