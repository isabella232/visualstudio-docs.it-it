---
title: 'CA1822: Contrassegna i membri come statici'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a566518d41a37e12ce20188bfe84c02a6cabcf9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890193"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale - Se il membro non è visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate. Non importante: se si modifica semplicemente il membro a un membro di istanza con il `this` (parola chiave).<br /><br /> Rilievo - se si modifica il membro da un membro di istanza a un membro statico ed è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un membro che non accede ai dati dell'istanza non è contrassegnato come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descrizione della regola
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Creazione di siti di chiamata non virtuali, si impedirà di un controllo in fase di esecuzione per ogni chiamata che accerti che il puntatore all'oggetto corrente è diverso da null. Si potrà così ottenere un miglioramento sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni. In alcuni casi, l'errore di accesso di istanza dell'oggetto corrente rappresenta un problema di correzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Contrassegnare il membro come static (o condivisi [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o utilizzare 'this' / 'Me' nel metodo body, se appropriato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola per il codice fornito in precedenza per il quale la correzione sarebbe una modifica sostanziale.

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)