---
title: 'Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cc42b63524a867c0893aa255180c740d03d4b5fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778765"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedura: Impostare le opzioni relative ai nomi file dei dati sulle prestazioni

Per impostazione predefinita, un file dei dati di profilatura con estensione *vsp* viene salvato con la sintassi seguente:

*Percorso\File-VSP\AAMMGG(N)* **.vsp**

È possibile modificare i parametri di denominazione nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni.

|||
|-|-|
|*Percorso*|Directory che contiene il rapporto. Il percorso predefinito è la cartella della soluzione o il percorso predefinito per i progetti e le soluzioni dell'utente.|
|*File-VSP*|Nome del file di dati di profilatura. Il nome predefinito è il nome della soluzione o del file eseguibile che viene profilato.|
|*AAMMGG*|Indicatore di data che indica l'anno, il mese e il giorno in cui sono stati raccolti i dati di profilatura.|
|*(N) Il*|Se esiste più di un file di dati di profilatura, al nome del file tra parentesi viene aggiunto un numero incrementato.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Per modificare la sintassi di denominazione dei file di dati di profilatura di una sessione di prestazioni

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi fare clic su **Proprietà**.

2. Fare clic su **General**.

3. In **Rapporto** modificare le impostazioni seguenti:

    |||
    |-|-|
    |**Percorso report**|Specificare una directory per archiviare i file di dati di profilatura.|
    |**Nome del report**|Specificare un nome di base per i file.|
    |**Aggiungere automaticamente nuovi rapporti alla sessione**|Selezionare la casella di controllo per aggiungere automaticamente il file di dati alla sessione di prestazioni.|
    |**Accodare un numero incrementale ai rapporti generati**|Selezionare la casella di controllo per aggiungere un numero incrementale al nome del file quando esiste più di un file con lo stesso nome. Deselezionare la casella di controllo per sovrascrivere un file esistente.|
    |**Utilizzare un timestamp per il numero**|Selezionare la casella di controllo per aggiungere un datestamp al nome del file.|
