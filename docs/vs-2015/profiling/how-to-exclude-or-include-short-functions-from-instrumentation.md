---
title: 'Procedura: Escludere o includere funzioni brevi nella strumentazione | Microsoft Docs'
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
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f02e34e9fdb399aa8078342d3a8441f077a60f66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541046"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Procedura: Escludere o includere funzioni brevi nella strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: escludere o includere funzioni brevi nella strumentazione](https://docs.microsoft.com/visualstudio/profiling/how-to-exclude-or-include-short-functions-from-instrumentation).  
  
Per impostazione predefinita, gli strumenti di profilatura escludono le *funzioni piccole* dalla strumentazione. Le funzioni piccole sono funzioni brevi che non effettuano alcuna chiamata di funzione. L'esclusione di queste funzioni piccole fornisce un minore sovraccarico di strumentazione e di conseguenza assicura una migliore velocità di strumentazione. L'esclusione delle funzioni piccole riduce inoltre la dimensione del file di dati di profilatura delle prestazioni (con estensione vsp) e il tempo necessario per l'analisi. Se le funzioni piccole vengono escluse, il tempo in esse impiegato viene considerato nel tempo esclusivo e inclusivo delle relative funzioni padre. Le funzioni piccole possono essere escluse o incluse nella strumentazione, come descritto nella procedura seguente.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Per escludere o includere funzioni brevi nella strumentazione  
  
1.  In **Esplora prestazioni** selezionare **Sessione prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic sulle proprietà di **Strumentazione**.  
  
3.  Per escludere le funzioni brevi dalla strumentazione, selezionare **Escludi funzioni brevi da strumentazione**. Questa è l'impostazione predefinita.  
  
     oppure  
  
     Per includere le funzioni brevi nella strumentazione, deselezionare **Escludi funzioni brevi da strumentazione**.  
  
4.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)



