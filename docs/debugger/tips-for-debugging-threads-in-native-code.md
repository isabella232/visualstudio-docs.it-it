---
title: Suggerimenti per il debug dei thread in codice nativo | Microsoft Docs
description: Leggere un elenco di suggerimenti per il debug dei thread in codice nativo se si esegue il debug di app multithread in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150054"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:

- È possibile visualizzare il contenuto del blocco di informazioni del thread immettendo `@TIB` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.

- È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.

- Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)