---
title: 'CA1707: Gli identificatori non devono contenere caratteri di sottolineatura | Microsoft Docs'
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
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0aeea5c113ebebe33d4c371fed1a5c46da4e735e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211068"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Gli identificatori non devono contenere caratteri di sottolineatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [CA1707: gli identificatori non devono contenere caratteri di sottolineatura](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores) su docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Category|Microsoft.Naming|  
|Modifica importante|Interrompere l'esecuzione, quando generati sugli assembly<br /><br /> Non sostanziale - Quando generato nei parametri di tipo|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore contiene il carattere di sottolineatura (_).  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura (_). La regola controlla gli spazi dei nomi, tipi, membri e parametri.  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere tutti i caratteri di sottolineatura dal nome.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

