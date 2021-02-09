---
title: Scheda generale, finestra di dialogo Proprietà finestra | Microsoft Docs
description: Visualizzare la scheda generale per informazioni su una finestra, inclusi didascalia, handle, rettangolo, handle dell'istanza dell'applicazione, handle di menu e dati utente.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1aa19ad99629f5106ee89876f347dfafd7520d26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870506"
---
# <a name="general-tab-window-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà finestra
Utilizzare la scheda **generale** per visualizzare informazioni sulla finestra selezionata. Per visualizzare la finestra di [dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra di [visualizzazione di Windows](../debugger/windows-view.md) . Selezionare un nodo della finestra nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **generale** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Titolo finestra**|Testo nella didascalia della finestra o testo contenuto in una finestra se è un controllo.|
|**Handle finestra**|ID univoco di questa finestra. I numeri di handle della finestra vengono riutilizzati. identificano una finestra solo per la durata di tale finestra.|
|**Routine finestra**|Indirizzo virtuale della funzione della routine della finestra per questa finestra. Questo campo indica anche se questa finestra è una finestra Unicode e se è sottoclassata.|
|**Rettangolo**|Rettangolo di delimitazione per la finestra. Viene visualizzata anche la dimensione del rettangolo. Le unità sono pixel nelle coordinate dello schermo.|
|**Rettangolo ripristinato**|Rettangolo di delimitazione per la finestra ripristinata. Viene visualizzata anche la dimensione del rettangolo. Il rettangolo ripristinato sarà diverso da Rectangle solo quando la finestra è ingrandita o ridotta a icona. Le unità sono pixel nelle coordinate dello schermo.|
|**Rettangolo client**|Rettangolo di delimitazione per l'area client della finestra. Viene visualizzata anche la dimensione del rettangolo. Le unità sono pixel rispetto alla parte superiore sinistra dell'area client della finestra.|
|**Handle istanza**|Handle dell'istanza dell'applicazione. Gli handle di istanza non sono univoci.|
|**ID controllo o handle di menu**|Se la finestra visualizzata è una finestra figlio, viene visualizzata l'etichetta ID controllo. ID controllo è un intero che identifica l'ID di controllo della finestra figlio. Se la finestra visualizzata non è una finestra figlio, viene visualizzata l'etichetta dell'handle di menu. Handle di menu è un intero che identifica l'handle del menu associato a questa finestra.|
|**Dati utente**|Dati specifici dell'applicazione associati a questa struttura della finestra.|
|**Byte finestra**|Numero di byte aggiuntivi associati a questa finestra. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|