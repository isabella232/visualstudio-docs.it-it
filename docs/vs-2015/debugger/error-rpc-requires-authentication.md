---
title: 'Errore: RPC richiede autenticazione | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e606c0e730b279723248a3fdbdd5b3e2bca1c4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520049"
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: RPC richiede autenticazione](https://docs.microsoft.com/visualstudio/debugger/error-rpc-requires-authentication).  
  
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Eseguire `\` *windir*`\system32\regedt32.exe`  
  
2.  Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Riavviare il computer per rendere effettiva la modifica del Registro di sistema.  
  
4.  Se il problema persiste, contattare l'amministratore di dominio sui **configurazione Computer -> modelli amministrativi - > sistema -> Remote Procedure Call -> restrizioni per i client RPC non autenticati** gruppo impostazione dei criteri.



