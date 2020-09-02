---
title: "Procedura: usare il Visualizzatore dell'albero di WPF | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825441"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Procedura: utilizzare il visualizzatore della struttura ad albero di WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare il visualizzatore dell'albero di WPF per esplorare la struttura ad albero visuale di un oggetto WPF e visualizzare le proprietà di dipendenza WPF per gli oggetti contenuti in tale albero. Per ulteriori informazioni sugli alberi visivi, vedere [strutture ad albero in WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Per ulteriori informazioni sulle proprietà di dipendenza, vedere [Cenni preliminari sulle proprietà di dipendenza](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Quando si apre il Visualizzatore della struttura ad albero di WPF, vengono visualizzati due riquadri: la **struttura ad albero visuale** a sinistra e il riquadro **Proprietà** _nome_**:**_tipo_ a destra. Selezionare un oggetto nel riquadro **struttura ad albero visuale** e il riquadro **Proprietà** _nome_**:**_tipo_ viene aggiornato automaticamente per visualizzare le proprietà dell'oggetto.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Per aprire il visualizzatore della struttura ad albero di WPF  
  
1. In un suggerimento dati, in una finestra **Espressioni di controllo**, **Auto** o **Variabili locali** fare clic sulla freccia della lente d'ingrandimento accanto al nome di un oggetto WPF.  
  
     Verrà visualizzato un elenco di visualizzatori.  
  
2. Fare clic su **Visualizzatore dell'albero di WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Per eseguire ricerche nella struttura ad albero visuale  
  
- Nel riquadro **Struttura ad albero visuale**, digitare la stringa da cercare nella casella **Cerca**.  
  
  Il visualizzatore della struttura ad albero di WPF troverà immediatamente il primo oggetto nella struttura ad albero visuale che corrisponde alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.  

  - Per passare alla corrispondenza successiva all'interno della struttura ad albero visuale, fare clic su **Successiva**.  

  - Per ritornare alla corrispondenza precedente, fare clic su **Prec**.  

  - Per cancellare i criteri di ricerca, fare clic su **Cancella**.  

### <a name="to-search-the-properties-list"></a>Per eseguire ricerche nell'elenco di proprietà  
  
- Nel riquadro **Proprietà** _nome_**:**_digitare_ la stringa che si desidera cercare nella casella **filtro** .  
  
  Il visualizzatore della struttura ad albero di WPF troverà immediatamente le proprietà che corrispondono alla stringa digitata; nell'elenco sono visualizzate soltanto le proprietà corrispondenti alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.  

  - Per cancellare i criteri di ricerca, fare clic su **Cancella**.  
  
### <a name="to-close-the-visualizer"></a>Per chiudere il visualizzatore  
  
- Fare clic sull'icona **Chiudi** nell'angolo in alto a destra della finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare un visualizzatore](../misc/how-to-use-a-visualizer.md)   
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Strutture ad albero in WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Cenni preliminari sulle proprietà di dipendenza](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
