---
title: 'CA1702: le Parole composte devono essere digitate correttamente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cfc723e94b8be2f427be7b42d676218b0d9aa68d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201135"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [CA1702 le: le parole composte devono essere digitate correttamente](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) su docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Category|Microsoft.Naming|  
|Modifica importante|Rilievo-when generato su assembly.<br /><br /> Non sostanziale - Quando viene attivato su parametri di tipo.|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore contiene più parole e almeno una delle parole sembra essere una parola composta che non è digitata correttamente.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il nome dell'identificatore è suddiviso in parole che si basano le maiuscole e minuscole. Ogni combinazione di due parole contigui viene controllata dalla libreria del correttore ortografico Microsoft. Se è riconosciuta, l'identificatore genera una violazione della regola. Sono esempi di parole composte che causano una violazione "CheckSum" e "MultiPart", che devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, numerose eccezioni sono incorporate nella regola, e sono contrassegnate molte parole singole, ad esempio "Toolbar" e "Filename", che devono essere digitati due parole di distinte (in questo caso, "ToolBar" e "FileName").  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare il nome in modo che viene maiuscole e minuscole.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografici e l'intento consiste nell'usare due parole.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida sulla denominazione](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Convenzioni per l'uso di maiuscole e minuscole](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

