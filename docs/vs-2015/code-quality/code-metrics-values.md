---
title: I valori delle metriche del codice | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0c22a6659105a3d00f5c73cd880a33d357e216e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183456"
---
# <a name="code-metrics-values"></a>Valori della metrica del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Grazie all'uso della metrica del codice, gli sviluppatori possono comprendere quali tipi e/o i metodi devono essere rielaborati o più approfonditi. I team di sviluppo possono identificare i potenziali rischi, comprendere lo stato corrente di un progetto e tenere traccia dello stato durante lo sviluppo di software.  
  
## <a name="software-measurements"></a>Misurazioni di software  
 L'elenco seguente mostra i risultati di metrica codice [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Calcola:  
  
-   **Indice di manutenibilità** – calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice. Un valore elevato indica una migliore gestibilità. Le classificazioni di codifica a colori sono utilizzabile per identificare rapidamente aree problematiche nel codice. Una classificazione uguale a verde è compreso tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione uguale a giallo è compreso tra 10 e 19 e indica che il codice sia moderatamente gestibile. Una classificazione uguale a rosso è una classificazione compresa tra 0 e 9 e indica una manutenibilità insufficiente.  
  
-   **Complessità ciclomatica** : misura la complessità del codice strutturale. Viene creato dal calcolo del numero di percorsi del codice diversi nel flusso del programma. Un programma che ha il flusso di controllo complessi richiederà più test per ottenere buona copertura del codice e sarà meno facile da gestire.  
  
    > [!NOTE]
    >  In alcuni casi, il calcolo della complessità ciclomatica per un metodo in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] differisce dalle versioni precedenti. Per altre informazioni, vedere la sezione "modifiche in Visual Studio 2010 codice complessità calcoli" del [risoluzione dei problemi di metrica codice](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profondità dell'ereditarietà** – indica il numero di definizioni di classi che estendono alla radice della gerarchia di classi. Maggiore è la profondità della gerarchia più difficile è possibile conoscere in cui vengono definiti determinati metodi e campi o / e ridefinito.  
  
-   **Accoppiamento di classe** – misura l'accoppiamento di classi univoche tramite i parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanza generica o modello, le classi di base, le implementazioni dell'interfaccia, i campi definiti nei tipi esterni, e decorazione di attributo. Progettazione software di qualità impone che i tipi e metodi devono avere un'elevata coesione e accoppiamento basso. Accoppiamento elevato indica una progettazione che è difficile da riutilizzare e gestire a causa delle molte interdipendenze con altri tipi.  
  
-   **Righe di codice** – indica il numero approssimativo di righe di codice. Il conteggio è basato sul codice IL e non è pertanto il numero esatto di righe nel file del codice sorgente. Un numero molto elevato potrebbe indicare che un tipo o metodo sta provando a eseguire troppe operazioni e deve essere suddiviso. Può anche indicare che il tipo o metodo potrebbe essere difficile da gestire.  
  
## <a name="anonymous-methods"></a>Metodi anonimi  
 Un' *metodo anonimo* è semplicemente un metodo che non ha nome. Metodi anonimi vengono spesso usati per passare un blocco di codice come un parametro del delegato. I risultati della metrica per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, associati con il membro che dichiara il metodo. Non sono associati al membro che chiama il metodo.  
  
 Per altre informazioni sul modo in cui la metrica del codice gestisce i metodi anonimi, vedere [metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Codice generato  
 Alcuni strumenti software e i compilatori di generano il codice che viene aggiunto a un progetto e che lo sviluppatore di progetto non consente di visualizzare o non deve cambiare. In genere, la metrica del codice ignora il codice generato quando si calcola i valori delle metriche. In questo modo i valori delle metriche in base a ciò che lo sviluppatore può visualizzare e modificare.  
  
 Codice generato per i moduli di Windows non viene ignorato, poiché si tratta di codice che lo sviluppatore può visualizzare e modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



