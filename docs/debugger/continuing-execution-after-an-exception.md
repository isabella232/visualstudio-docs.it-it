---
title: Continuazione dell'esecuzione dopo un'eccezione | Microsoft Docs
description: Informazioni su cosa accade quando il debugger interrompe l'esecuzione a causa di un'eccezione non gestita. È possibile continuare l'esecuzione nello stesso thread.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: baed5da414077ee5d81482f092e697ddb608e420
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121726"
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
Quando il debugger interrompe l'esecuzione a causa di un'eccezione, per impostazione predefinita verrà visualizzato **l'helper** eccezioni . Se l'helper  eccezioni  è stato disabilitato nella finestra di dialogo Opzioni , verrà  visualizzato l'Assistente eccezioni **(C#** o Visual Basic) o la finestra di dialogo Eccezione (C++).

 Quando viene **visualizzato l'helper** eccezioni, è possibile provare a risolvere il problema che ha causato l'eccezione.

## <a name="managed-and-native-code"></a>Codice gestito e nativo
 Nel codice gestito e nativo è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. **L'helper** eccezioni sblocca lo stack di chiamate fino al punto in cui è stata generata l'eccezione.

## <a name="mixed-code"></a>Codice misto
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.

## <a name="see-also"></a>Vedi anche

- [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)