---
title: Creazione di visualizzatori personalizzati di dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8433af07b5f1315e73e6916e58123fcd14bddf0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792854"
---
# <a name="create-custom-visualizers-of-data"></a>Creazione di visualizzatori personalizzati di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I visualizzatori sono componenti del [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interfaccia utente del debugger. Oggetto *Visualizzatore* crea una finestra di dialogo o un'altra interfaccia per visualizzare una variabile o un oggetto in modo appropriato al relativo tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come apparirebbe in una finestra del browser; un visualizzatore di bitmap interpreta una struttura di bitmap e visualizza l'oggetto grafico da essa rappresentato. Alcuni visualizzatori consentono inoltre di modificare i dati.  
  
 Il debugger di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] include sei visualizzatori standard. Questi sono testo, HTML, XML e JSON visualizzatori, ognuno dei quali utilizzati per oggetti stringa; il Visualizzatore dell'albero di WPF, per la visualizzazione delle proprietà di una struttura visiva oggetto WPF; e il Visualizzatore di dataset, che funziona per gli oggetti DataSet, DataView e DataTable. In futuro è possibile che Microsoft Corporation renda disponibili ulteriori visualizzatori per il download, mentre altri potranno essere disponibili tramite terze parti e dalla community. È inoltre possibile scrivere visualizzatori personalizzati e installarli nel debugger di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
> [!NOTE]
>  Nelle **Store** le app, solo il testo standard, i visualizzatori HTML, XML e JSON sono supportati. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
 Nel debugger i visualizzatori sono rappresentati da un'icona a forma di lente di ingrandimento. Quando viene visualizzata l'icona di lente di ingrandimento in una **suggerimento dati**, nella finestra delle variabili del debugger o nel **controllo immediato** nella finestra di dialogo è possibile fare clic sulla lente di ingrandimento per selezionare un visualizzatore appropriato per il tipo di dati dell'oggetto corrispondente.  
  
 I visualizzatori non sono supportati in Compact Framework.  
  
> [!NOTE]
>  Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile. Di conseguenza, i visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale. Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)  
  
 [Procedura dettagliata: scrittura di un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)  
  
 [Procedura: Testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)



