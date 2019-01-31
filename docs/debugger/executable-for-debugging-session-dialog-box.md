---
title: Eseguibile per la finestra di dialogo di sessione di debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d6bc004ac9d450e0f5ea358d16bb25ab6cabecf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018751"
---
# <a name="executable-for-debugging-session-dialog-box"></a>finestra di dialogo Eseguibile per la sessione di debug

Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile. Visual Studio non è possibile avviare direttamente una DLL. Al contrario, Visual Studio avvia l'eseguibile specificato. È possibile eseguire il debug di DLL quando viene chiamata dall'eseguibile.  
  
 **Nome del file eseguibile**  
 Immettere il nome e il percorso di un file eseguibile che chiama la DLL sottoposta a debug.  
  
 **URL per accedere al progetto (solo ATL Server)**  
 Se si esegue il debug di una DLL di ATL Server, immettere l'URL del progetto.  
  
 Una volta immesse, queste impostazioni vengono archiviate in pagine delle proprietà, il progetto in modo non sarà necessario immetterle nuovamente per le sessioni di debug successive. Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori. Per ulteriori informazioni sulla specifica di un eseguibile per la sessione di debug, vedere [Debug delle DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Vedere anche

 [Debug in Visual Studio](../debugger/index.md)  
 [Presentazione del debugger](../debugger/debugger-feature-tour.md)