---
title: Suggerimenti per il debug di thread in codice nativo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e8690583794c23ce95fb52ef6cab3ab6667afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184925"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:  
  
-   È possibile visualizzare il contenuto del blocco di informazioni del Thread, digitare `@TIB` nella **Watch** finestra oppure **controllo immediato** nella finestra di dialogo.  
  
-   È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nella **Watch** finestra oppure **controllo immediato** nella finestra di dialogo.  
  
-   Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



