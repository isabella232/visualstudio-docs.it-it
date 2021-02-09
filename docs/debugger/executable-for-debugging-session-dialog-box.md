---
title: Finestra di dialogo eseguibile per la sessione di debug | Microsoft Docs
description: Per eseguire il debug di una DLL, è necessario specificare un eseguibile per chiamare la DLL. Informazioni sulla finestra di dialogo visualizzata quando non è specificato alcun eseguibile.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870831"
---
# <a name="executable-for-debugging-session-dialog-box"></a>finestra di dialogo Eseguibile per la sessione di debug

Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile. Visual Studio non è in grado di avviare direttamente una DLL. Visual Studio avvia invece il file eseguibile specificato. È possibile eseguire il debug della DLL quando viene chiamata dall'eseguibile.

 **Nome file eseguibile** Immettere il nome del percorso di un eseguibile che chiama la DLL di cui si esegue il debug.

 **URL a cui è possibile accedere al progetto (solo ATL Server)** Se si sta eseguendo il debug di una DLL di ATL Server, immettere l'URL in cui è possibile trovare il progetto.

 Una volta immesse, queste impostazioni vengono archiviate nelle pagine delle proprietà del progetto, pertanto non sarà necessario immetterle di nuovo per le sessioni di debug successive. Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori. Per ulteriori informazioni sulla specifica di un eseguibile per la sessione di debug, vedere [debug di dll](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)