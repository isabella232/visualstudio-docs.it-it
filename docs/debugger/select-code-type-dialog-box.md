---
title: Finestra di dialogo Seleziona tipo di codice | Microsoft Docs
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6fefcea57b97ad3b31e4d10330756565c005184
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248765"
---
# <a name="select-code-type-dialog-box"></a>Finestra di dialogo Seleziona tipo di codice

Per visualizzare questa finestra di dialogo, aprire la finestra di dialogo **Connetti a processo** e fare clic su **Seleziona**.

**Determinare automaticamente il tipo di codice di cui eseguire il debug** Il debugger appropriato verrà selezionato in base al tipo di codice in esecuzione.

**Eseguire il debug di questi tipi di codice:** Dall'elenco fornito scegliere i tipi di codice di cui si vuole eseguire il debug. Questo può essere utile durante [la risoluzione di un errore di connessione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Questa opzione limita il rilevamento solo ai tipi di codice di cui si vuole eseguire il debug.

::: moniker range=">=vs-2019"
- Blazor WebAssembly -Lato client Blazor WebAssembly
- GPU-emulatore software-codice C++ in esecuzione in un emulatore software GPU
- JavaScript (Chrome)-JavaScript in esecuzione in Chrome
- JavaScript (Microsoft Edge-Chromium)-JavaScript in esecuzione in Microsoft Edge basato su cromo per Windows 10
- Debugger CDP (v3) JavaScript-Chrome DevTools protocollo versione 3, usato per il debug in un client CDP
- Gestito (CoreCLR)-.NET Core
- Gestita (compilazione nativa)-codice/CLR C++
- Gestito (v 3.5, v 3.0, v 2.0)-codice .NET Framework per .NET Framework 2,0 e versioni successive (fino a 3,5)
- Gestito (v. 4.6, v 4.5, v 4.0)-codice .NET Framework per .NET Framework 4,0 e versioni successive
- Nativo-C/C++
- Node.js debug-codice ospitato dal runtime di Node.js
- Python-Python 
- Script: specifica il debugger di script generale per JavaScript. Usare opzioni più restrittive se si applicano allo scenario, ad esempio JavaScript (Chrome).
- T-SQL-Transact-SQL
- Unity-Unity
- Modalità di compatibilità gestita: specifica il debugger legacy per il codice gestito, per l'uso in genere nel debug in modalità mista con codice/CLR C++ (Abilita modifica e continuazione per la modalità mista) o per supportare le estensioni destinate al debugger legacy. Nella maggior parte degli scenari di debug in modalità mista selezionare **nativo** e i tipi di codice **gestito** appropriati anziché la modalità di compatibilità gestita.
::: moniker-end

Per la maggior parte degli scenari, non è supportato il fissaggio di più debugger nella stessa sessione di debug. Questa operazione può essere eseguita usando una seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
