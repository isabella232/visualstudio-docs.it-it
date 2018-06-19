---
title: 'Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sospette o non si è certi, non connettersi a questo processo | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178008"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sospette o non si è certi, non connettersi al processo.
Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione. Un processo non attendibile contenente codice malware può danneggiare il computer durante l'esecuzione del debug. Se hai motivo per non considerare attendibile il processo, quindi è necessario fare clic **annullare** per impedire il debug.  
  
 Per non visualizzare questo avviso durante il debug di uno scenario legittimo, chiudere Visual Studio e impostare il valore di questa chiave del Registro di sistema su 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`e quindi riavviare Visual Studio. Dopo aver completato il debug dello scenario, reimpostare il valore su 0 e riavviare Visual Studio.  
  
 Tra gli utenti attendibili sono inclusi quello che esegue il debug e un set di utenti standard comunemente definiti nei computer in cui è installato .NET Framework, ad esempio `aspnet`, `localsystem`, `networkservice` e `localservice`.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 nome  
 Nome dell'assembly di cui è richiesto il debug  
  
 Utente  
 Utente corrente  
  
 Attach  
 Scegliere questo pulsante per connettersi al processo e proseguire il debug  
  
 Non connettersi  
 Non connettersi al processo  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)