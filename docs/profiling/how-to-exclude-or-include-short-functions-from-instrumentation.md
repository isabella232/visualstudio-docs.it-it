---
title: Escludere o includere funzioni brevi nella strumentazione
description: Per impostazione predefinita, le funzioni brevi che non chiamano altre funzioni vengono escluse dalla strumentazione per ridurre il sovraccarico. Informazioni su come includerli o escluderli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd541574efa9be7b58774d77aead729ceab92231
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141857"
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

## <a name="see-also"></a>Vedi anche
- [Controllare la raccolta dati](../profiling/controlling-data-collection.md)
- [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)
