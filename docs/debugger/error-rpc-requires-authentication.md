---
description: Il debugger di Visual Studio non può connettersi al computer remoto.
title: RPC richiede l'autenticazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a2bc92ad4686c30db46ae62f38b10ac837535fa14bf56a2c9dadc22936d13dfa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420170"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Eseguire `\` *windir*`\system32\regedt32.exe`

2. Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Riavviare il computer per rendere effettiva la modifica del Registro di sistema.

4. Se il problema persiste, contattare l'amministratore di dominio per informazioni sull'impostazione dei criteri di gruppo > Modelli amministrativi > **System > Remote Procedure Call > Restrictions for Unauthenticated RPC clients** (Restrizioni per i client RPC non autenticati).
