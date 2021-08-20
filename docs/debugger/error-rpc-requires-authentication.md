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
ms.openlocfilehash: 6de57ce80e15087b7c66986e0c44a3d7a1e3868e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154482"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Eseguire `\` *windir*`\system32\regedt32.exe`

2. Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Riavviare il computer per rendere effettiva la modifica del Registro di sistema.

4. Se il problema persiste, contattare l'amministratore di dominio per l'impostazione dei criteri di gruppo Configurazione computer **> Modelli amministrativi > System > Remote Procedure Call > Restrictions for Unauthenticated RPC clients** (Restrizioni per i client RPC non autenticati).
