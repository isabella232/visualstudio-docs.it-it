---
title: 'CA2109: Controllare i gestori di eventi visibili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88fbd5bbe873ae8bec9a506efbdb20d3fc77a2c1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232797"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Controllare i gestori di eventi visibili

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
È stato rilevato un metodo di gestione eventi pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
Un metodo di gestione degli eventi visibile esternamente presenta un problema di sicurezza che richiede la revisione.

Non esporre i metodi di gestione degli eventi a meno che non sia assolutamente necessario. Un gestore eventi, un tipo delegato, che richiama il metodo esposto, può essere aggiunto a qualsiasi evento purché le firme dell'evento e del gestore corrispondano. Gli eventi possono essere generati da qualsiasi codice e vengono spesso generati da codice di sistema altamente attendibile in risposta alle azioni dell'utente, ad esempio facendo clic su un pulsante. L'aggiunta di un controllo di sicurezza a un metodo di gestione degli eventi non impedisce al codice di registrare un gestore eventi che richiama il metodo.

Una richiesta non può proteggere in modo affidabile un metodo richiamato da un gestore eventi. Le richieste di sicurezza consentono di proteggere il codice da chiamanti non attendibili esaminando i chiamanti nello stack di chiamate. Il codice che aggiunge un gestore eventi a un evento non è necessariamente presente nello stack di chiamate quando vengono eseguiti i metodi del gestore eventi. Lo stack di chiamate potrebbe pertanto avere solo chiamanti altamente attendibili quando viene richiamato il metodo del gestore eventi. Ciò comporta la riuscita delle richieste effettuate dal metodo del gestore eventi. Inoltre, l'autorizzazione richiesta potrebbe essere dichiarata quando viene richiamato il metodo. Per questi motivi, il rischio di non correggere una violazione di questa regola può essere valutato solo dopo aver esaminato il metodo di gestione degli eventi. Quando si esamina il codice, considerare i problemi seguenti:

- Il gestore dell'evento esegue qualsiasi operazione pericolosa o sfruttabile, ad esempio l'asserzione delle autorizzazioni o l'eliminazione dell'autorizzazione per il codice non gestito?

- Quali sono le minacce per la sicurezza da e verso il codice perché può essere eseguito in qualsiasi momento con solo chiamanti altamente attendibili nello stack?

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, esaminare il metodo e valutare quanto segue:

- È possibile rendere il metodo di gestione degli eventi non pubblico?

- È possibile spostare tutte le funzionalità pericolose dal gestore eventi?

- Se viene imposta una richiesta di sicurezza, questa operazione può essere eseguita in altro modo?

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola solo dopo un'attenta revisione della sicurezza per assicurarsi che il codice non rappresenti una minaccia per la sicurezza.

## <a name="example"></a>Esempio
Il codice seguente illustra un metodo di gestione degli eventi che può essere usato in modo improprio dal codice dannoso.

[!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>