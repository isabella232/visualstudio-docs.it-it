---
title: Creare un report di confronto del profiler (riga di comando)
description: Usare VSPerfReport.exe dalla riga di comando per confrontare i risultati di due file di dati del profiler. Il confronto mostra le differenze tra le sessioni di profilatura.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 73ce7084a959e5ba21bcc22075c7452abc0186fed53abc72b1c97cc493200631
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426950"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Procedura: Creare un report di confronto del profiler dal prompt dei comandi
È possibile generare un report degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che confronta i dati sulle prestazioni di due file di dati di profilatura, con estensione *vsp* o *vsps*. Il report indica le differenze, le regressioni relative alle prestazioni e i miglioramenti riscontrati da una sessione di profilatura all'altra. I valori nel report presentano il delta o la modifica rispetto alla linea di base del primo file specificato. Il delta è calcolato determinando la differenza tra il valore precedente, che è il valore della linea di base, e il valore risultante dalla nuova analisi. I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione (IP) e tipi.

 Per elencare gli identificatori dei campi e delle categorie di confronto, digitare la riga di comando seguente:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Usare la sintassi seguente per creare il report di confronto:

 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 È possibile aggiungere le opzioni contenute nella tabella seguente alla riga di comando **VSPerfReport /diff**.

|Opzione|Descrizione|
|------------|-----------------|
|**DiffThreshold:**[*Value*]|Ignorare la differenza se al di sotto di questo valore di soglia in percentuale. Inoltre, i nuovi dati con valori al di sotto della soglia non verranno visualizzati.|
|**DiffTable:** *TableName*|Usare questa tabella per confrontare i file. Per impostazione predefinita, viene usata la tabella delle funzioni. Specificare l'identificatore elencato in **VSPerfReport /querydifftables**.|
|**DiffColumn:** *ColumnName*|Usare questa colonna per confrontare i valori. Per impostazione predefinita, viene usata la colonna percentuale campioni esclusivi. Specificare l'identificatore elencato in **VSPerfReport /querydifftables**.|
