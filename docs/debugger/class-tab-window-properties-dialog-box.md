---
title: Scheda Classe, finestra di dialogo Proprietà finestra | Microsoft Docs
description: Selezionare la scheda Classe in Visual Studio, spostare lo stato attivo sulla finestra Windows Visualizza, selezionare un nodo della finestra e scegliere Visualizza proprietà > per visualizzare la finestra di dialogo Proprietà finestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4179680ae5f5c55c322de8fbfc9552923ba3962a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630917"
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
Usare la **scheda** Classe per visualizzare informazioni sulla classe della finestra selezionata. Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla Windows [visualizzazione.](../debugger/windows-view.md) Selezionare qualsiasi nodo della finestra nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Classe sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Nome della classe**|Nome (o numero ordinale) di questa classe finestra.|
|**Stili classe**|Combinazione di codici di stile della classe.|
|**Byte classe**|Dati specifici dell'applicazione associati a questa classe di finestra.|
|**Atomo classe**|Atom per la classe restituita dalla **chiamata RegisterClass.**|
|**Handle istanza**|Handle di istanza del modulo che ha registrato la classe. Gli handle di istanza non sono univoci.|
|**Byte finestra**|Numero di byte aggiuntivi associati a ogni finestra di questa classe. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori dei byte in formato DWORD.|
|**Routine finestra**|Indirizzo corrente della **funzione WndProc** per le finestre di questa classe. Questo comportamento è diverso **da Window Proc** nella scheda **Generale** se la finestra è sottoclassata.|
|**Nome menu**|Nome del menu principale associato alle finestre di questa classe ("none" se non è presente alcun menu).|
|**Handle icona**|Handle per l'icona associata alle finestre di questa classe ("none" se non è presente alcuna icona).|
|**Handle cursore**|Handle per il cursore associato alle finestre di questa classe ("none" se non è presente alcun cursore).|
|**Riempimento sfondo**|Handle per il pennello di sfondo associato alle finestre di questa classe o uno dei colori COLOR_* predefiniti per disegnare lo sfondo della finestra ("nessuno" se non è presente alcun pennello).|