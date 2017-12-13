---
redirect_url: /visualstudio/ide/how-to-search-for-topics
ms.openlocfilehash: a66c168ca81b22c32fc05afddd01266950791d1e
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2017
---
title: "Suggerimenti per la ricerca full-text | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" f1_keywords: 
  - "hv_search" helpviewer_keywords: 
  - "Help Viewer, suggerimenti per la ricerca full-text"
  - "suggerimenti per la ricerca full-text [Help Viewer]" ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="full-text-search-tips"></a>Suggerimenti per la ricerca full-text
Uno dei metodi più utili per l'individuazione delle informazioni nella Guida consiste nell'eseguire una ricerca full-text. Se si comprendono gli effetti della sintassi sulle query, è possibile creare ricerche più mirate che restituiscano solo gli argomenti di interesse. La sintassi include caratteri speciali, parole riservate e filtri. In questo argomento vengono illustrati suggerimenti, procedure e informazioni dettagliate sulla sintassi che aiutano a creare le query correttamente.
  
### <a name="general-guidelines"></a>Indicazioni generali  
Nella tabella seguente sono elencate alcune regole di base e linee guida per lo sviluppo di query di ricerca nella Guida.  
  
|Sintassi|Descrizione|  
|------------|-----------------|  
|Distinzione fra maiuscole e minuscole|Le ricerche non distinguono tra maiuscole e minuscole. Sviluppare i criteri di ricerca usando indifferentemente caratteri maiuscoli o minuscoli. Ad esempio, "OLE" e "ole" restituiscono gli stessi risultati.|  
|Combinazioni di caratteri|Non è possibile cercare solo singole lettere (a-z) o singoli numeri (0-9). Se si tenta di cercare determinate parole riservate, ad esempio "e", "da" e "con", queste vengono ignorate. Per altre informazioni, vedere "Parole ignorate nelle ricerche (parole non significative)" più avanti in questo argomento.|  
|Ordine di valutazione|Le query di ricerca vengono valutate da sinistra a destra.|  
  
### <a name="search-syntax"></a>Sintassi di ricerca  
 Se si specifica una stringa di ricerca che include più parole, ad esempio "parola1 parola2", tale stringa equivale all'immissione di "parola1 AND parola2", che restituisce solo gli argomenti che contengono tutte le singole parole nella stringa di ricerca.  
  
> [!IMPORTANT]
> - La ricerca di frasi non è supportata. Se si specifica più di una parola in una stringa di ricerca, gli argomenti restituiti conterranno tutte le parole che sono state specificate ma non necessariamente la frase esatta.  
> - Usare gli operatori logici per specificare la relazione tra le parole nella frase di ricerca. È possibile includere operatori logici, come ad esempio AND, OR, NOT e NEAR, per limitare la ricerca. Ad esempio, se si cerca "dichiarazione NEAR unione", i risultati della ricerca includeranno argomenti contenenti le parole "dichiarazione" e "unione" distanti non più di alcune parole una dall'altra. Per altre informazioni, vedere [Logical Operators in Search Expressions](../ide/logical-operators-in-search-expressions.md) (Operatori logici nelle espressioni di ricerca).  
  
### <a name="filters"></a>Filtri  
 È possibile limitare ulteriormente i risultati di ricerca usando gli operatori di ricerca avanzata. La Guida include tre categorie che è possibile usare per filtrare i risultati della ricerca full-text: titolo, codice e parola chiave.
  
### <a name="ranking-of-search-results"></a>Classificazione dei risultati di ricerca  
 L'algoritmo di ricerca applica determinati criteri per consentire la classificazione superiore o inferiore dei risultati di ricerca nell'elenco dei risultati. In generale:  
  
1.  I contenuti che includono le parole di ricerca nel titolo sono classificati a un livello superiore rispetto ai contenuti che non le includono.  
  
2.  I contenuti che includono parole molto simili alle parole di ricerca sono classificati a un livello superiore rispetto ai contenuti che non le includono.  
  
3.  I contenuti che contengono una densità maggiore delle parole di ricerca sono classificati a un livello superiore rispetto ai contenuti che hanno una densità inferiore.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Parole ignorate nelle ricerche (parole non significative)  
 Alcune parole o numeri molto comuni, definiti a volte parole non significative, vengono ignorati automaticamente durante la ricerca full-text. Ad esempio, se si cerca la frase "passare a", i risultati visualizzeranno gli argomenti contenenti la parola "passare" ma non "a".  
  
## <a name="see-also"></a>Vedere anche
[Locate Information](../ide/locate-information.md)  (Individuare informazioni)  
[Logical Operators in Search Expressions](../ide/logical-operators-in-search-expressions.md) (Operatori logici nelle espressioni di ricerca)