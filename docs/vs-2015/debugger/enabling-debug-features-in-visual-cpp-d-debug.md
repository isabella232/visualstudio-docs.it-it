---
title: Abilitazione della funzionalità di Debug in Visual C++ (-D_DEBUG) | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67de755105f30ee4a88daeef26bc29bc9841ae39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526558"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Attivazione delle funzionalità di debug in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [l'abilitazione delle funzionalità di Debug in Visual C++ (-D_DEBUG)](https://docs.microsoft.com/visualstudio/debugger/enabling-debug-features-in-visual-cpp-d-debug).  
  
Nelle [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], le funzionalità di debug, ad esempio le asserzioni vengono abilitate quando si compila il programma con il simbolo **debug** definito. È possibile definire **debug** in uno dei due modi:  
  
-   Specificare **#define debug** nel codice sorgente, o  
  
-   Specificare il **/D_DEBUG** opzione del compilatore. (Se si crea il progetto in Visual Studio usando procedure guidate **/D_DEBUG** viene definito automaticamente nella configurazione di Debug.)  
  
 Quando **debug** è definito, il compilatore compila le sezioni di codice racchiusi tra **debug #ifdef** e `#endif`.  
  
 La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. File di intestazione MFC determinano la versione corretta della libreria MFC per il collegamento a in base ai simboli definiti, ad esempio **debug** e **Unicode**. Per informazioni dettagliate, vedere [versioni di librerie MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



