---
title: Escludere o includere funzioni brevi nella strumentazione
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4aaae07987f1d3364b064465aa6edff9a4748301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329786"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Procedura: Escludere o includere funzioni brevi nella strumentazione
Per impostazione predefinita, gli strumenti di profilatura escludono le *funzioni piccole* dalla strumentazione. Le funzioni piccole sono funzioni brevi che non effettuano alcuna chiamata di funzione. L'esclusione di queste funzioni piccole fornisce un minore sovraccarico di strumentazione e di conseguenza assicura una migliore velocità di strumentazione. L'esclusione delle funzioni piccole riduce anche la dimensione del file di dati di profilatura delle prestazioni, con estensione *vsp*, e il tempo necessario per l'analisi. Se le funzioni piccole vengono escluse, il tempo in esse impiegato viene considerato nel tempo esclusivo e inclusivo delle relative funzioni padre. Le funzioni piccole possono essere escluse o incluse nella strumentazione, come descritto nella procedura seguente.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Per escludere o includere funzioni brevi nella strumentazione

1. In **Esplora prestazioni** selezionare **Sessione prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.

     Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

2. In **Pagine delle proprietà** fare clic sulle proprietà di **Strumentazione**.

3. Per escludere le funzioni brevi dalla strumentazione, selezionare **Escludi funzioni brevi da strumentazione**. Si tratta dell'impostazione predefinita.

     -oppure-

     Per includere le funzioni brevi nella strumentazione, deselezionare **Escludi funzioni brevi da strumentazione**.

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Controllare la raccolta dati](../profiling/controlling-data-collection.md)
- [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)
