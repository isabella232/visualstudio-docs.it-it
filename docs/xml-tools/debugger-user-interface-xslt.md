---
title: Finestre del debugger XSLT
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae37db21072e81a5940f09f085bf261839686a69
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646082"
---
# <a name="debugger-user-interface-xslt"></a>Interfaccia utente del debugger (XSLT)

Questo articolo descrive le finestre del debugger e le finestre di dialogo. Vengono illustrate solo le parti dell'interfaccia utente che hanno un comportamento di debug specifico di XSLT.

Per ulteriori informazioni, vedere la Guida di [riferimento all'interfaccia utente di debug](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Finestra Variabili locali

Nella finestra Variabili locali vengono visualizzate le informazioni sulle variabili definite nel foglio di stile. La finestra Variabili locali contiene tre colonne di informazioni:

**Nome**

Questa colonna contiene i nomi di tutte le variabili locali nell'ambito corrente. I set di nodi hanno un controllo albero di cui è possibile eseguire il drill-down per visualizzare le relative sottocartelle.

**Valore**

In questa colonna è visualizzato il valore contenuto da ciascuna variabile. Nei nodi Attribute, processing instruction, comment, text e CData viene visualizzato il valore di testo del nodo. Nei nodi Namespace viene visualizzato l'URI dello spazio dei nomi.

**Type**

In questa colonna viene identificato il tipo di dati di ogni variabile elencata nella colonna **nome** .

Nella finestra Variabili locali vengono inoltre visualizzate le variabili di contesto predefinite che tengono traccia del contesto della trasformazione XSLT. Nella tabella seguente vengono descritte le variabili di contesto predefinite usate dal debugger XSLT.

|Name|Descrizione|
|-|-----------------|
|`last()`|La dimensione del contesto.|
|`position()`|Posizione, ossia il numero di indice, del nodo di contesto, in base alla dimensione del contesto.|
|`self::node()`|Il valore del nodo di contesto.|

## <a name="output-window"></a>Output (finestra)

Nella finestra di output vengono visualizzati eventuali messaggi di errore o eccezioni di sicurezza che si verificano durante il debug. Viene inoltre visualizzato l'output del debugger.

## <a name="task-list"></a>Elenco attività

Il **elenco attività** elenca tutti gli errori di compilazione nel foglio di stile. Se si fa doppio clic sull'errore il cursore si sposta sulla riga contenente l'errore.

Il **elenco attività** include tutti gli errori che si verificano nei blocchi di script nel file XSLT.

> [!NOTE]
> Il debugger XSLT non contiene avvisi, quindi non vengono mai visualizzati nella **elenco attività**.

## <a name="breakpoints-window"></a>finestra Punti di interruzione

Nella finestra Punti di interruzione vengono visualizzati tutti i punti di interruzione impostati nel progetto corrente. Se si aggiunge un punto di interruzione mentre la finestra è visualizzata, la finestra viene aggiornata automaticamente per mostrare il nuovo punto di interruzione.

La finestra Punto di interruzione dovrebbe comportarsi allo stesso modo degli altri debugger di Visual Studio.

## <a name="watch-window"></a>Finestra Espressioni di controllo

La finestra Espressioni di controllo viene usata per valutare le variabili. È anche possibile modificare i valori delle variabili.

Le variabili visualizzate nella finestra Espressioni di controllo sono relative al contesto corrente (l'elemento in primo piano nello stack di chiamate). Se si modifica il contesto, la finestra viene aggiornata e vengono visualizzate le variabili impostate per quel determinato contesto.

## <a name="call-stack-window"></a>Finestra Stack di chiamate

La finestra **stack di chiamate** viene utilizzata per visualizzare i nomi delle funzioni nello stack di chiamate, i tipi di parametro e i valori dei parametri. Le informazioni relative allo stack di chiamate sono visualizzate solo quando il programma in fase di debug si trova in modalità interruzione.

Lo stack di chiamate rappresenta i vari contesti in cui si verifica l'esecuzione XSLT. Se, ad esempio, è presente una chiamata dal modello "a" al modello "b", il modello "a" e il modello "b" vengono visualizzati nella finestra **stack di chiamate** con il contesto corrente all'inizio dell'elenco. L'utente è in grado di visualizzare la query attualmente in esecuzione.

Se i modelli non dispongono di un nome nel file XSLT, vengono usati i nomi generati dal processore XSLT.

Se si fa clic su un elemento diverso da quello presente all'inizio dell'elenco, viene indicato al visualizzatore dove si è verificata la creazione di un ramo dell'esecuzione XSLT usando l'evidenziazione verde standard e le frecce verdi.

## <a name="quickwatch-dialog-box"></a>Controllo immediato (finestra di dialogo)

La finestra di dialogo controllo **immediato** viene utilizzata per valutare le espressioni XPath 1,0. Il nodo di contesto (il nodo `self::node()` proveniente dalla finestra Variabili locali) fornisce il contesto per l'esecuzione dell'espressione XPath. Il risultato dell'esecuzione dell'espressione XPath viene visualizzato nella finestra Espressioni di controllo.

Nell'elenco seguente vengono descritte le restrizioni relative alla valutazione dell'espressione XPath:

- Sono consentite solo le funzioni XPath incorporate.

- Non sono consentite funzioni XSLT predefinite, ad esempio `document()` e `key()`.

- Non sono consentite funzioni definite dall'utente.

Per altre informazioni, vedere [procedura: valutare un'espressione XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Disassembly (finestra)

Nella finestra Disassembly viene visualizzato il codice di assembly generato dal compilatore XSLT. Questa finestra può essere usata nello stesso modo in cui si usano tutte le altre finestre Disassembly di Visual Studio.

Per ulteriori informazioni, [procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Esaminare le variabili nelle finestre auto e variabili locali in Visual Studio](../debugger/autos-and-locals-windows.md)