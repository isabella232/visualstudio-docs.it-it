---
title: Visualizzare la memoria per le variabili nel debugger | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdf8e5fc5ee0ac34b4c295f6cc593e0a93b548ae
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257264"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Usare le finestre di memoria nel debugger di Visual Studio (C#, C++, Visual Basic, F#)

Durante il debug, il **memoria** finestra Mostra lo spazio di memoria, l'app sta usando. 

Il debugger di windows, ad esempio **Watch**, **Auto**, **variabili locali**e il **controllo immediato** finestra di dialogo Mostra le variabili, che vengono archiviate per specifici posizioni di memoria. Il **memoria** finestra viene visualizzato al quadro generale. La visualizzazione della memoria è utile per esaminare grandi porzioni di dati (buffer o stringhe di grandi dimensioni, ad esempio) che non vengono visualizzate anche in altre finestre. 

Il **memoria** finestra non è limitata alla visualizzazione dei dati. Visualizza tutti gli elementi nello spazio di memoria, inclusi i dati, codice e casualmente in memoria non assegnata.  

Il **memoria** finestra non è disponibile per uno script o il debug SQL. Questi linguaggi non supportano il concetto di memoria.  
  
## <a name="open-a-memory-window"></a>Aprire una finestra memoria  
  
Quali altre finestre del debugger, il **memoria** windows sono disponibili solo durante una sessione di debug. 

>[!IMPORTANT]
>Per abilitare il **memoria** windows **Abilita debug a livello di indirizzo** deve essere selezionato nella **strumenti** > **opzioni** (o **Debug** > **opzioni**) > **debug** > **generale**. 

**Per aprire una finestra memoria**
  
1. Assicurarsi che **abilitare il debug a livello di indirizzo** sia selezionato nel **Tools** > **opzioni** (o **Debug**  >  **Le opzioni**) > **debug** > **generali**. 
   
1. Avviare il debug, selezionare la freccia verde, premendo **F5**, o selezionando **Debug** > **Avvia debug**.  
   
2. Sotto **Debug** > **Windows** > **memoria**selezionare **1 memoria**, **memoria 2**, **Memoria 3**, o **memoria 4**. (Alcune edizioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrono sola **memoria** finestra.)  

## <a name="move-around-in-the-memory-window"></a>Spostarsi nella finestra memoria  

Lo spazio degli indirizzi di un computer è esteso ed è facilmente possibile perdere il posto giusto mediante lo scorrimento nel **memoria** finestra. 

Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, scorrere verso il basso. Per visualizzare un indirizzo inferiore, scorrere verso l'alto.  

È possibile passare immediatamente a un indirizzo specificato nella **memoria** finestra mediante trascinamento e rilascio o immettendo l'indirizzo nel **indirizzo** campo. Il **indirizzi** campo accetta alfanumerici indirizzi e le espressioni che restituiscono indirizzi, ad esempio `e.User.NonroamableId`. 

Per forzare immediatamente rivalutazione di un'espressione nel **indirizzi** field, selezionare la freccia arrotondato **Rivaluta automaticamente** icona. 

Per impostazione predefinita, il **memoria** trattata nella finestra **indirizzo** espressioni come espressioni in tempo reale, che vengono nuovamente valutate come l'esecuzione dell'app. Le espressioni attive possono essere utile, ad esempio, per visualizzare la memoria selezionata da una variabile puntatore.  

**Per utilizzare il trascinamento della selezione per spostare in una posizione di memoria:**  
   
1. In qualsiasi finestra del debugger, selezionare un indirizzo di memoria o una variabile puntatore che contiene un indirizzo di memoria.  
   
2. Trascinare e rilasciare l'indirizzo o il puntatore nel **memoria** finestra. Tale indirizzo viene quindi visualizzata nel **indirizzi** campo e il **memoria** finestra viene modificata per visualizzare l'indirizzo nella parte superiore. 
  
**Per spostare in una posizione di memoria immettendola nel campo dell'indirizzo:**
  
- Digitare o incollare l'indirizzo o espressione nel **indirizzi** campo e premere **invio**, o sceglierlo dall'elenco a discesa nel **indirizzo** campo. Il **memoria** finestra viene modificata per visualizzare l'indirizzo nella parte superiore.
  
## <a name="customize-the-memory-window"></a>Personalizzare la finestra memoria 

Per impostazione predefinita, il contenuto della memoria vengono visualizzati come numeri interi da 1 byte in formato esadecimale e la larghezza della finestra determina il numero di colonne visualizzate. È possibile personalizzare il modo di **memoria** finestra Mostra il contenuto della memoria.  
  
**Per modificare il formato del contenuto della memoria:**  
  
-  Fare doppio clic nella **memoria** finestra e scegliere i formati desiderato dal menu di scelta rapida.  
  
**Per modificare il numero di colonne nella finestra Memoria:**
  
- Selezionare la freccia a discesa accanto al **colonne** campo e selezionare il numero di colonne da visualizzare oppure selezionare **automatico** regolazione automatica in base alla larghezza finestra.  
  
Se non si desidera il contenuto del **memoria** finestra per modificare l'App viene eseguita, è possibile disattivare la valutazione dell'espressione in tempo reale. 

**Per attivare o disattivare la valutazione diretta:**  
  
- Fare doppio clic nella **memoria** finestra e selezionare **Rivaluta automaticamente** nel menu di scelta rapida. 

  >[!NOTE]
  >Live espressione di valutazione e viceversa è attivata per impostazione predefinita, quindi selezionando **Rivaluta automaticamente** lo disattiva. Selezionando **Rivaluta automaticamente** nuovamente riattivato successivamente. 
  
È possibile nascondere o visualizzare la barra degli strumenti in cima il **memoria** finestra. Non si avrà accesso per il **indirizzo** campo o altri strumenti quando la barra degli strumenti è nascosta.  
  
**Per attivare o disattivare la visualizzazione della barra degli strumenti:**  
  
- Fare doppio clic nella **memoria** finestra e selezionare **Mostra barra degli strumenti** nel menu di scelta rapida. La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.  
  
## <a name="follow-a-pointer-through-memory"></a>Seguire un puntatore in memoria  

Nelle app di codice nativo, è possibile usare i nomi di registro come espressioni attive. È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.  
  
**Per seguire un puntatore in memoria:**
  
1. Nel **memoria** finestra **indirizzo** immettere un'espressione puntatore che si trova nell'ambito corrente. A seconda del linguaggio, può essere necessario dereferenziarla.  
  
2. Premere **INVIO**.  
   
   Quando si usa un comando di debug, ad esempio **passaggio**, l'indirizzo di memoria visualizzato nel **indirizzo** campo e in cima il **memoria** finestra cambia automaticamente quando il puntatore del mouse modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)