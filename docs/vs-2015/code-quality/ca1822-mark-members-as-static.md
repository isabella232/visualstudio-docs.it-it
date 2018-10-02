---
title: 'CA1822: Contrassegna i membri come statici | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f483a483d7f2f6b53f781a158c12f7661a3923f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519755"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [CA1822: contrassegna i membri come statici](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static) su docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|MarkMethodsAsStatic|  
|CheckId|CA1822|  
|Category|Microsoft.Performance|  
|Modifica importante|Non sostanziale - Se il membro non è visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate. Non importante: se si modifica semplicemente il membro a un membro di istanza con il `this` (parola chiave).<br /><br /> Rilievo - se si modifica il membro da un membro di istanza a un membro statico ed è visibile all'esterno dell'assembly.|  
  
## <a name="cause"></a>Causa  
 Un membro che non accede ai dati dell'istanza non è contrassegnato come static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Descrizione della regola  
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Creazione di siti di chiamata non virtuali, si impedirà di un controllo in fase di esecuzione per ogni chiamata che accerti che il puntatore all'oggetto corrente è diverso da null. Si potrà così ottenere un miglioramento sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni. In alcuni casi, l'errore di accesso di istanza dell'oggetto corrente rappresenta un problema di correzione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Contrassegnare il membro come static (o condivisi [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) o utilizzare 'this' / 'Me' nel metodo body, se appropriato.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola per il codice fornito in precedenza per il quale la correzione sarebbe una modifica sostanziale.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)

