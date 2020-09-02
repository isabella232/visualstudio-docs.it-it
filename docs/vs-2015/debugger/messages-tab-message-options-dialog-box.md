---
title: Scheda messaggi, finestra di dialogo Opzioni messaggio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149444"
---
# <a name="messages-tab-message-options-dialog-box"></a>Scheda Messaggi, Finestra di dialogo Opzioni messaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilizzare la scheda **messaggi** per selezionare i tipi di messaggi da elencare nella [visualizzazione messaggi](../debugger/messages-view.md)e per specificare i criteri di ricerca del messaggio. Per visualizzare la finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **Registra messaggi** dal menu **Spy** .  
  
 In genere, è innanzitutto necessario selezionare **gruppi di messaggi**e quindi ottimizzare la selezione selezionando i singoli **messaggi da visualizzare**. Il pulsante **All** seleziona tutti i tipi di messaggio e il pulsante **None** Cancella tutti i tipi.  
  
 Nella scheda **messaggi** sono disponibili le impostazioni seguenti:  
  
 **Messaggi da visualizzare**  
 Selezionare messaggi specifici per la visualizzazione. Quando si crea una nuova finestra messaggi, è possibile visualizzare tutti i messaggi. Quando si filtrano i messaggi dalla scheda **messaggi** , questo filtro si applica solo ai nuovi messaggi, non ai messaggi che sono già stati visualizzati nella visualizzazione di Windows.  
  
 **Gruppi di messaggi**  
 Selezionare gruppi di messaggi per la visualizzazione. I gruppi disponibili includono:  
  
- WM_USER: con un codice maggiore o uguale a WM_USER  
  
- Registrato: registrato con la chiamata a **RegisterWindowMessage**  
  
- Sconosciuto: messaggi sconosciuti nell'intervallo compreso tra 0 e (WM_USER-1)  
  
  Si noti che questi **gruppi di messaggi** non eseguono il mapping a voci specifiche in **messaggi da visualizzare**. Quando si seleziona un gruppo, la selezione viene applicata direttamente al flusso di messaggi.  
  
  Una casella di controllo in grigio all'interno dei **gruppi di messaggi** indica che la casella **di riepilogo messaggi da visualizzare** è stata modificata per i messaggi nel gruppo. non tutti i tipi di messaggio del gruppo sono selezionati.  
  
  **Salva impostazioni come predefinite**  
  Salvare le impostazioni correnti per utilizzarle successivamente come opzioni di ricerca dei messaggi. Queste impostazioni vengono salvate anche quando si esce da Spy + +.
