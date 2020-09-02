---
title: Abilitazione delle funzionalità di debug in Visual C++ (-D_DEBUG) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686697"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Attivazione delle funzionalità di debug in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] le funzionalità di debug, ad esempio le asserzioni, vengono attivate quando si compila il programma definendo il simbolo **_DEBUG**. Il simbolo **_DEBUG** può essere definito in uno dei due modi seguenti:  
  
- Specificare **#define _DEBUG** nel codice sorgente.  
  
- Specificare l'opzione del compilatore **/D_DEBUG**. Quando si crea un progetto mediante le procedure guidate di Visual Studio, il simbolo **/D_DEBUG** viene definito automaticamente nella configurazione di debug.  
  
  Quando viene definito **_DEBUG**, il compilatore compila le sezioni del codice precedute e seguite da **#ifdef _DEBUG** e `#endif`.  
  
  La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. I file di intestazione MFC determinano la versione corretta della libreria MFC con cui effettuare il collegamento in base ai simboli definiti, ad esempio **_DEBUG** e **_UNICODE**. Per informazioni dettagliate, vedere [Versioni delle librerie MFC](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
