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
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849956"
---
# <a name="executable-for-debugging-session-dialog-box"></a>finestra di dialogo Eseguibile per la sessione di debug

Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile. Visual Studio non è possibile avviare direttamente una DLL. Al contrario, Visual Studio avvia l'eseguibile specificato. È possibile eseguire il debug di DLL quando viene chiamata dall'eseguibile.

 **Nome del file eseguibile** immettere il nome del percorso di un file eseguibile che chiama la DLL si esegue il debug.

 **Accedere all'URL in cui può essere il progetto (solo ATL Server)** se si esegue il debug di una DLL di ATL Server, immettere l'URL dove si trova il progetto.

 Una volta immesse, queste impostazioni vengono archiviate in pagine delle proprietà, il progetto in modo non sarà necessario immetterle nuovamente per le sessioni di debug successive. Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori. Per ulteriori informazioni sulla specifica di un eseguibile per la sessione di debug, vedere [Debug delle DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)