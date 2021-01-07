---
title: Scheda file di paging, finestra di dialogo Proprietà processo | Microsoft Docs
description: Utilizzare la scheda file di paging delle proprietà del processo per esaminare il file di paging di un processo. Questo articolo descrive le impostazioni disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47f4a2e9215cb2e98fdfefecdf978cb4a442ad84
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975056"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Scheda File di paging, finestra di dialogo Proprietà processo
Utilizzare la scheda **file** di paging per esaminare il file di paging di un processo. Per visualizzare la finestra di [dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo in una finestra [visualizzazione processi](../debugger/processes-view.md) . Selezionare un nodo di processo nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **file di paging** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Byte file di paging**|Numero corrente di pagine utilizzate da questo processo nel file di paging. Il file di paging archivia le pagine di dati utilizzate dal processo, ma non incluse in altri file. Il file di paging viene usato da tutti i processi e la mancanza di spazio nel file di paging può causare errori durante l'esecuzione di altri processi.|
|**N. max byte file di paging**|Numero massimo di pagine utilizzate dal processo nel file di paging.|
|**Errori di pagina**|Numero di errori di pagina dei thread in esecuzione in questo processo. Un errore di pagina si verifica quando un thread fa riferimento a una pagina di memoria virtuale che non si trova nel proprio working set nella memoria principale. Pertanto, la pagina non verrà recuperata dal disco se è presente nell'elenco di standby e quindi già nella memoria principale o se è utilizzata da un altro processo con cui la pagina è condivisa.|