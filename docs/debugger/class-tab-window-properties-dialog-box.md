---
title: Scheda classe, finestra di dialogo Proprietà finestra | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62565013"
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
Utilizzare la scheda **classe** per visualizzare le informazioni sulla classe della finestra selezionata. Per visualizzare la finestra di [dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra di [visualizzazione di Windows](../debugger/windows-view.md) . Selezionare un nodo della finestra nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **classe** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Nome classe**|Nome (o numero ordinale) di questa classe della finestra.|
|**Stili classe**|Combinazione di codici di stile della classe.|
|**Byte classe**|Dati specifici dell'applicazione associati a questa classe della finestra.|
|**Atomo classe**|Atom per la classe restituita dalla chiamata di **registerClass** .|
|**Handle istanza**|Handle dell'istanza del modulo che ha registrato la classe. Gli handle di istanza non sono univoci.|
|**Byte finestra**|Numero di byte aggiuntivi associati a ogni finestra di questa classe. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|
|**Routine finestra**|Indirizzo corrente della funzione **WndProc** per Windows di questa classe. Questo comportamento è diverso rispetto a **Window Proc** nella scheda **generale** se la finestra è sottoclassata.|
|**Nome menu**|Nome del menu principale associato a Windows di questa classe ("None" se non è presente alcun menu).|
|**Handle icona**|Handle per l'icona associata a Windows di questa classe ("None" se non è presente alcuna icona).|
|**Handle cursore**|Handle per il cursore associato a Windows di questa classe ("None" se non è presente alcun cursore).|
|**Riempimento sfondo**|Handle per il pennello di sfondo associato a finestre di questa classe oppure uno dei colori COLOR_ * predefiniti per disegnare lo sfondo della finestra ("None" se non è presente alcun pennello).|