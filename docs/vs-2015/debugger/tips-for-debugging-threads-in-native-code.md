---
title: Suggerimenti per il debug dei thread in codice nativo | Microsoft Docs
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
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684876"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:  
  
- È possibile visualizzare il contenuto del blocco di informazioni del thread immettendo `@TIB` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.  
  
- È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.  
  
- Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
