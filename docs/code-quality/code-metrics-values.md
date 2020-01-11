---
title: Calcola metrica codice
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886408"
---
# <a name="code-metrics-values"></a>Valori della metrica del codice

La maggiore complessità delle applicazioni software moderne aumenta anche la difficoltà di rendere il codice affidabile e facile da gestire. La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Grazie all'uso della metrica del codice, gli sviluppatori possono comprendere quali tipi e/o i metodi devono essere rielaborati o più approfonditi. I team di sviluppo possono identificare i potenziali rischi, comprendere lo stato corrente di un progetto e tenere traccia dello stato durante lo sviluppo di software.

Gli sviluppatori possono utilizzare Visual Studio per generare dati di metrica del codice che consentono di misurare la complessità e della manutenibilità del codice gestito. Dati di metrica codice possono essere generati per un'intera soluzione o un singolo progetto.

Per informazioni su come generare dati di metrica codice in Visual Studio, vedere [procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Misurazioni di software

L'elenco seguente mostra il codice di risultati di metrica per il calcolo di Visual Studio:

- **Indice di manutenibilità** -calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice. Un valore elevato indica una migliore gestibilità. Le classificazioni di codifica a colori sono utilizzabile per identificare rapidamente aree problematiche nel codice. Una classificazione uguale a verde è compreso tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione uguale a giallo è compreso tra 10 e 19 e indica che il codice sia moderatamente gestibile. Una classificazione uguale a rosso è una classificazione compresa tra 0 e 9 e indica una manutenibilità insufficiente. Per ulteriori informazioni, vedere il post di Blog relativo all' [intervallo di indici di manutenzione e al significato](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) .

- **Complessità ciclomatica** -misura la complessità del codice strutturale. Viene creato dal calcolo del numero di percorsi del codice diversi nel flusso del programma. Un programma con un flusso di controllo complesso richiede un numero maggiore di test per ottenere una code coverage efficace ed è meno gestibile. Per ulteriori informazioni, vedere la [voce Wikipedia relativa alla complessità di ciclomatica](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Depth of ereditarietà** : indica il numero di classi diverse che ereditano l'una dall'altra, tornando alla classe di base. La profondità dell'ereditarietà è simile all'accoppiamento della classe in quanto una modifica in una classe di base può influire sulle classi ereditate. Maggiore è questo numero, maggiore è l'ereditarietà e maggiore è il rischio che le modifiche della classe di base provochino una modifica di rilievo. Per la profondità dell'ereditarietà, un valore basso è buono e un valore elevato non è valido.

- **Accoppiamento di classe** -misura l'accoppiamento di classi univoche tramite i parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanza generica o modello, le classi di base, le implementazioni dell'interfaccia, i campi definiti nei tipi esterni, e decorazione di attributo. Progettazione software di qualità impone che i tipi e metodi devono avere un'elevata coesione e accoppiamento basso. Accoppiamento elevato indica una progettazione che è difficile da riutilizzare e gestire a causa delle molte interdipendenze con altri tipi. Per ulteriori informazioni, vedere il post di Blog relativo all' [accoppiamento della classe](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Righe di codice sorgente** : indica il numero esatto di righe del codice sorgente presenti nel file di origine, incluse le righe vuote. Questa metrica è disponibile a partire da Visual Studio 2019 versione 16,4 e Microsoft. CodeAnalysis. metriche (2.9.5).

- **Righe di codice eseguibile** : indica il numero approssimativo di righe o operazioni del codice eseguibile. Si tratta di un conteggio del numero di operazioni nel codice eseguibile. Questa metrica è disponibile a partire da Visual Studio 2019 versione 16,4 e Microsoft. CodeAnalysis. metriche (2.9.5). Il valore è in genere una corrispondenza di chiusura con la metrica precedente, **righe di codice**, ovvero la metrica basata sull'istruzione MSIL utilizzata in modalità legacy.
::: moniker-end
::: moniker range="vs-2017"

- **Righe di codice** -indica il numero approssimativo di righe di codice. Il conteggio è basato sul codice IL e non è pertanto il numero esatto di righe nel file del codice sorgente. Un conteggio elevato potrebbe indicare che un tipo o un metodo sta provando a eseguire troppe operazioni e deve essere suddiviso. Può anche indicare che il tipo o metodo potrebbe essere difficile da gestire.

   > [!NOTE]
   > Il [versione della riga di comando](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) del codice strumento metriche conta le righe effettive di codice perché analizza il codice sorgente anziché IL.
::: moniker-end

## <a name="anonymous-methods"></a>Metodi anonimi

Un' *metodo anonimo* è semplicemente un metodo che non ha nome. Metodi anonimi vengono spesso usati per passare un blocco di codice come un parametro del delegato. I risultati della metrica del codice per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associati al membro che chiama il metodo.

## <a name="generated-code"></a>Codice generato

Alcuni strumenti software e i compilatori di generano il codice che viene aggiunto a un progetto e che lo sviluppatore di progetto non consente di visualizzare o non deve cambiare. In genere, la metrica del codice ignora il codice generato quando si calcola i valori delle metriche. In questo modo i valori delle metriche in base a ciò che lo sviluppatore può visualizzare e modificare.

Codice generato per i moduli di Windows non viene ignorato, poiché si tratta di codice che lo sviluppatore può visualizzare e modificare.

## <a name="next-steps"></a>Passaggi successivi

- [Procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilizzare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)
