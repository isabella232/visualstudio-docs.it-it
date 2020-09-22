---
title: Creare visualizzatori personalizzati di dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839976"
---
# <a name="create-custom-visualizers-of-data"></a>Creare visualizzatori personalizzati di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I visualizzatori sono componenti dell' [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interfaccia utente del debugger. Un *Visualizzatore* crea una finestra di dialogo o un'altra interfaccia per visualizzare una variabile o un oggetto in modo appropriato al relativo tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come apparirebbe in una finestra del browser; un visualizzatore di bitmap interpreta una struttura di bitmap e visualizza l'oggetto grafico da essa rappresentato. Alcuni visualizzatori consentono inoltre di modificare i dati.  
  
 Il debugger di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] include sei visualizzatori standard. I visualizzatori di testo, HTML, XML e JSON, che possono essere usati per oggetti stringa; il visualizzatore dell'albero di WPF, per la visualizzazione delle proprietà della struttura ad albero visuale di un oggetto WPF; e il visualizzatore di dataset, che può essere usato per oggetti DataSet, DataView e DataTable. In futuro è possibile che Microsoft Corporation renda disponibili ulteriori visualizzatori per il download, mentre altri potranno essere disponibili tramite terze parti e dalla community. È inoltre possibile scrivere visualizzatori personalizzati e installarli nel debugger di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
> [!NOTE]
> Nelle app dello **Store** sono supportati solo i visualizzatori di testo, HTML, XML e JSON standard. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
 Nel debugger i visualizzatori sono rappresentati da un'icona a forma di lente di ingrandimento. Quando viene visualizzata l'icona a forma di lente di ingrandimento in un **DataTip**, in una finestra delle variabili del debugger o nella finestra di dialogo controllo **immediato** , è possibile fare clic sulla lente di ingrandimento per selezionare un visualizzatore appropriato per il tipo di dati dell'oggetto corrispondente.  
  
 I visualizzatori non sono supportati in Compact Framework.  
  
> [!NOTE]
> Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile. Di conseguenza, i visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale. Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)  
  
 [Procedura dettagliata: scrittura di un visualizzatore in C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)  
  
 [Procedura: eseguire il test e il debug di un visualizzatore](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
