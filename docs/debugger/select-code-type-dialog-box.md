---
title: Finestra di dialogo Seleziona tipo di codice | Microsoft Docs
description: Informazioni sulla finestra di dialogo Seleziona tipo di codice in Visual Studio. Per visualizzare questa finestra di dialogo, aprire la finestra di dialogo Connetti a processo e fare clic su Seleziona.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5ecffb2bb8a6cf616b75386cac5823763534bb30
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636611"
---
# <a name="select-code-type-dialog-box"></a>Finestra di dialogo Seleziona tipo di codice

Per visualizzare questa finestra di dialogo, aprire la finestra di dialogo **Connetti a processo** e fare clic su **Seleziona**.

**Determinare automaticamente il tipo di codice di cui eseguire il debug** Il debugger appropriato verrà selezionato in base al tipo di codice in esecuzione.

**Eseguire il debug di questi tipi di codice:** Nell'elenco fornito scegliere i tipi di codice di cui si vuole eseguire il debug. Questa operazione può essere utile per [la risoluzione dei problemi relativi a un errore di collegamento di](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Questa opzione limita il rilevamento solo ai tipi di codice di cui si vuole eseguire il debug.

::: moniker range=">=vs-2019"
- Blazor WebAssembly - Lato client Blazor WebAssembly
- GPU - Software Emulator - Codice C++ in esecuzione in un emulatore software GPU
- JavaScript (Chrome) - JavaScript in esecuzione in Chrome
- JavaScript (Microsoft Edge - Chromium) - JavaScript in esecuzione in Chromium basato su Microsoft Edge per Windows 10
- Debugger CDP (V3) JavaScript - Chrome DevTools Protocol versione 3, usato per il debug in un client CDP
- Managed (CoreCLR) - .NET Core
- Gestito (compilazione nativa) - Codice C++/CLR
- Gestito (v3.5, v3.0, v2.0): codice .NET Framework per .NET Framework 2.0 e versioni successive (fino a 3.5)
- Gestito (v.4.6, v4.5, v4.0): codice .NET Framework per .NET Framework 4.0 e versioni successive
- Nativo - C/C++
- Node.js debug: codice ospitato dal runtime di Node.js
- Python - Python 
- Script: specifica il debugger di script generale per JavaScript. Usare opzioni più restrittive se si applicano allo scenario, ad esempio JavaScript (Chrome).
- T-SQL - Transact-SQL
- Unity - Unity
- Modalità di compatibilità gestita: specifica il debugger legacy per il codice gestito, da usare in genere nel debug in modalità mista con codice C++/CLR (abilita Modifica e continuazione per la modalità mista) o per supportare le estensioni destinate al debugger legacy. Nella maggior parte degli scenari di debug in modalità mista selezionare **Nativo** e i tipi **di** codice gestito appropriati invece della modalità di compatibilità gestita.
::: moniker-end

Per la maggior parte degli scenari, il collegamento di più debugger nella stessa sessione di debug non è supportato. È possibile eseguire questa operazione usando una seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
