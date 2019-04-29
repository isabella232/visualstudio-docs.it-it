---
title: 'Errore: RPC richiede autenticazione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850449"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Eseguire `\` *windir*`\system32\regedt32.exe`

2. Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Riavviare il computer per rendere effettiva la modifica del Registro di sistema.

4. Se il problema persiste, contattare l'amministratore di dominio sui **configurazione Computer > modelli amministrativi > sistema > Remote Procedure Call > restrizioni per i client RPC non autenticati** criteri di gruppo l'impostazione.