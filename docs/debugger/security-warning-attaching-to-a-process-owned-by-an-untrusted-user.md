---
description: Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione.
title: 'Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sembrano sospette o non si è sicuri, non connettersi a questo processo | Microsoft Docs'
ms.date: 1/15/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b0b60cc9a86f0eafce8378865b6161ef1c56a407
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636635"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo

Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione. Un processo non attendibile contenente codice malware può danneggiare il computer durante l'esecuzione del debug. Se si ritiene che il processo non sia attendibile, è opportuno fare clic su **Annulla** per impedire il debug.

Negli scenari IIS questo avviso può essere visualizzato se si usa un pool di applicazioni personalizzato, che non è attendibile.

Per eliminare questo avviso durante il debug di uno scenario legittimo:

1. Chiudere Visual Studio.

1. Impostare il valore della chiave del `DisableAttachSecurityWarning` Registro di sistema su 1.

   Trovare o creare la chiave in `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` e impostarla su 1.

   A partire Visual Studio 2017, se si vogliono visualizzare le impostazioni complete del Registro di sistema, è necessario caricare l'hive del Registro di sistema privato. Per altre informazioni, vedere [Come esaminare il registro Visual Studio 2017.](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md) Assicurarsi di scaricare l'hive del Registro di sistema privato prima di avviare Visual Studio.

1. Riavviare Visual Studio.

1. Dopo aver completato il debug dello scenario, reimpostare il valore su 0 e riavviare Visual Studio.

Tra gli utenti attendibili sono inclusi quello che esegue il debug e un set di utenti standard comunemente definiti nei computer in cui è installato .NET Framework, ad esempio `aspnet`, `localsystem`, `networkservice` e `localservice`.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

 Nome Nome dell'assembly richiesto per il debug

 Utente corrente

 Collega Premere per continuare a eseguire il debug collegando

 Non collegare Non connettersi al processo

## <a name="see-also"></a>Vedi anche
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
