---
title: Finestra di dialogo Proprietà finestra, scheda Generale | Microsoft Docs
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
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d699bda033a01e622925261bfa8455cae6f0f73a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526877"
---
# <a name="general-tab-window-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà finestra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [finestra di dialogo Proprietà finestra, scheda Generale](https://docs.microsoft.com/visualstudio/debugger/general-tab-window-properties-dialog-box).  
  
Usare la **generale** pressione di tab per visualizzare le informazioni sulla finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **generale** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Didascalia della finestra**|Il testo nel titolo della finestra o un testo contenuti in una finestra, se si tratta di un controllo.|  
|**Handle di finestra**|ID univoco di questa finestra. I numeri degli handle di finestra vengono riutilizzati; una finestra consentono di identificare solo per la durata di tale finestra.|  
|**Routine finestra**|L'indirizzo virtuale della funzione di routine della finestra per questa finestra. Questo campo indica anche se questa finestra è una finestra di Unicode e se è impostata come sottoclasse.|  
|**Rettangolo**|Il rettangolo di delimitazione per la finestra. Viene visualizzata anche le dimensioni del rettangolo. Le unità sono i pixel in coordinate dello schermo.|  
|**Rettangolo ripristinato**|Il rettangolo di delimitazione della finestra ripristinata. Viene visualizzata anche le dimensioni del rettangolo. Rettangolo ripristinato differisce dal rettangolo solo quando la finestra è ingrandita o ridotta a icona. Le unità sono i pixel in coordinate dello schermo.|  
|**Rettangolo client**|Il rettangolo di delimitazione per l'area client della finestra. Viene visualizzata anche le dimensioni del rettangolo. Le unità sono i pixel relativo alla parte superiore sinistra dell'area client della finestra.|  
|**Handle di istanza**|L'handle di istanza dell'applicazione. Gli handle di istanza non sono univoci.|  
|**ID di controllo o Handle Menu**|Se la finestra viene visualizzata una finestra figlio, viene visualizzata l'etichetta di ID di controllo. ID di controllo è un numero intero che identifica l'ID del controllo. della finestra figlio Se la finestra visualizzata non è una finestra figlio, viene visualizzata l'etichetta Handle Menu. Handle menu è un numero intero che identifica l'handle del menu associato a questa finestra.|  
|**Dati utente**|Dati specifici dell'applicazione che sono collegati a questa struttura della finestra.|  
|**Byte finestra**|Il numero di byte aggiuntivi associati a questa finestra. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|



