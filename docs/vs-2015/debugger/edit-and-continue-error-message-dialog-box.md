---
title: Modifica e continuazione finestra di messaggio di errore | Microsoft Docs
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
ms.openlocfilehash: 73018dcdc34d3a824ff13da13fc12d03b8d13a7e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968224"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Finestra di dialogo di errore di Modifica e continuazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si esegue il debug in un linguaggio che supporta la modifica e continuazione, ma **modifica e continuazione** non è disponibile per il tipo di sono state apportate modifiche al codice. Nel messaggio di errore sono riportate informazioni più dettagliate. Questa finestra di dialogo può essere visualizzata per uno dei seguenti motivi:  
  
-   Si è tentato di modificare il codice gestito mentre era abilitato il debug di codice non gestito. La funzionalità Modifica e continuazione non è compatibile con il debug in modalità mista.  
  
-   Si è tentato di modificare il codice di SQL Server.  
  
-   Si è tentato di modificare il codice durante il debug di un dump di Dr. Watson.  
  
-   Si è provato a modificare il codice dopo che si è verificata un'eccezione non gestita e l'opzione "**Rimuovi stack di chiamate su eccezioni non gestite**" non è stato selezionato.  
  
-   Si è tentato di modificare il codice durante il debug di un'applicazione di runtime incorporata.  
  
-   Si è provato a modificare il codice in un programma che si era connessi anziché avviandolo dal **Debug** menu.  
  
-   Si è tentato di modificare il codice ottimizzato.  
  
-   Si è tentato di modificare il codice gestito quando la destinazione è un'applicazione a 64 bit. Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86 (*Project* **delle proprietà**, **compilare** scheda **del compilatore avanzate** impostazione.).  
  
-   Si è tentato di modificare il codice in un assembly modificato durante il debug e ricaricato.  
  
-   Si è tentato di modificare il codice in un assembly che non è stato caricato.  
  
-   Si è avviato il debug di una versione precedente dell'applicazione, poiché la nuova versione presenta errori di compilazione.  
  
-   Si è tentato di modificare il codice durante l'esecuzione.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **OK**  
 Chiudere la finestra di dialogo e annullare il tentativo di modifica immediatamente precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)
