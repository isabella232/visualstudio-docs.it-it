---
title: Abilitazione della funzionalità di Debug in Visual C++ (-D_DEBUG) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949617"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Attivazione delle funzionalità di debug in Visual C++ (/D_DEBUG)
Nelle [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], le funzionalità di debug, ad esempio le asserzioni vengono abilitate quando si compila il programma con il simbolo **debug** definito. È possibile definire **debug** in uno dei due modi:  
  
- Specificare **#define debug** nel codice sorgente, o  
  
- Specificare il **/D_DEBUG** opzione del compilatore. (Se si crea il progetto in Visual Studio usando procedure guidate **/D_DEBUG** viene definito automaticamente nella configurazione di Debug.)  
  
  Quando **debug** è definito, il compilatore compila le sezioni di codice racchiusi tra **debug #ifdef** e `#endif`.  
  
  La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. File di intestazione MFC determinano la versione corretta della libreria MFC per il collegamento a in base ai simboli definiti, ad esempio **debug** e **Unicode**. Per informazioni dettagliate, vedere [versioni di librerie MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)