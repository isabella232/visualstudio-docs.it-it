---
title: 'CA1822: Contrassegna i membri come statici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebbbbe01f1dd23dfc560e019133dacd3517b388
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253456"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni: se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata. Senza interruzioni: se si modifica semplicemente il membro in un membro di istanza con `this` la parola chiave.<br /><br /> Suddivisione: se si modifica il membro da un membro di istanza a un membro statico ed è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Un membro che non accede ai dati dell'istanza non è contrassegnato come static (Shared [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in).

## <a name="rule-description"></a>Descrizione della regola
I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. La creazione di siti di chiamata non virtuali impedirà un controllo in fase di esecuzione per ogni chiamata che verifica che il puntatore all'oggetto corrente sia diverso da null. Questo può ottenere un miglioramento delle prestazioni misurabile per il codice sensibile alle prestazioni. In alcuni casi, l'errore di accesso all'istanza dell'oggetto corrente rappresenta un problema di correttezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Contrassegnare il membro come statico (o condiviso [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in) o usare ' This '/' me ' nel corpo del metodo, se appropriato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola per il codice distribuito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

## <a name="related-rules"></a>Regole correlate
[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Rimuovi variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)