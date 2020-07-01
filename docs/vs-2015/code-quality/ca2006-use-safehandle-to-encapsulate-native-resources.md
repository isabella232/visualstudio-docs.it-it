---
title: 'CA2006: utilizzare SafeHandle per incapsulare le risorse native | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521147"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Usare SafeHandle per incapsulare le risorse native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Il codice gestito USA <xref:System.IntPtr> per accedere alle risorse native.

## <a name="rule-description"></a>Descrizione della regola
 L'utilizzo di `IntPtr` nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutti gli utilizzi di `IntPtr` devono essere esaminati per determinare se l'utilizzo di una <xref:System.Runtime.InteropServices.SafeHandle> tecnologia o di una tecnologia simile è necessario al suo posto. Si verificheranno problemi se l'oggetto `IntPtr` rappresenta una risorsa nativa, ad esempio memoria, un handle di file o un socket, di cui il codice gestito è considerato proprietario. Se il codice gestito è proprietario della risorsa, deve anche rilasciare le risorse native associate, perché un errore a tale scopo provocherebbe perdite di risorse.

 In questi scenari, si verificano problemi di sicurezza o affidabilità anche se è consentito l'accesso multithread a `IntPtr` e viene fornito un modo per rilasciare la risorsa rappresentata da `IntPtr` . Questi problemi implicano il riciclo del `IntPtr` valore nella versione della risorsa, mentre l'uso simultaneo della risorsa viene eseguito in un altro thread. Ciò può causare race condition in cui un thread può leggere o scrivere dati associati alla risorsa non corretta. Se, ad esempio, il tipo archivia un handle del sistema operativo come `IntPtr` e consente agli utenti di chiamare sia **Close** che qualsiasi altro metodo che utilizza tale handle simultaneamente e senza un certo tipo di sincronizzazione, il codice presenta un problema di riciclo della maniglia.

 Questo problema di riciclo della gestione può causare il danneggiamento dei dati e, spesso, una vulnerabilità di sicurezza. `SafeHandle`e la classe di pari livello <xref:System.Runtime.InteropServices.CriticalHandle> forniscono un meccanismo per incapsulare un handle nativo a una risorsa in modo che tali problemi di threading possano essere evitati. Inoltre, è possibile utilizzare `SafeHandle` e la relativa classe di pari livello `CriticalHandle` per altri problemi di threading, ad esempio, per controllare con attenzione la durata degli oggetti gestiti che contengono una copia dell'handle nativo sulle chiamate ai metodi nativi. In questa situazione è spesso possibile rimuovere le chiamate a `GC.KeepAlive` . L'overhead di prestazioni che si verifica quando si usa `SafeHandle` e, a un livello inferiore, `CriticalHandle` può essere ridotto spesso con un'attenta progettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Convertire `IntPtr` l'utilizzo in `SafeHandle` per gestire in modo sicuro l'accesso alle risorse native. <xref:System.Runtime.InteropServices.SafeHandle>Per esempi, vedere l'argomento di riferimento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non visualizzare questo avviso.

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable>
