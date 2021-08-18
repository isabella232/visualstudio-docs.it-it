---
title: Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato.
titleSuffix: ''
description: "'Si è verificato un errore DCOM durante il tentativo di contattare il computer remoto. L'accesso è stato negato.\" Visualizzare informazioni su questa Visual Studio di errore di debug remoto."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 53d8bbb4a4d053e4120cacfb1d44ca14295a3d22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052486"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato.
Il debug remoto usa DCOM per la comunicazione tra i computer locale e remoto nelle situazioni seguenti:

- Il debugger è impostato sulla  **modalità di compatibilità nativa** o la modalità di compatibilità gestita è selezionata nella pagina Strumenti > opzioni **> debug**

- Si esegue il debug di codice C++ (C++ /CLI) gestito.

- In Visual Studio 2013, quando **l'opzione Abilita** Modifica e continuazione nativa è selezionata nella pagina Strumenti **> opzioni > debug**

- Alcuni scenari di debug di terze parti

  Questo errore si verifica quando il processo di Visual Studio non è in grado di autenticarsi (o le credenziali fornite sono ritenute insufficienti) rispetto al processo del debugger remoto su DCOM. Una o più delle soluzioni seguenti possono risolvere il problema:

- Disattivare  **Usa modalità di compatibilità nativa** e **Modalità di compatibilità gestita**.

- In Visual Studio 2013 disattivare **Abilita Modifica e continuazione nativo**.

- Riavviare entrambi i computer.

- Se il debug remoto richiede l'immissioni di credenziali, selezionare l'opzione per salvarle.

## <a name="see-also"></a>Vedi anche

- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)