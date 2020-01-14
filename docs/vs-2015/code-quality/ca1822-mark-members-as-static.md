---
title: 'CA1822: contrassegna i membri come statici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce4aa6aef9c70d0d628603afa7a256c309f280d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917938"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [CA1822: contrassegna i membri come statici](/visualstudio/code-quality/ca1822-mark-members-as-static).

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Categoria|Microsoft.Performance|
|Modifica importante|Senza interruzioni: se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br /><br /> Senza interruzioni: se si modifica semplicemente il membro in un membro di istanza con la parola chiave `this`.<br /><br /> Suddivisione: se si modifica il membro da un membro di istanza a un membro statico ed è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un membro che non accede ai dati dell'istanza non è contrassegnato come static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Descrizione della regola
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. La creazione di siti di chiamata non virtuali impedisce la verifica in fase di esecuzione per ogni chiamata che verifica che il puntatore all'oggetto corrente sia diverso da null. Questo può ottenere un miglioramento delle prestazioni misurabile per il codice sensibile alle prestazioni. In alcuni casi, l'errore di accesso all'istanza dell'oggetto corrente rappresenta un problema di correttezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Contrassegnare il membro come statico (o condiviso in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) o usare ' This '/' me ' nel corpo del metodo, se appropriato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola per il codice distribuito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)
