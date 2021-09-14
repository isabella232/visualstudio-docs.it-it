---
title: Scheda File di pagina, finestra di dialogo Proprietà processo | Microsoft Docs
description: Usare la scheda File di paging di Proprietà processo per esaminare il file di paging di un processo. Questo articolo descrive le impostazioni disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c1c2e703a0c07e36594bc5fa67c5da6f2e060d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709901"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Scheda File di paging, finestra di dialogo Proprietà processo
Usare la **scheda File di** paging per esaminare il file di paging di un processo. Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione](../debugger/processes-view.md) processi. Selezionare un nodo di processo nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda File di pagina sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Byte file di paging**|Numero corrente di pagine utilizzato da questo processo nel file di paging. Il file di paging archivia le pagine di dati utilizzate dal processo, ma non contenute in altri file. Il file di paging viene usato da tutti i processi e la mancanza di spazio nel file di paging può causare errori durante l'esecuzione di altri processi.|
|**N. max byte file di paging**|Numero massimo di pagine utilizzate da questo processo nel file di paging.|
|**Errori di pagina**|Numero di errori di pagina da parte dei thread in esecuzione in questo processo. Un errore di pagina si verifica quando un thread fa riferimento a una pagina di memoria virtuale che non si trova nel proprio working set nella memoria principale. Di conseguenza, la pagina non verrà recuperata dal disco se è presente nell'elenco di standby e quindi è già presente nella memoria principale o se viene utilizzata da un altro processo con cui la pagina è condivisa.|