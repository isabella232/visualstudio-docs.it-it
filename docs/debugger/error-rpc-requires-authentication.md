---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bb172455226ab290a74da07e97fc40deb30b6ba
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852550"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Esegui `\` *windir*`\system32\regedt32.exe`

2. Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Riavviare il computer per rendere effettiva la modifica del Registro di sistema.

4. Se il problema persiste, contattare l'amministratore di dominio per informazioni sulla **configurazione del Computer > Modelli amministrativi > sistema > Remote Procedure Call > restrizioni per i client RPC non autenticati** impostazione di criteri di gruppo.