---
title: Finestre del debugger XSLT
description: Informazioni sulle parti dell'interfaccia utente del debugger XSLT che controllano il comportamento di debug specifico di XSLT, tra cui le finestre Variabili locali, Output, Punti di interruzione, Stack di chiamate ed Espressioni di controllo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d5d5a0bd5e0c3885607db77343d20fc013467a93ce7e19be2387d84010556751
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351473"
---
# <a name="debugger-user-interface-xslt"></a>Interfaccia utente del debugger (XSLT)

Questo articolo descrive le finestre e le finestre di dialogo del debugger. Vengono illustrate solo le parti dell'interfaccia utente che hanno un comportamento di debug specifico di XSLT.

Per altre informazioni, vedere Le informazioni di riferimento [sull'interfaccia utente di debug.](../debugger/debugging-user-interface-reference.md)

## <a name="locals-window"></a>Finestra Variabili locali

Nella finestra Variabili locali vengono visualizzate le informazioni sulle variabili definite nel foglio di stile. La finestra Variabili locali contiene tre colonne di informazioni:

**Nome**

Questa colonna contiene i nomi di tutte le variabili locali nell'ambito corrente. I set di nodi hanno un controllo struttura ad albero di cui è possibile eseguire il drill-down per visualizzarne le sottocartelle.

**Valore**

In questa colonna è visualizzato il valore contenuto da ciascuna variabile. Nei nodi Attribute, processing instruction, comment, text e CData viene visualizzato il valore di testo del nodo. Nei nodi Namespace viene visualizzato l'URI dello spazio dei nomi.

**Tipo**

Questa colonna identifica il tipo di dati di ogni variabile elencata nella **colonna** Nome .

Nella finestra Variabili locali vengono inoltre visualizzate le variabili di contesto predefinite che tengono traccia del contesto della trasformazione XSLT. Nella tabella seguente vengono descritte le variabili di contesto predefinite usate dal debugger XSLT.

|Nome|Descrizione|
|-|-----------------|
|`last()`|La dimensione del contesto.|
|`position()`|Posizione, ossia il numero di indice, del nodo di contesto, in base alla dimensione del contesto.|
|`self::node()`|Il valore del nodo di contesto.|

## <a name="output-window"></a>Output (finestra)

Nella finestra di output vengono visualizzati eventuali messaggi di errore o eccezioni di sicurezza che si verificano durante il debug. Mostra anche l'output del debugger.

## <a name="task-list"></a>Elenco attività

Il **Elenco attività** elenca tutti gli errori di compilazione nel foglio di stile. Se si fa doppio clic sull'errore il cursore si sposta sulla riga contenente l'errore.

Il **Elenco attività** include eventuali errori che si verificano nei blocchi di script nel file XSLT.

> [!NOTE]
> Il debugger XSLT non ha avvisi, quindi non vengono mai visualizzati nel **Elenco attività**.

## <a name="breakpoints-window"></a>finestra Punti di interruzione

Nella finestra Punti di interruzione vengono visualizzati tutti i punti di interruzione impostati nel progetto corrente. Se si aggiunge un punto di interruzione mentre la finestra è visualizzata, la finestra viene aggiornata automaticamente per mostrare il nuovo punto di interruzione.

La finestra Punto di interruzione dovrebbe comportarsi allo stesso modo degli altri debugger di Visual Studio.

## <a name="watch-window"></a>Finestra Espressioni di controllo

La finestra Espressioni di controllo viene usata per valutare le variabili. È anche possibile modificare i valori delle variabili.

Le variabili visualizzate nella finestra Espressioni di controllo sono relative al contesto corrente (l'elemento in primo piano nello stack di chiamate). Se si modifica il contesto, la finestra viene aggiornata e vengono visualizzate le variabili impostate per quel determinato contesto.

## <a name="call-stack-window"></a>Finestra Stack di chiamate

La **finestra Stack di** chiamate viene usata per visualizzare i nomi delle funzioni nello stack di chiamate, i tipi di parametro e i valori dei parametri. Le informazioni relative allo stack di chiamate sono visualizzate solo quando il programma in fase di debug si trova in modalità interruzione.

Lo stack di chiamate rappresenta i vari contesti in cui si verifica l'esecuzione XSLT. Ad esempio, se è presente una chiamata dal modello "a" al modello "b", il modello "a" e il modello "b" vengono visualizzati nella finestra **Stack** di chiamate con il contesto corrente all'inizio dell'elenco. L'utente è in grado di visualizzare la query attualmente in esecuzione.

Se i modelli non dispongono di un nome nel file XSLT, vengono usati i nomi generati dal processore XSLT.

Se si fa clic su un elemento diverso da quello presente all'inizio dell'elenco, viene indicato al visualizzatore dove si è verificata la creazione di un ramo dell'esecuzione XSLT usando l'evidenziazione verde standard e le frecce verdi.

## <a name="quickwatch-dialog-box"></a>Controllo immediato (finestra di dialogo)

La **finestra di dialogo** Controllo immediato viene utilizzata per valutare le espressioni XPath 1.0. Il nodo di contesto (il nodo `self::node()` proveniente dalla finestra Variabili locali) fornisce il contesto per l'esecuzione dell'espressione XPath. Il risultato dell'esecuzione dell'espressione XPath viene visualizzato nella finestra Espressioni di controllo.

Nell'elenco seguente vengono descritte le restrizioni relative alla valutazione delle espressioni XPath:

- Sono consentite solo le funzioni XPath incorporate.

- Le funzioni XSLT incorporate, ad esempio `document()` e , non sono `key()` consentite.

- Non sono consentite funzioni definite dall'utente.

Per altre informazioni, vedere [Procedura: Valutare un'espressione XPath.](../xml-tools/how-to-evaluate-an-xpath-expression.md)

## <a name="disassembly-window"></a>Disassembly (finestra)

Nella finestra Disassembly viene visualizzato il codice di assembly generato dal compilatore XSLT. Questa finestra può essere usata nello stesso modo in cui si usano tutte le altre finestre Disassembly di Visual Studio.

Per altre informazioni, [vedere Procedura: Usare la finestra disassembly](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Vedi anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Esaminare le variabili nelle finestre auto e variabili locali in Visual Studio](../debugger/autos-and-locals-windows.md)
