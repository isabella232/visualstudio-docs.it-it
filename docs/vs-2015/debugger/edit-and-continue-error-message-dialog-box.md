---
title: Finestra di dialogo modifica e continuazione messaggio di errore | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428294"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Finestra di dialogo di errore di Modifica e continuazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si esegue il debug in un linguaggio che supporta modifica e continuazione, ma la funzionalità **modifica e continuazione** non è disponibile per il tipo di modifiche apportate al codice. Nel messaggio di errore sono riportate informazioni più dettagliate. Questa finestra di dialogo può essere visualizzata per uno dei seguenti motivi:  
  
- Si è tentato di modificare il codice gestito mentre era abilitato il debug di codice non gestito. La funzionalità Modifica e continuazione non è compatibile con il debug in modalità mista.  
  
- Si è tentato di modificare il codice di SQL Server.  
  
- Si è tentato di modificare il codice durante il debug di un dump di Dr. Watson.  
  
- Si è tentato di modificare il codice dopo un'eccezione non gestita ed è stata selezionata l'opzione "**Rimuovi stack di chiamate su eccezioni non gestite**".  
  
- Si è tentato di modificare il codice durante il debug di un'applicazione di runtime incorporata.  
  
- Si è tentato di modificare il codice in un programma a cui si è connessi anziché iniziare dal menu **debug** .  
  
- Si è tentato di modificare il codice ottimizzato.  
  
- Si è tentato di modificare il codice gestito quando la destinazione è un'applicazione a 64 bit. Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86 (*Project* **Proprietà**progetto, scheda **Compila** , impostazione **del compilatore avanzata** ).  
  
- Si è tentato di modificare il codice in un assembly modificato durante il debug e ricaricato.  
  
- Si è tentato di modificare il codice in un assembly che non è stato caricato.  
  
- Si è avviato il debug di una versione precedente dell'applicazione, poiché la nuova versione presenta errori di compilazione.  
  
- Si è tentato di modificare il codice durante l'esecuzione.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **OK**  
 Chiudere la finestra di dialogo e annullare il tentativo di modifica immediatamente precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)
