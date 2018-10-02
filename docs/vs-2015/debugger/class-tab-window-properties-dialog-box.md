---
title: Scheda classe, finestra di dialogo Proprietà finestra | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a4be66a2eb725f2c81032b18414a2d6d624a0cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526195"
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [scheda classe, finestra di dialogo Proprietà finestra](https://docs.microsoft.com/visualstudio/debugger/class-tab-window-properties-dialog-box).  
  
Usare la **classe** pressione di tab per visualizzare informazioni sulla classe della finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **classe** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome di classe**|Il nome (o numero ordinale) di questa classe di finestra.|  
|**Stili delle classi**|Una combinazione dei codici di stile di classe.|  
|**Byte classe**|Dati specifici dell'applicazione associati a questa classe della finestra.|  
|**Classe Atom**|Il formato atom per la classe restituita dal **RegisterClass** chiamare.|  
|**Handle di istanza**|L'handle di istanza del modulo che ha registrato la classe. Gli handle di istanza non sono univoci.|  
|**Byte finestra**|Il numero di byte aggiuntivi associati a ogni finestra di questa classe. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|  
|**Routine finestra**|L'indirizzo corrente del **WndProc** funzione per le finestre di questa classe. Questo comportamento è diverso da **Window Proc** nel **generali** scheda se la finestra è una sottoclasse.|  
|**Nome del menu**|Il nome del menu principale di cui è associato alle finestre di questa classe ("none" Se non vi è alcun menu).|  
|**Handle dell'icona**|L'handle per l'icona associata a windows di questa classe ("none" Se non è presente alcuna icona).|  
|**Handle del cursore**|L'handle per il cursore tramite cui è associato alle finestre di questa classe ("none" se vi è alcun cursore).|  
|**Riempimento sfondo**|L'handle per il pennello di sfondo associata a windows di questa classe o uno dei colori predefiniti Color _ * per disegnare lo sfondo della finestra ("none" se è presente Nessun pennello).|



