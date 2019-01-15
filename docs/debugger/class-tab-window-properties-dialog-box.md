---
title: Scheda classe, finestra di dialogo Proprietà finestra | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37c02e529740bdfe5e2b0ed9bdfecd077ee05f4f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824327"
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
Usare la **classe** pressione di tab per visualizzare informazioni sulla classe della finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **classe** scheda:  
  
|Voce|Description|  
|-----------|-----------------|  
|**Nome di classe**|Il nome (o numero ordinale) di questa classe di finestra.|  
|**Stili classe**|Una combinazione dei codici di stile di classe.|  
|**Byte classe**|Dati specifici dell'applicazione associati a questa classe della finestra.|  
|**Atomo classe**|Il formato atom per la classe restituita dal **RegisterClass** chiamare.|  
|**Handle istanza**|L'handle di istanza del modulo che ha registrato la classe. Gli handle di istanza non sono univoci.|  
|**Byte finestra**|Il numero di byte aggiuntivi associati a ogni finestra di questa classe. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|  
|**Routine finestra**|L'indirizzo corrente del **WndProc** funzione per le finestre di questa classe. Questo comportamento è diverso da **Window Proc** nel **generali** scheda se la finestra è una sottoclasse.|  
|**Nome menu**|Il nome del menu principale di cui è associato alle finestre di questa classe ("none" Se non vi è alcun menu).|  
|**Handle icona**|L'handle per l'icona associata a windows di questa classe ("none" Se non è presente alcuna icona).|  
|**Handle cursore**|L'handle per il cursore tramite cui è associato alle finestre di questa classe ("none" se vi è alcun cursore).|  
|**Riempimento sfondo**|L'handle per il pennello di sfondo associata a windows di questa classe o uno dei colori predefiniti Color _ * per disegnare lo sfondo della finestra ("none" se è presente Nessun pennello).|