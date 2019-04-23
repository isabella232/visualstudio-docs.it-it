---
title: Suggerimenti per il debug di thread in codice nativo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c4bed2506fef0c4f066e58e158b062c2a6b39aa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074177"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:  
  
- È possibile visualizzare il contenuto del blocco di informazioni del thread immettendo `@TIB` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.  
  
- È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.  
  
- Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
