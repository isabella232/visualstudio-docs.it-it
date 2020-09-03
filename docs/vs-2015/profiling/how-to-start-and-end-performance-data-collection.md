---
title: 'Procedura: Iniziare e terminare la raccolta dei dati sulle prestazioni | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15c6d6c904bbab27bac541894ed6cd4f9e1f80f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202685"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Procedura: Iniziare e terminare la raccolta dei dati sulle prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prima di avviare la profilatura, è necessario aggiungere alla sessione di prestazioni il file binario di destinazione che si vuole profilare. Per aggiungere una destinazione, fare clic con il pulsante destro del mouse su **Destinazioni** in **Esplora prestazioni** e quindi fare clic su **Aggiungi binario di destinazione**. Nella finestra di dialogo **Aggiungi binario di destinazione** selezionare il nome del file e quindi fare clic su **Apri**. Verrà aggiunto un nuovo file binario.  
  
### <a name="to-start-profiling"></a>Per avviare la profilatura  
  
1. Fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni nella finestra **Esplora prestazioni** e scegliere una delle opzioni seguenti:  
  
    - **Avvio con analisi**: avvia l'applicazione e comincia immediatamente la profilatura.  
  
    - **Avvio con analisi sospeso**: avvia l'applicazione ma non comincia la profilatura. È possibile avviare la profilatura selezionando **Riprendi raccolta** nella finestra **Controllo raccolta dati**. Per altre informazioni, vedere [procedura: sospendere e riprendere la raccolta dei dati sulle prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Per terminare la profilatura  
  
- Il metodo consigliato per terminare una sessione di profilatura consiste nella chiusura dell'applicazione. Per terminare immediatamente la profilatura, nella barra degli strumenti di **Esplora prestazioni** fare clic su **Interrompi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo della raccolta dati](../profiling/controlling-data-collection.md)   
 [Procedura: sospendere e riprendere la raccolta dei dati sulle prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md)
