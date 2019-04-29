---
title: Scheda classe, finestra di dialogo Proprietà finestra | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565013"
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare la **classe** pressione di tab per visualizzare informazioni sulla classe della finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **classe** scheda:  
  
|Voce|Descrizione|  
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
