---
title: Finestre di memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
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
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158461"
---
# <a name="memory-windows"></a>Finestra Memoria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra **memoria** fornisce una visualizzazione dello spazio di memoria usato dall'applicazione. Nella finestra **espressioni di controllo** , nella finestra di dialogo controllo **immediato** , nella finestra **auto** e variabili **locali** viene visualizzato il contenuto delle variabili, archiviate in posizioni specifiche in memoria. Tuttavia, nella finestra **memoria** viene visualizzata l'immagine su larga scala. Questa visualizzazione può essere opportuna quando si intende esaminare grandi porzioni di dati, ad esempio buffer o stringhe di notevoli dimensioni, che non vengono visualizzate adeguatamente nella altre finestre. Tuttavia, la finestra **memoria** non è limitata alla visualizzazione dei dati. Nella finestra Memoria viene visualizzato ogni tipo di contenuto dello spazio di memoria, sia che si tratti di dati, di codice o di contenuto eliminato e collocato casualmente in spazio di memoria non assegnato.  
  
 La finestra **memoria** è disponibile solo se il debug a livello di indirizzo è abilitato nella finestra di dialogo **Opzioni** , nodo**debug** . La finestra **memoria** non è disponibile per script o SQL, ovvero linguaggi che non riconoscono il concetto di memoria.  
  
## <a name="opening-a-memory-window"></a>Apertura di una finestra Memoria  
  
#### <a name="to-open-a-memory-window"></a>Per aprire una finestra Memoria  
  
1. Avviare il debug, se la modalità di debug non è ancora attiva.  
  
2. Scegliere **finestre**dal menu **debug** . Quindi, scegliere **memoria** , quindi fare clic su **memoria 1**, **memoria 2**, **memoria 3**o **memoria 4**. Le edizioni di livello inferiore di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hanno una sola finestra di **memoria** . Se si usa una di queste edizioni, è sufficiente fare clic su **memoria**.  
  
## <a name="paging-in-the-memory-window"></a>Paging nella finestra Memoria  
 La finestra **memoria** ha una barra di scorrimento verticale che funziona in modo non standard. Poiché lo spazio degli indirizzi di un moderno computer è molto ampio, trascinando il cursore su una posizione casuale sarebbe facile perderne la posizione. Per questa ragione, la casella di scorrimento è fluttuante e rimane sempre al centro della barra di scorrimento. Nelle applicazioni in codice nativo è possibile spostarsi verso l'alto o verso il basso dello spazio di memoria, ma non è consentito lo scorrimento casuale.  
  
 Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, spostarsi verso il basso, non verso l'alto.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Per spostarsi verso l'alto o verso il basso di una pagina di memoria  
  
1. Per spostarsi verso il basso, ovvero verso un indirizzo di memoria superiore, fare clic sulla barra di scorrimento verticale sotto il cursore.  
  
2. Per spostarsi verso l'alto, ovvero verso un indirizzo di memoria inferiore, fare clic sulla barra di scorrimento verticale sopra il cursore.  
  
## <a name="selecting-a-memory-location"></a>Selezione di un indirizzo di memoria  
 Se si desidera spostarsi immediatamente in una posizione selezionata in memoria, è possibile utilizzare un'operazione di trascinamento della selezione o modificando il valore nella casella **Indirizzo** . La casella degli **indirizzi** accetta non solo valori numerici, ma anche espressioni che restituiscono indirizzi. Per impostazione predefinita, la finestra di **memoria** considera un'espressione di **Indirizzo** come espressione Live, che viene rivalutata durante l'esecuzione del programma. Le espressioni attive possono rivelarsi molto utili. Ad esempio, possono essere utilizzate per visualizzare la memoria selezionata da un puntatore.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Per selezionare un indirizzo di memoria mediante trascinamento e rilascio  
  
1. Da qualsiasi finestra selezionare un indirizzo di memoria o una variabile puntatore contenente un indirizzo di memoria.  
  
2. Trascinare l'indirizzo o il puntatore sulla finestra **memoria** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Per selezionare una posizione di memoria mediante modifica  
  
1. Nella finestra **memoria** selezionare la casella **Indirizzo** .  
  
2. Digitare o incollare l'indirizzo che si desidera visualizzare, quindi premere **invio**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Modifica della modalità di visualizzazione delle informazioni nella finestra Memoria  
 È inoltre possibile personalizzare il modo in cui il contenuto della memoria viene visualizzato nella finestra **Memoria**. Per impostazione predefinita, il contenuto della memoria viene visualizzato come dati integer a 1 byte in formato esadecimale e con un numero di colonne determinato automaticamente dalla larghezza corrente della finestra.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Per cambiare il formato del contenuto della memoria  
  
1. Fare clic con il pulsante destro del mouse sulla finestra **memoria** .  
  
2. Scegliere il formato desiderato.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Per modificare il numero di colonne nella finestra Memoria  
  
1. Nella barra degli strumenti nella parte superiore della finestra **memoria** individuare l'elenco **colonne** .  
  
2. Nell'elenco **colonne** selezionare il numero di colonne che si desidera visualizzare o selezionare **auto** per la regolazione automatica in base alla larghezza della finestra.  
  
   Se non si desidera modificare il contenuto della finestra di **memoria** durante l'esecuzione del programma, è possibile disattivare la valutazione dell'espressione Live.  
  
#### <a name="to-toggle-live-evaluation"></a>Per attivare o disattivare la valutazione diretta  
  
1. Fare clic con il pulsante destro del mouse sulla finestra **memoria** .  
  
2. Nel menu di scelta rapida fare clic su **Rivaluta automaticamente**.  
  
    Se la valutazione diretta è attiva, l'opzione risulterà selezionata e facendo clic su di essa la valutazione diretta verrà disattivata. Se la valutazione diretta non è attiva, l'opzione risulterà deselezionata e facendo clic su di essa verrà attivata.  
  
   È possibile nascondere o visualizzare la barra degli strumenti nella parte superiore della finestra **Memoria**. Non è possibile accedere alla casella Indirizzo o ad altri strumenti quando la barra degli strumenti è nascosta.  
  
#### <a name="to-toggle-the-toolbar"></a>Per attivare o disattivare la barra degli strumenti  
  
1. Fare clic con il pulsante destro del mouse sulla finestra **memoria** .  
  
2. Scegliere **Mostra barra degli strumenti**dal menu di scelta rapida.  
  
     La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.  
  
## <a name="following-a-pointer-through-memory"></a>Come seguire il movimento di un puntatore in memoria  
 Nelle applicazioni in codice nativo è inoltre possibile utilizzare i nomi di registro come espressioni attive. È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Per osservare il movimento di un puntatore in memoria  
  
1. Nella casella **Indirizzo** della finestra **memoria** Digitare un'espressione puntatore. La variabile puntatore deve trovarsi nell'ambito corrente. A seconda del linguaggio, può essere necessario dereferenziarla.  
  
2. Premere **INVIO**.  
  
     A questo punto, quando si usa un comando di esecuzione, ad esempio **Step**, l'indirizzo di memoria visualizzato cambierà automaticamente quando cambia il puntatore.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
