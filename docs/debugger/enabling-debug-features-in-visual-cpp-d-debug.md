---
title: Abilitazione delle funzionalità C++ di debug nei progetti (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7f772b74a42b9704f1fd77c731022ddb44774c68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430677"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Attivazione delle funzionalità di C++ debug nei progetti (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le funzionalità di debug, ad esempio le asserzioni, vengono attivate quando si compila il programma definendo il simbolo **_DEBUG**. Il simbolo **_DEBUG** può essere definito in uno dei due modi seguenti:

- Specificare **#define _DEBUG** nel codice sorgente.

- Specificare l'opzione del compilatore **/D_DEBUG**. Quando si crea un progetto mediante le procedure guidate di Visual Studio, il simbolo **/D_DEBUG** viene definito automaticamente nella configurazione di debug.

  Quando viene definito **_DEBUG**, il compilatore compila le sezioni del codice precedute e seguite da **#ifdef _DEBUG** e `#endif`.

  La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. I file di intestazione MFC determinano la versione corretta della libreria MFC con cui effettuare il collegamento in base ai simboli definiti, ad esempio **_DEBUG** e **_UNICODE**. Per informazioni dettagliate, vedere [Versioni delle librerie MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Vedere anche
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)