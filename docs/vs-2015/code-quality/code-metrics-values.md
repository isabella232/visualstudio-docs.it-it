---
title: Valori della metrica del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667729"
---
# <a name="code-metrics-values"></a>Valori della metrica del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Sfruttando la metrica del codice, gli sviluppatori possono comprendere quali tipi e/o metodi devono essere rilavorati o testati in modo più accurato. I team di sviluppo possono identificare potenziali rischi, comprendere lo stato attuale di un progetto e tenere traccia dello stato di avanzamento durante lo sviluppo del software.

## <a name="software-measurements"></a>Misurazioni software
 L'elenco seguente mostra i risultati della metrica del codice che [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] calcola:

- **Indice di gestibilità** : calcola un valore di indice compreso tra 0 e 100 che rappresenta la semplicità relativa di gestione del codice. Un valore elevato significa una migliore gestibilità. È possibile usare le classificazioni con codifica a colori per identificare rapidamente le aree problematiche nel codice. Una classificazione verde è compresa tra 20 e 100 e indica che il codice ha una corretta gestibilità. Una classificazione gialla è compresa tra 10 e 19 e indica che il codice è moderatamente gestibile. Una classificazione rossa è una classificazione compresa tra 0 e 9 e indica una bassa gestibilità.

- **Complessità ciclomatica** : misura la complessità strutturale del codice. Viene creato calcolando il numero di percorsi di codice diversi nel flusso del programma. Un programma con un flusso di controllo complesso richiederà un numero maggiore di test per ottenere una code coverage efficace e sarà meno gestibile.

    > [!NOTE]
    > In alcuni casi, il calcolo della complessità ciclomatica per un metodo in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] differisce dalle versioni precedenti. Per ulteriori informazioni, vedere la sezione "modifiche in Visual Studio 2010 calcoli di complessità del codice" per la risoluzione dei problemi relativi alla [metrica del codice](../code-quality/troubleshooting-code-metrics-issues.md).

- **Depth of ereditarietà** : indica il numero di definizioni di classe che si estendono alla radice della gerarchia di classi. Maggiore è la gerarchia, più difficile è capire dove vengono definiti o/o ridefiniti determinati metodi e campi.

- **Accoppiamento della classe** : misura l'accoppiamento a classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanze generiche o di modello, classi base, implementazioni di interfacce, campi definiti su tipi esterni e attributo effetto. Una buona progettazione software impone che i tipi e i metodi abbiano una coesione elevata e un accoppiamento basso. Un accoppiamento elevato indica una progettazione difficili da riutilizzare e gestire a causa delle diverse interdipendenze di altri tipi.

- **Righe di codice** : indica il numero approssimativo di righe nel codice. Il conteggio è basato sul codice IL e pertanto non è il numero esatto di righe nel file di codice sorgente. Un conteggio molto elevato potrebbe indicare che un tipo o un metodo sta provando a eseguire troppe operazioni e deve essere suddiviso. Potrebbe inoltre indicare che il tipo o il metodo potrebbe essere difficile da gestire.

## <a name="anonymous-methods"></a>Metodi anonimi
 Un *metodo anonimo* è semplicemente un metodo senza nome. I metodi anonimi vengono usati più frequentemente per passare un blocco di codice come parametro del delegato. I risultati delle metriche per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associate al membro che chiama il metodo.

 Per altre informazioni sul modo in cui le metriche del codice trattano i metodi anonimi, vedere [metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Codice generato
 Alcuni strumenti e compilatori software generano codice aggiunto a un progetto e che lo sviluppatore del progetto non Visualizza o non deve essere modificato. Per lo più, la metrica del codice ignora il codice generato durante il calcolo dei valori delle metriche. In questo modo, i valori delle metriche riflettono ciò che lo sviluppatore può visualizzare e modificare.

 Il codice generato per Windows Form non viene ignorato perché è il codice che lo sviluppatore può visualizzare e modificare.

## <a name="see-also"></a>Vedere anche
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
