---
title: Continuazione dell'esecuzione dopo un'eccezione | Microsoft Docs
description: Scopri cosa accade quando il debugger interrompe l'esecuzione a causa di un'eccezione non gestita. Potrebbe essere possibile continuare l'esecuzione nello stesso thread.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9af71aba1b26c3d8160af229d8c050038800106a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865813"
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
Quando il debugger interrompe l'esecuzione a causa di un'eccezione, per impostazione predefinita viene visualizzato l' **Helper eccezioni**. Se l' **Helper eccezioni** è stato disabilitato nella finestra di dialogo **Opzioni** , sarà possibile visualizzare le informazioni sulle **eccezioni** (C# o Visual Basic) o la finestra di dialogo **eccezione** (C++).

 Quando viene visualizzato l' **Helper eccezioni** , è possibile tentare di risolvere il problema che ha causato l'eccezione.

## <a name="managed-and-native-code"></a>Codice gestito e nativo
 Nel codice gestito e nativo è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. Il **supporto eccezioni** rimuove lo stack di chiamate nel punto in cui è stata generata l'eccezione.

## <a name="mixed-code"></a>Codice misto
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.

## <a name="see-also"></a>Vedi anche

- [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)