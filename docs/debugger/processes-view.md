---
title: Visualizzazione processi | Microsoft Docs
description: Visualizzazione processi consente di visualizzare un albero di tutti i processi attivi nel sistema. Per ulteriori informazioni sui contenuti e sugli utilizzi, vedere i collegamenti a ulteriori informazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a52da28d01eac4f04081497888fbbfccaf4495e2
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975134"
---
# <a name="processes-view"></a>Visualizzazione processi
Nella visualizzazione processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati l'ID del processo e il nome del modulo. Utilizzare la visualizzazione processi se si desidera esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema".

 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere una o più finestre di primo livello associate. Ogni finestra di primo livello può essere proprietaria di una serie di finestre. Un simbolo + indica che un livello è compresso. La visualizzazione compressa è costituita da una riga per processo. Per espandere il livello, fare clic sul simbolo +.

 Utilizzare la visualizzazione processi se si desidera esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema". Per trovare un processo, comprimere l'albero ed eseguire una ricerca nell'elenco.

## <a name="procedures"></a>Procedure

#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione processi

1. Scegliere **processi** dal menu **Spy** .

   ![Visualizzazione processi di Spy&#43;&#43; ](../debugger/media/spy--_processes.png "_Processes di Spy + +") Visualizzazione processi di Spy + +

   Nella figura precedente viene illustrata la visualizzazione processi con i nodi processo e thread espansi.

### <a name="in-this-section"></a>Contenuto della sezione
 [Ricerca di un processo nella visualizzazione processi](../debugger/how-to-search-for-a-process-in-processes-view.md) Viene illustrato come trovare un processo specifico nella visualizzazione processi.

 [Visualizzazione delle proprietà del processo](../debugger/how-to-display-process-properties.md) Viene illustrato come visualizzare ulteriori informazioni su un messaggio.

### <a name="related-sections"></a>Sezioni correlate
 [Viste di Spy + +](../debugger/spy-increment-views.md) Illustra le visualizzazioni ad albero di Spy + + di Windows, i messaggi, i processi e i thread.

 [Uso di Spy + +](../debugger/using-spy-increment.md) Introduce lo strumento Spy + + e spiega come può essere usato.

 Finestra di [dialogo ricerca processi](../debugger/process-search-dialog-box.md) Utilizzato per trovare il nodo per un processo specifico nella visualizzazione processi.

 Finestra di [dialogo Proprietà processo](../debugger/process-properties-dialog-box.md) Consente di visualizzare le proprietà di un processo selezionato nella visualizzazione processi.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy + +.