---
title: 'CA2006: Usare SafeHandle per incapsulare le risorse native | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcf385263eba5a6012097f43b49e7a75166bad42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154408"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Usare SafeHandle per incapsulare le risorse native
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Il codice gestito utilizza <xref:System.IntPtr> per accedere alle risorse native.

## <a name="rule-description"></a>Descrizione della regola
 Uso di `IntPtr` nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze dei `IntPtr` devono essere esaminate per determinare se l'uso di un <xref:System.Runtime.InteropServices.SafeHandle> , o una tecnologia simile, è necessario al suo posto. Se si verificheranno problemi di `IntPtr` rappresenta una risorsa nativa, ad esempio memoria, un handle di file o un socket, che il codice gestito viene considerato come proprietario. Se il codice gestito è il proprietario della risorsa, è necessario rilasciare anche le risorse native associate, in quanto un tentativo di eseguire questa operazione potrebbe causare perdite di risorse.

 In questi scenari, i problemi di sicurezza o di affidabilità saranno disponibile anche se è consentito l'accesso a thread multipli per il `IntPtr` e un modo per rilasciare la risorsa rappresentata dalla `IntPtr` viene fornito. Questi problemi riguardano il riciclo del `IntPtr` valore sul rilascio di risorse durante l'utilizzo simultaneo di risorsa è stata effettuata in un altro thread. Ciò può causare una race condition in cui un thread possa leggere o scrivere dati associata alla risorsa errata. Ad esempio, se il tipo archivia un handle del sistema operativo come una `IntPtr` e consente agli utenti di chiamare entrambe **Chiudi** e qualsiasi altro metodo che usa tale handle e simultaneamente senza alcun tipo di sincronizzazione, il codice ha un riciclo c'è problema.

 Questo problema di riciclo può causare il danneggiamento dei dati e, spesso una vulnerabilità di sicurezza. `SafeHandle` e la relativa classe di elemento di pari livello <xref:System.Runtime.InteropServices.CriticalHandle> forniscono un meccanismo per incapsulare un handle nativo di una risorsa in modo che tali problemi di threading possono essere evitati. Inoltre, è possibile usare `SafeHandle` e la relativa classe di elemento di pari livello `CriticalHandle` per altri problemi di threading, ad esempio, per controllare con attenzione la durata degli oggetti gestiti che contengono una copia dell'handle nativo nelle chiamate ai metodi nativi. In questo caso, è spesso possibile evitare chiamate a `GC.KeepAlive`. Il sovraccarico delle prestazioni che si verifica quando si usa `SafeHandle` e, a un livello inferiore, `CriticalHandle`, spesso può essere ridotto tramite un'attenta progettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Convertire `IntPtr` tra l'utilizzo di `SafeHandle` per gestire in modo sicuro l'accesso alle risorse native. Vedere il <xref:System.Runtime.InteropServices.SafeHandle> argomento di riferimento per gli esempi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non si deve eliminare l'avviso.

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable>
