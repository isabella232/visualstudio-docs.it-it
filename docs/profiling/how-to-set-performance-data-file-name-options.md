---
title: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni | Microsoft Docs
description: Informazioni su come modificare qualsiasi parametro di denominazione nella pagina Generale della finestra di dialogo delle proprietà per la sessione di prestazioni.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1b08b9e4f6abf28a95a3ca51a058981f04fe79f31867d7a0842b57771a0d1a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355022"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni

Per impostazione predefinita, un file dei dati di profilatura con estensione *vsp* viene salvato con la sintassi seguente:

*Path\VSP-File\YYMMDD(N)* **.vsp**

È possibile modificare i parametri di denominazione nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni.

|Parametro|Descrizione|
|-|-|
|*Percorso*|Directory che contiene il rapporto. Il percorso predefinito è la cartella della soluzione o il percorso predefinito per i progetti e le soluzioni dell'utente.|
|*File-VSP*|Nome del file di dati di profilatura. Il nome predefinito è il nome della soluzione o del file eseguibile che viene profilato.|
|*AAMMGG*|Indicatore di data che indica l'anno, il mese e il giorno in cui sono stati raccolti i dati di profilatura.|
|*(N)*|Se esiste più di un file di dati di profilatura, al nome del file tra parentesi viene aggiunto un numero incrementato.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Per modificare la sintassi di denominazione dei file di dati di profilatura di una sessione di prestazioni

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi fare clic su **Proprietà**.

2. Fare clic su **Generale**.

3. In **Rapporto** modificare le impostazioni seguenti:

    |Nome|Descrizione|
    |-|-|
    |**Percorso report**|Specificare una directory per archiviare i file di dati di profilatura.|
    |**Nome report**|Specificare un nome di base per i file.|
    |**Aggiungere automaticamente nuovi rapporti alla sessione**|Selezionare la casella di controllo per aggiungere automaticamente il file di dati alla sessione di prestazioni.|
    |**Accodare un numero incrementale ai rapporti generati**|Selezionare la casella di controllo per aggiungere un numero incrementale al nome del file quando esiste più di un file con lo stesso nome. Deselezionare la casella di controllo per sovrascrivere un file esistente.|
    |**Utilizzare un timestamp per il numero**|Selezionare la casella di controllo per aggiungere un datestamp al nome del file.|
