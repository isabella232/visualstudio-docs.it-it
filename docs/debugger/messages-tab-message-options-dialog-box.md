---
title: Scheda messaggi, finestra di dialogo Opzioni messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 858126d3de92b2247501da9b53aa305e4d8101d6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984834"
---
# <a name="messages-tab-message-options-dialog-box"></a>Scheda Messaggi, Finestra di dialogo Opzioni messaggio
Usare la **messaggi** pressione di tab per selezionare quali tipi di elenco nel messaggio [visualizzazione messaggi](../debugger/messages-view.md)e per specificare i criteri di ricerca di messaggi. Per visualizzare il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **i messaggi di Log** dal **Spy** menu.  
  
 In genere, si seleziona innanzitutto **gruppi di messaggi**e quindi ottimizzare la selezione selezionando singoli **dei messaggi alla visualizzazione**. Il **tutte** pulsante Seleziona tutti i tipi di messaggio e il **None** pulsante Cancella tutti i tipi.  
  
 Le impostazioni seguenti sono disponibili sul **messaggi** scheda:  
  
 **Messaggi da visualizzare**  
 Selezionare i messaggi specifici per la visualizzazione. Quando si crea una nuova finestra dei messaggi, è possibile visualizzare tutti i messaggi. Quando si filtrano i messaggi dal **messaggi** scheda, tale filtro si applica solo ai nuovi messaggi, non a quelli che sono già stati visualizzati nella visualizzazione di Windows.  
  
 **Gruppi di messaggi**  
 Selezionare i gruppi di messaggi per la visualizzazione. Gruppi disponibili includono:  
  
- WM_USER: con un codice maggiore di o uguale a WM_USER  
  
- Registrato: registrato con il **RegisterWindowMessage** chiamare  
  
- Sconosciuto: messaggi sconosciuti nell'intervallo da 0 a (WM_USER - 1)  
  
  Si noti che questi **gruppi di messaggi** non eseguono il mapping alle voci specifiche sotto **messaggi da visualizzare**. Quando si seleziona un gruppo, la selezione viene applicata direttamente al flusso di messaggi.  
  
  All'interno di una casella di controllo disabilitata **gruppi di messaggi** indica che il **messaggi da visualizzare** casella di riepilogo è stata modificata per i messaggi in tale gruppo; non tutti i tipi di messaggio in tale gruppo vengono selezionati.  
  
  **Salva impostazioni come predefinite**  
  Salvare le impostazioni correnti per un utilizzo successivo come le opzioni di ricerca di messaggi. Queste impostazioni vengono salvate anche quando si esce da Spy + +.