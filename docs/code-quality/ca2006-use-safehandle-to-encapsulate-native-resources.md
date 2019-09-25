---
title: 'CA2006: Usare SafeHandle per incapsulare le risorse native'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233094"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Usare SafeHandle per incapsulare le risorse native

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Il codice gestito <xref:System.IntPtr> USA per accedere alle risorse native.

## <a name="rule-description"></a>Descrizione della regola

L'utilizzo `IntPtr` di nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutti gli utilizzi `IntPtr` di devono essere esaminati per determinare se l'utilizzo <xref:System.Runtime.InteropServices.SafeHandle> di una tecnologia o di una tecnologia simile è necessario al suo posto. Si verificheranno problemi se `IntPtr` l'oggetto rappresenta una risorsa nativa, ad esempio memoria, un handle di file o un socket, di cui il codice gestito è considerato proprietario. Se il codice gestito è proprietario della risorsa, deve anche rilasciare le risorse native associate, perché un errore a tale scopo provocherebbe perdite di risorse.

In questi scenari, si verificano problemi di sicurezza o affidabilità anche se è consentito l'accesso multithread a `IntPtr` e viene fornito un modo per rilasciare la risorsa rappresentata `IntPtr` da. Questi problemi implicano il `IntPtr` riciclo del valore nella versione della risorsa, mentre l'uso simultaneo della risorsa viene eseguito in un altro thread. Ciò può causare race condition in cui un thread può leggere o scrivere dati associati alla risorsa non corretta. Se, ad esempio, il tipo archivia un handle del sistema `IntPtr` operativo come e consente agli utenti di chiamare sia **Close** che qualsiasi altro metodo che utilizza tale handle simultaneamente e senza un certo tipo di sincronizzazione, il codice presenta un problema di riciclo della maniglia.

Questo problema di riciclo della gestione può causare il danneggiamento dei dati e, spesso, una vulnerabilità di sicurezza. `SafeHandle`e la classe <xref:System.Runtime.InteropServices.CriticalHandle> di pari livello forniscono un meccanismo per incapsulare un handle nativo a una risorsa in modo che tali problemi di threading possano essere evitati. Inoltre, è possibile utilizzare `SafeHandle` e la relativa classe `CriticalHandle` di pari livello per altri problemi di threading, ad esempio, per controllare con attenzione la durata degli oggetti gestiti che contengono una copia dell'handle nativo sulle chiamate ai metodi nativi. In questa situazione è spesso possibile rimuovere le chiamate a `GC.KeepAlive`. Il sovraccarico delle prestazioni che si verifica quando si `SafeHandle` utilizza e, a un livello inferiore, `CriticalHandle`può essere spesso ridotto tramite un'attenta progettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Convertire `IntPtr` l'utilizzo `SafeHandle` in per gestire in modo sicuro l'accesso alle risorse native. Per esempi <xref:System.Runtime.InteropServices.SafeHandle> , vedere l'articolo di riferimento.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non visualizzare questo avviso.

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable>