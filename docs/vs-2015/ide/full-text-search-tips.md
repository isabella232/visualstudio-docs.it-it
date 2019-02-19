---
title: Suggerimenti per la ricerca full-text | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a015aeff983979bbb8f6ddedc245c74d3fb5f77b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54791708"
---
# <a name="full-text-search-tips"></a>Suggerimenti per la ricerca full-text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno dei metodi più utili per l'individuazione delle informazioni nella Guida consiste nell'eseguire una ricerca full-text. Per ottimizzare e personalizzare i risultati, è necessario comprendere l'impatto della sintassi sulla query. In questo argomento vengono illustrati suggerimenti, procedure e informazioni dettagliate sulla sintassi che aiutano a creare le query correttamente.  
  
## <a name="full-text-search-tips"></a>Suggerimenti per la ricerca full-text  
 Se si comprende in che modo la Guida interpreta la formattazione usata nelle query, sarà possibile creare ricerche più mirate che restituiscano solo gli argomenti di interesse. Tali formati includono caratteri speciali, parole riservate e filtri.  
  
### <a name="general-guidelines"></a>Indicazioni generali  
 Nella tabella seguente sono elencate alcune regole di base e linee guida per lo sviluppo di query di ricerca nella Guida.  
  
|Sintassi|Descrizione|  
|------------|-----------------|  
|Distinzione fra maiuscole e minuscole|Le ricerche non distinguono tra maiuscole e minuscole. Sviluppare i criteri di ricerca usando indifferentemente caratteri maiuscoli o minuscoli. Ad esempio, "OLE" e "ole" restituiscono gli stessi risultati.|  
|Combinazioni di caratteri|Non è possibile cercare solo singole lettere (a-z) o numeri (0-9). Se si tenta di cercare determinate parole riservate, come ad esempio "e", "da" e "con", queste verranno ignorate. Per altre informazioni, vedere "Parole ignorate nelle ricerche (parole non significative)" più avanti in questo argomento.|  
|Ordine di valutazione|Le query di ricerca vengono valutate da sinistra a destra.|  
  
### <a name="search-syntax"></a>Sintassi di ricerca  
 Se si specifica una stringa di ricerca che include più parole, ad esempio "parola1 parola2", tale stringa equivale all'immissione di "parola1 AND parola2", che restituisce solo gli argomenti che contengono tutte le singole parole nella stringa di ricerca.  
  
> [!IMPORTANT]
> 1. La ricerca di frasi non è supportata. Se si specifica più di una parola in una stringa di ricerca, gli argomenti restituiti conterranno tutte le parole che sono state specificate ma non necessariamente la frase esatta.  
>    2.  Usare gli operatori logici per specificare la relazione tra le parole nella frase di ricerca. È possibile includere operatori logici, come ad esempio AND, OR, NOT e NEAR, per limitare la ricerca. Ad esempio, se si cerca "dichiarazione NEAR unione", i risultati della ricerca includeranno argomenti contenenti le parole "dichiarazione" e "unione" distanti non più di alcune parole una dall'altra. Per altre informazioni, vedere [Logical Operators in Search Expressions](../ide/logical-operators-in-search-expressions.md) (Operatori logici nelle espressioni di ricerca).  
  
### <a name="filters"></a>Filtri  
 È possibile limitare ulteriormente i risultati di ricerca usando gli operatori di ricerca avanzata. La Guida include tre categorie che è possibile usare per filtrare i risultati della ricerca full-text: titolo, codice e parola chiave. Per altre informazioni, vedere [Advanced Search Operators in Search Expressions](../ide/advanced-search-operators-in-search-expressions.md) (Operatori di ricerca avanzata nelle espressioni di ricerca).  
  
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
