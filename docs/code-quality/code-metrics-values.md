---
title: Calcolare le metriche del codice
ms.date: 11/02/2018
description: Informazioni sulla complessità tematica, sull'accoppiamento di classi e su altre metriche Visual Studio del codice. Informazioni su come le metriche possono tenere traccia dello stato di avanzamento dello sviluppo e identificare i rischi.
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
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: fbd74301a7a7ff1299b8d9496e20793bbfabdf6f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632057"
---
# <a name="code-metrics-values"></a>Valori delle metriche del codice

La maggiore complessità delle applicazioni software moderne aumenta anche la difficoltà di rendere il codice affidabile e gestibile. La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Sfruttando le metriche del codice, gli sviluppatori possono comprendere quali tipi e/o metodi devono essere rielaborati o testati in modo più approfondito. I team di sviluppo possono identificare potenziali rischi, comprendere lo stato corrente di un progetto e tenere traccia dello stato di avanzamento durante lo sviluppo del software.

Gli sviluppatori possono Visual Studio per generare dati di metrica del codice che misurano la complessità e la manutenibilità del codice gestito. I dati delle metriche del codice possono essere generati per un'intera soluzione o un singolo progetto.

Per informazioni su come generare dati di metrica del codice in Visual Studio, vedere [Procedura: Generare dati di metrica del codice.](../code-quality/how-to-generate-code-metrics-data.md)

## <a name="software-measurements"></a>Misurazioni software

L'elenco seguente mostra i risultati delle metriche del codice Visual Studio calcola:

- **Indice di** manutenibilità: calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa facilità di gestione del codice. Un valore elevato significa una migliore manutenibilità. Le classificazioni con codifica a colori possono essere usate per identificare rapidamente le aree di problemi nel codice. Una classificazione verde è compresa tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione gialla è compresa tra 10 e 19 e indica che il codice è moderatamente gestibile. Una classificazione rossa è una classificazione compresa tra 0 e 9 e indica una manutenibilità bassa. Per altre informazioni, vedere [Intervallo di indici di manutenibilità e significato.](code-metrics-maintainability-index-range-and-meaning.md)

- **Complessità tematica:** misura la complessità strutturale del codice. Viene creato calcolando il numero di percorsi di codice diversi nel flusso del programma. Un programma con un flusso di controllo complesso richiede più test per ottenere risultati code coverage ed è meno gestibile. Per altre informazioni, vedere la voce [di Wikipedia relativa alla complessità tematica.](https://wikipedia.org/wiki/Cyclomatic_complexity)

- **Profondità dell'ereditarietà:** indica il numero di classi diverse che ereditano l'una dall'altra, fino alla classe di base. La profondità dell'ereditarietà è simile all'accoppiamento di classi in cui una modifica in una classe di base può influire su qualsiasi classe ereditata. Maggiore è questo numero, maggiore sarà l'ereditarietà e maggiore sarà il rischio che le modifiche della classe di base comportano una modifica che causa un'interruzione. Per Depth of Inheritance, un valore basso è valido e un valore alto non è valido.

- **Accoppiamento di** classi: misura l'accoppiamento in classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate a metodi, istanze generiche o modello, classi di base, implementazioni di interfaccia, campi definiti su tipi esterni e decorazione di attributi. Una buona progettazione software impone che i tipi e i metodi debbano avere un accoppiamento elevato e basso. Un accoppiamento elevato indica una progettazione difficile da riutilizzare e gestire a causa delle numerose interdipendenze su altri tipi. Per altre informazioni, vedere [Accoppiamento di classi.](code-metrics-class-coupling.md)

::: moniker range=">=vs-2019"

- **Righe di codice sorgente:** indica il numero esatto di righe di codice sorgente presenti nel file di origine, incluse le righe vuote. Questa metrica è disponibile a partire Visual Studio 2019 versione 16.4 e Microsoft.CodeAnalysis.Metrics (2.9.5).

- **Righe di codice eseguibile:** indica il numero approssimativo di righe o operazioni di codice eseguibile. Conteggio del numero di operazioni nel codice eseguibile. Questa metrica è disponibile a partire Visual Studio 2019 versione 16.4 e Microsoft.CodeAnalysis.Metrics (2.9.5). Il valore è in genere una corrispondenza vicina alla metrica precedente, **Righe** di codice , ovvero la metrica basata su istruzioni MSIL usata in modalità legacy.
::: moniker-end
::: moniker range="vs-2017"

- **Righe di codice:** indica il numero approssimativo di righe nel codice. Il conteggio è basato sul codice IL e pertanto non è il numero esatto di righe nel file di codice sorgente. Un conteggio elevato potrebbe indicare che un tipo o un metodo sta tentando di eseguire troppe operazioni e deve essere suddiviso. Potrebbe anche indicare che il tipo o il metodo potrebbe essere difficile da gestire.

   > [!NOTE]
   > La [versione della riga di comando](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) dello strumento di metrica del codice conta le righe di codice effettive perché analizza il codice sorgente anziché IL.
::: moniker-end

## <a name="anonymous-methods"></a>Metodi anonimi

Un *metodo anonimo* è semplicemente un metodo senza nome. I metodi anonimi vengono usati più di frequente per passare un blocco di codice come parametro delegato. I risultati delle metriche del codice per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associati al membro che chiama il metodo .

## <a name="generated-code"></a>Codice generato

Alcuni strumenti software e compilatori generano codice che viene aggiunto a un progetto e che lo sviluppatore del progetto non vede o non deve modificare. Principalmente, le metriche del codice ignorano il codice generato quando calcola i valori delle metriche. In questo modo i valori delle metriche riflettono ciò che lo sviluppatore può visualizzare e modificare.

Il codice generato per Windows form non viene ignorato, perché è il codice che lo sviluppatore può visualizzare e modificare.

## <a name="next-steps"></a>Passaggi successivi

- [Procedura: Generare dati di metrica del codice](../code-quality/how-to-generate-code-metrics-data.md)
- [Usare la finestra Code Metrics Results (Risultati metriche codice)](../code-quality/working-with-code-metrics-data.md)