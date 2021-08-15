---
title: Suggerimenti per il debug di thread in code | Microsoft Docs
description: Leggere un elenco di suggerimenti per il debug dei thread nel codice nativo se si esegue il debug di app multithreading in Visual Studio.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: e2dffe0a53383343c6990b2b19eeead2bb200893e1c97662d8afb4cb44c3812f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310888"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Suggerimenti per il debug dei thread in codice nativo
Di seguito sono riportati alcuni suggerimenti che è possibile utilizzare durante il debug dei thread in codice nativo:

- È possibile visualizzare il contenuto del blocco di informazioni del thread immettendo `@TIB` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.

- È possibile visualizzare l'ultimo codice di errore per il thread corrente immettendo `@Err` nella finestra **Espressioni di controllo** o nella finestra di dialogo **Controllo immediato**.

- Per il debug di applicazioni multithreading è possibile utilizzare le funzioni delle librerie di runtime del linguaggio C (CRT). Per altre informazioni, vedere [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)