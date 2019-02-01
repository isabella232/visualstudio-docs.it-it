---
title: 'Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non stabilire la connessione al processo | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17511c5f89ca40cc002a80da955df10c8773b97c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952184"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo
Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione. Un processo non attendibile contenente codice malware può danneggiare il computer durante l'esecuzione del debug. Se si ritiene che il processo non sia attendibile, è opportuno fare clic su **Annulla** per impedire il debug.  
  
 Per eliminare questo avviso durante il debug di uno scenario legittimo, chiudere Visual Studio e impostare il valore di questa chiave del Registro di sistema su 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`e quindi riavviare Visual Studio. Dopo aver completato il debug dello scenario, reimpostare il valore su 0 e riavviare Visual Studio.  
  
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
 [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)