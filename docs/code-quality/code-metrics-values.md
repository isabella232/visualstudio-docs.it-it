---
title: Calcolare la metrica del codice
ms.date: 11/02/2018
description: Informazioni su complessità ciclomatica, accoppiamento di classi e altre metriche di Visual Studio Code. Scopri come le metriche possono tenere traccia dello stato di avanzamento dello sviluppo e identificare i rischi.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f843df01059adef3a94bb46501e4e75bd67d5a7
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069487"
---
# <a name="code-metrics-values"></a>Valori della metrica del codice

L'aumento della complessità delle applicazioni software moderne aumenta anche la difficoltà di rendere il codice affidabile e gestibile. La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Sfruttando la metrica del codice, gli sviluppatori possono comprendere quali tipi e/o metodi devono essere rilavorati o testati in modo più accurato. I team di sviluppo possono identificare potenziali rischi, comprendere lo stato attuale di un progetto e tenere traccia dello stato di avanzamento durante lo sviluppo del software.

Gli sviluppatori possono usare Visual Studio per generare dati di metrica del codice che misurano la complessità e la gestibilità del codice gestito. È possibile generare dati di metrica del codice per un'intera soluzione o un singolo progetto.

Per informazioni su come generare dati di metrica del codice in Visual Studio, vedere [procedura: generare dati di metrica](../code-quality/how-to-generate-code-metrics-data.md)del codice.

## <a name="software-measurements"></a>Misurazioni software

L'elenco seguente mostra i risultati della metrica del codice calcolati da Visual Studio:

- **Indice di gestibilità** : calcola un valore di indice compreso tra 0 e 100 che rappresenta la semplicità relativa di gestione del codice. Un valore elevato significa una migliore gestibilità. È possibile usare le classificazioni con codifica a colori per identificare rapidamente le aree problematiche nel codice. Una classificazione verde è compresa tra 20 e 100 e indica che il codice ha una corretta gestibilità. Una classificazione gialla è compresa tra 10 e 19 e indica che il codice è moderatamente gestibile. Una classificazione rossa è una classificazione compresa tra 0 e 9 e indica una bassa gestibilità. Per ulteriori informazioni, vedere l' [intervallo di indici di gestibilità e il significato](code-metrics-maintainability-index-range-and-meaning.md).

- **Complessità ciclomatica** : misura la complessità strutturale del codice. Viene creato calcolando il numero di percorsi di codice diversi nel flusso del programma. Un programma con un flusso di controllo complesso richiede un numero maggiore di test per ottenere una code coverage efficace ed è meno gestibile. Per ulteriori informazioni, vedere la [voce Wikipedia relativa alla complessità di ciclomatica](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Depth of ereditarietà** : indica il numero di classi diverse che ereditano l'una dall'altra, tornando alla classe di base. La profondità dell'ereditarietà è simile all'accoppiamento della classe in quanto una modifica in una classe di base può influire sulle classi ereditate. Maggiore è questo numero, maggiore è l'ereditarietà e maggiore è il rischio che le modifiche della classe di base provochino una modifica di rilievo. Per la profondità dell'ereditarietà, un valore basso è buono e un valore elevato non è valido.

- **Accoppiamento della classe** : misura l'accoppiamento a classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanze generiche o di modello, classi base, implementazioni di interfacce, campi definiti su tipi esterni e decorazione di attributi. Una buona progettazione software impone che i tipi e i metodi abbiano una coesione elevata e un accoppiamento basso. Un accoppiamento elevato indica una progettazione difficili da riutilizzare e gestire a causa delle diverse interdipendenze di altri tipi. Per altre informazioni, vedere [accoppiamento delle classi](code-metrics-class-coupling.md).

::: moniker range=">=vs-2019"

- **Righe di codice sorgente** : indica il numero esatto di righe del codice sorgente presenti nel file di origine, incluse le righe vuote. Questa metrica è disponibile a partire da Visual Studio 2019 versione 16,4 e Microsoft. CodeAnalysis. Metrics (2.9.5).

- **Righe di codice eseguibile** : indica il numero approssimativo di righe o operazioni del codice eseguibile. Si tratta di un conteggio del numero di operazioni nel codice eseguibile. Questa metrica è disponibile a partire da Visual Studio 2019 versione 16,4 e Microsoft. CodeAnalysis. Metrics (2.9.5). Il valore è in genere una corrispondenza di chiusura con la metrica precedente, **righe di codice**, ovvero la metrica basata sull'istruzione MSIL utilizzata in modalità legacy.
::: moniker-end
::: moniker range="vs-2017"

- **Righe di codice** : indica il numero approssimativo di righe nel codice. Il conteggio è basato sul codice IL e pertanto non è il numero esatto di righe nel file di codice sorgente. Un conteggio elevato potrebbe indicare che un tipo o un metodo sta provando a eseguire troppe operazioni e deve essere suddiviso. Potrebbe inoltre indicare che il tipo o il metodo potrebbe essere difficile da gestire.

   > [!NOTE]
   > La [versione da riga di comando](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) dello strumento metrica codice conta le righe di codice effettive perché analizza il codice sorgente anziché il.
::: moniker-end

## <a name="anonymous-methods"></a>Metodi anonimi

Un *metodo anonimo* è semplicemente un metodo senza nome. I metodi anonimi vengono usati più frequentemente per passare un blocco di codice come parametro del delegato. I risultati della metrica del codice per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associate al membro che chiama il metodo.

## <a name="generated-code"></a>Codice generato

Alcuni strumenti e compilatori software generano codice aggiunto a un progetto e che lo sviluppatore del progetto non Visualizza o non deve essere modificato. Per lo più, la metrica del codice ignora il codice generato durante il calcolo dei valori delle metriche. In questo modo, i valori delle metriche riflettono ciò che lo sviluppatore può visualizzare e modificare.

Il codice generato per Windows Forms non viene ignorato perché è il codice che lo sviluppatore può visualizzare e modificare.

## <a name="next-steps"></a>Passaggi successivi

- [Procedura: generare dati di metrica del codice](../code-quality/how-to-generate-code-metrics-data.md)
- [Usare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)