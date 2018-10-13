---
title: Eseguibile per la finestra di dialogo di sessione di debug | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1279ba5b3ed79c4115143a72e4543bbd6c123d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189826"
---
# <a name="executable-for-debugging-session-dialog-box"></a>finestra di dialogo Eseguibile per la sessione di debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile. Visual Studio non è in grado di avviare direttamente una DLL, ma avvierà l'eseguibile specificato. È possibile eseguire il debug della DLL quando viene chiamata dall'eseguibile.  
  
 **Nome del file eseguibile**  
 Immettere il nome e il percorso di un file eseguibile che chiama la DLL sottoposta a debug.  
  
 **Accedere all'URL in cui può essere il progetto (solo ATL Server)**  
 Se si esegue il debug di una DLL di ATL Server, immettere l'URL del progetto.  
  
 Una volta immesse, queste impostazioni sono archiviate nelle Pagine delle proprietà del progetto, pertanto non è necessario immetterle nuovamente per le successive sessioni di debug. Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori. Per altre informazioni su come specificare un file eseguibile per la sessione di debug, vedere [debug delle DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)



