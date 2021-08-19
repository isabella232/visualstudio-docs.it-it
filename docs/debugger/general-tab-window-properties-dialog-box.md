---
title: Scheda Generale, finestra di dialogo Proprietà finestra | Microsoft Docs
description: Visualizzare la scheda Generale per informazioni su una finestra, tra cui didascalia, handle, rettangolo, handle dell'istanza dell'applicazione, handle di menu e dati utente.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce5dda5f3fb1581e5239d9d3ffcdee8de864498a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154304"
---
# <a name="general-tab-window-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà finestra
Usare la **scheda** Generale per visualizzare informazioni sulla finestra selezionata. Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo Windows [visualizzazione.](../debugger/windows-view.md) Selezionare qualsiasi nodo della finestra nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Generale sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Titolo finestra**|Testo nella didascalia della finestra o testo contenuto in una finestra se si tratta di un controllo .|
|**Handle finestra**|ID univoco di questa finestra. I numeri degli handle di finestra vengono riutilizzati. identificano una finestra solo per la durata di tale finestra.|
|**Routine finestra**|Indirizzo virtuale della funzione di routine della finestra per questa finestra. Questo campo indica anche se questa finestra è una finestra Unicode e se è sottoclassata.|
|**Rettangolo**|Rettangolo di delimitazione per la finestra. Vengono visualizzate anche le dimensioni del rettangolo. Le unità sono pixel nelle coordinate dello schermo.|
|**Rettangolo ripristinato**|Rettangolo di delimitazione per la finestra ripristinata. Vengono visualizzate anche le dimensioni del rettangolo. Restored Rect sarà diverso da Rectangle solo quando la finestra è ingrandita o ridotta a icona. Le unità sono pixel nelle coordinate dello schermo.|
|**Rettangolo client**|Rettangolo di delimitazione per l'area client della finestra. Vengono visualizzate anche le dimensioni del rettangolo. Le unità sono pixel rispetto alla parte superiore sinistra dell'area client della finestra.|
|**Handle istanza**|Handle di istanza dell'applicazione. Gli handle di istanza non sono univoci.|
|**ID controllo o handle di menu**|Se la finestra visualizzata è una finestra figlio, viene visualizzata l'etichetta ID controllo. L'ID controllo è un numero intero che identifica l'ID di controllo della finestra figlio. Se la finestra visualizzata non è una finestra figlio, viene visualizzata l'etichetta Handle di menu. L'handle di menu è un numero intero che identifica l'handle del menu associato a questa finestra.|
|**Dati utente**|Dati specifici dell'applicazione collegati a questa struttura della finestra.|
|**Byte finestra**|Numero di byte aggiuntivi associati a questa finestra. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori dei byte in formato DWORD.|