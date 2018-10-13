---
title: Gerarchia di chiamata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07d4cdc8551f7c8a8dbbcc14f682001a4bc8d83a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260084"
---
# <a name="call-hierarchy"></a>Gerarchia di chiamata
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
La gerarchia di chiamata consente di spostarsi nel codice visualizzando tutte le chiamate da e verso un metodo, una proprietà o un costruttore selezionato. Ciò consente di comprendere meglio il flusso del codice e di valutare gli effetti delle modifiche al codice. È possibile esaminare diversi livelli del codice per visualizzare le complesse catene di chiamate di metodi e i punti di ingresso aggiuntivi al codice, in modo da poter esplorare tutti i possibili percorsi di esecuzione.  
  
 La gerarchia di chiamata è disponibile in fase di progettazione, a differenza dello stack di chiamate che viene visualizzato dal debugger.  
  
## <a name="using-call-hierarchy"></a>Uso della gerarchia di chiamata  
 Per visualizzare la finestra **Gerarchia di chiamata**, fare clic con il pulsante destro del mouse sul nome di una chiamata a un metodo, una proprietà o un costruttore e quindi scegliere **Visualizza gerarchia delle chiamate**.  
  
 Il nome del membro viene visualizzato in un riquadro con visualizzazione struttura ad albero nella finestra **Gerarchia di chiamata**. Se si espande il nodo del membro, vengono visualizzati i sottonodi **Chiamate a**_nome membro_ e **Chiamate da**_nome membro_. La figura seguente mostra questi nodi nella finestra **Gerarchia di chiamata**.  
  
 ![Gerarchia di chiamata con un nodo aperto](../../ide/reference/media/onenode.png "OneNode")  
Finestra Gerarchia di chiamata  
  
-   Se si espande il nodo **Chiamate a**, vengono visualizzati tutti i membri che chiamano il membro selezionato.  
  
-   Se si espande il nodo **Chiamate da**, vengono visualizzati tutti i membri chiamati dal membro selezionato.  
  
 È quindi possibile espandere ognuno di questi membri dei sottonodi nei nodi **Chiamate a** e **Chiamate da**. In questo modo è possibile spostarsi nello stack dei chiamanti, come illustrato nella figura seguente.  
  
 ![Gerarchia di chiamata con più nodi aperti](../../ide/media/multiplenodes.png "MultipleNodes")  
Finestra Gerarchia di chiamata  
  
 Per i membri definiti come virtuali o astratti viene visualizzato un nodo **Overrides method name** (Esegui override nome metodo). Per i membri di interfaccia viene visualizzato un nodo **Implements method name** (Implementa nome metodo). Questi nodi espandibili vengono visualizzati allo stesso livello dei nodi **Chiamate a** e **Chiamate da**.  
  
 La casella **Ambito di ricerca** sulla barra degli strumenti include le opzioni **Soluzione personale**, **Progetto corrente** e **documento corrente**.  
  
 Quando si seleziona un membro figlio nel riquadro della visualizzazione struttura ad albero **Gerarchia di chiamata**:  
  
-   Il riquadro dei dettagli **Gerarchia di chiamata** visualizza tutte le righe di codice in cui tale membro figlio viene chiamato dal membro padre.  
  
-   La **finestra Definizione codice**, se aperta, visualizza il codice per il membro selezionato. Questa finestra è disponibile in C# e C++. Per altre informazioni su questa finestra, vedere [Visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  La finestra Gerarchia di chiamata non trova riferimenti ai gruppi di metodi, che includono le posizioni in cui un metodo viene aggiunto come gestore eventi o assegnato a un delegato. Per trovare tutti i riferimenti a un metodo, è possibile usare il comando **Trova tutti i riferimenti**.  
  
## <a name="shortcut-menu-items"></a>Comandi del menu di scelta rapida  
 La tabella seguente descrive i vari comandi del menu di scelta rapida disponibili quando si fa clic con il pulsante destro del mouse su un nodo nel riquadro della visualizzazione struttura ad albero.  
  
|Comando del menu di scelta rapida|Descrizione|  
|-----------------------|-----------------|  
|**Aggiungi come nuova radice**|Aggiunge il nodo selezionato al riquadro della visualizzazione struttura ad albero come un nuovo nodo radice. Questo permette di concentrare l'attenzione su un sottoalbero specifico.|  
|**Rimuovi radice**|Rimuove il nodo radice selezionato dal riquadro di visualizzazione albero. Questa opzione è disponibile solo da un nodo radice.<br /><br /> È anche possibile usare il pulsante della barra degli strumenti **Rimuovi radice** per rimuovere il nodo radice selezionato.|  
|**Vai a definizione**|Esegue il comando Vai a definizione nel nodo selezionato. Questo comando consente di passare alla definizione originale per una chiamata al membro o una definizione di variabile.<br /><br /> Per eseguire il comando Vai a definizione, è anche possibile fare doppio clic sul nodo selezionato o premere F12 nel nodo selezionato.|  
|**Trova tutti i riferimenti**|Esegue il comando Trova tutti i riferimenti nel nodo selezionato. Questo comando consente di trovare tutte le righe di codice nel progetto che fanno riferimento a una classe o a un membro.<br /><br /> È anche possibile usare MAIUSC + F12 per eseguire il comando Trova tutti i riferimenti nel nodo selezionato.|  
|**Copia**|Copia il contenuto del nodo selezionato (ma non i sottonodi).|  
|**Aggiorna**|Comprime il nodo selezionato in modo che espandendolo nuovamente vengano visualizzate le informazioni più recenti.|



