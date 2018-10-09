---
title: 'CA2001: Evitare le chiamate a metodi problematici | Microsoft Docs'
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
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3a62259f0c0d4de701cba9619ba8a067926a99e6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47541176"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitare le chiamate a metodi problematici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2001: evitare chiamate a metodi problematici](https://docs.microsoft.com/visualstudio/code-quality/ca2001-avoid-calling-problematic-methods).

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro chiama un metodo potenzialmente pericoloso o problematico.

## <a name="rule-description"></a>Descrizione della regola
 Evitare di effettuare chiamate a metodi potenzialmente pericolosi e superflui.

 Una violazione di questa regola si verifica quando un membro chiama uno dei metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|La chiamata a GC. Raccogli possono influire in modo significativo le prestazioni dell'applicazione ed sono solo raramente necessario. Per altre informazioni, vedere la [Mariani Rico](http://go.microsoft.com/fwlink/?LinkId=169256) post di blog su MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e Resume sono state deprecate a causa del comportamento imprevedibile.  Usare altre classi nel <xref:System.Threading> dello spazio dei nomi, ad esempio <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, e <xref:System.Threading.Semaphore> per sincronizzare i thread o proteggere le risorse.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Il metodo DangerousGetHandle pone un rischio per la sicurezza in quanto può restituire un handle che non è valido. Vedere le <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> e il <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metodi per altre informazioni su come usare il metodo DangerousGetHandle in modo sicuro.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Questi metodi possono caricare assembly da posizioni non previste. Ad esempio, vedere i post di blog note di CLR .NET di Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [Choosing a Binding Context](http://go.microsoft.com/fwlink/?LinkId=164451) sul sito Web MSDN per informazioni sui metodi di caricamento degli assembly.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Una volta il codice utente avvia l'esecuzione di un processo gestito, è troppo tardi per chiamare in modo affidabile CoSetProxyBlanket. Common language runtime (CLR) esegue operazioni di inizializzazione che possono impedire successiva gli utenti di P/Invoke.<br /><br /> Se è necessario chiamare CoSetProxyBlanket per un'applicazione gestita, è consigliabile avviare il processo usando un file eseguibile di codice nativo (C++), chiamate CoSetProxyBlanket nel codice nativo e quindi avviare l'applicazione di codice gestito nel processo. (Assicurarsi di specificare un numero di versione di runtime.)|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere o sostituire la chiamata al metodo pericoloso o problematico.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È necessario eliminare i messaggi da questa regola solo quando nessun alternative al metodo problematico sono disponibili.

## <a name="see-also"></a>Vedere anche
 [Avvisi di affidabilità](../code-quality/reliability-warnings.md)


