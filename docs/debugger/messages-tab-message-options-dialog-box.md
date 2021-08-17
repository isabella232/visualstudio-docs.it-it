---
description: Usare la scheda Messaggi per selezionare i tipi di messaggio da elencare nella visualizzazione Messaggi e per specificare i criteri di ricerca dei messaggi.
title: Scheda Messaggi, finestra di dialogo Opzioni messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e1b81fd00da997912a0b9ad1ece7abc28136f8e7c7bb06fd91dd571d5cd752b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391252"
---
# <a name="messages-tab-message-options-dialog-box"></a>Scheda Messaggi, Finestra di dialogo Opzioni messaggio
Usare la **scheda Messaggi** per selezionare i tipi di messaggio da elencare in [Visualizzazione messaggi](../debugger/messages-view.md)e per specificare i criteri di ricerca dei messaggi. Per visualizzare la [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere Log Messages **(Registra** messaggi) dal menu **Spy.**

 In genere, selezionare prima **Gruppi di** messaggi e quindi ottimizzare la selezione selezionando singoli messaggi **per visualizzare**. Il **pulsante** Tutti seleziona tutti i tipi di messaggio e il **pulsante Nessuno** cancella tutti i tipi.

 Nella scheda Messaggi sono disponibili **le impostazioni** seguenti:

 **Messaggi da visualizzare** Selezionare messaggi specifici per la visualizzazione. Quando si crea una nuova finestra Messaggi, è possibile visualizzare tutti i messaggi. Quando si filtrano **i** messaggi dalla scheda Messaggi, tale filtro si applica solo ai nuovi messaggi, non ai messaggi già visualizzati nella Windows messaggi.

 **Gruppi di messaggi** Selezionare i gruppi di messaggi da visualizzare. I gruppi disponibili includono:

- WM_USER: con un codice maggiore o uguale a WM_USER

- Registrato: registrato con la **chiamata RegisterWindowMessage**

- Sconosciuto: messaggi sconosciuti nell'intervallo da 0 a (WM_USER - 1)

  Si noti che questi **gruppi di messaggi** non sono mappati a voci specifiche in Messaggi da **visualizzare**. Quando si seleziona un gruppo, la selezione viene applicata direttamente al flusso di messaggi.

  Una casella di  controllo disattivata all'interno dei gruppi di messaggi indica che la casella di riepilogo **Messaggi** da visualizzare è stata modificata per i messaggi in tale gruppo. non tutti i tipi di messaggio in tale gruppo sono selezionati.

  **Salva Impostazioni come predefinito** Salvare le impostazioni correnti per usarle in seguito come opzioni di ricerca dei messaggi. Queste impostazioni vengono salvate anche quando si esce da Spy++.
