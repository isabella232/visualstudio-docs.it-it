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
ms.openlocfilehash: 394fafb0c9185a5e11ba759a5b873236956cf25b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652203"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizzare SafeHandle per incapsulare le risorse native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Il codice gestito USA <xref:System.IntPtr> per accedere alle risorse native.

## <a name="rule-description"></a>Descrizione della regola
 L'uso di `IntPtr` nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutti gli utilizzi di `IntPtr` devono essere esaminati per determinare se l'utilizzo di una tecnologia <xref:System.Runtime.InteropServices.SafeHandle> o una tecnologia simile è necessario al suo posto. Si verificheranno problemi se il `IntPtr` rappresenta una risorsa nativa, ad esempio la memoria, un handle di file o un socket, che il codice gestito è considerato proprietario. Se il codice gestito è proprietario della risorsa, deve anche rilasciare le risorse native associate, perché un errore a tale scopo provocherebbe perdite di risorse.

 In questi scenari, si verificano problemi di sicurezza o affidabilità anche se è consentito l'accesso multithread a `IntPtr` e viene fornito un modo per rilasciare la risorsa rappresentata da `IntPtr`. Questi problemi implicano il riciclo del valore `IntPtr` nella versione della risorsa, mentre l'uso simultaneo della risorsa viene eseguito in un altro thread. Ciò può causare race condition in cui un thread può leggere o scrivere dati associati alla risorsa non corretta. Se, ad esempio, il tipo archivia un handle del sistema operativo come `IntPtr` e consente agli utenti di chiamare sia **Close** che qualsiasi altro metodo che utilizza tale handle simultaneamente e senza un certo tipo di sincronizzazione, il codice presenta un problema di riciclo della maniglia.

 Questo problema di riciclo della gestione può causare il danneggiamento dei dati e, spesso, una vulnerabilità di sicurezza. `SafeHandle` e la relativa classe di pari livello <xref:System.Runtime.InteropServices.CriticalHandle> forniscono un meccanismo per incapsulare un handle nativo a una risorsa in modo che tali problemi di threading possano essere evitati. Inoltre, è possibile utilizzare `SafeHandle` e la relativa classe di pari livello `CriticalHandle` per altri problemi di threading, ad esempio, per controllare con attenzione la durata degli oggetti gestiti che contengono una copia dell'handle nativo sulle chiamate ai metodi nativi. In questa situazione è spesso possibile rimuovere le chiamate a `GC.KeepAlive`. Il sovraccarico delle prestazioni si verifica quando si utilizza `SafeHandle` e, a un livello inferiore, `CriticalHandle`, spesso può essere ridotto tramite un'attenta progettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Convertire l'utilizzo `IntPtr` in `SafeHandle` per gestire in modo sicuro l'accesso alle risorse native. Per esempi, vedere l'argomento di riferimento <xref:System.Runtime.InteropServices.SafeHandle>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non visualizzare questo avviso.

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable>
