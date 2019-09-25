---
title: 'CA2001: Evitare le chiamate a metodi problematici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233185"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitare le chiamate a metodi problematici

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Category|Microsoft.Reliability|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un membro chiama un metodo potenzialmente pericoloso o problematico.

## <a name="rule-description"></a>Descrizione della regola

Evitare di effettuare chiamate a metodi non necessarie e potenzialmente pericolose. Una violazione di questa regola si verifica quando un membro chiama uno dei metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Chiamata a GC. Collect può influire in modo significativo sulle prestazioni dell'applicazione ed è raramente necessario. Per ulteriori informazioni, vedere la voce del Blog relativo alle [prestazioni di Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) in MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e thread. Resume sono stati deprecati a causa del comportamento imprevedibile.  Usare altre classi <xref:System.Threading> nello spazio dei nomi, <xref:System.Threading.Monitor>ad esempio <xref:System.Threading.Mutex>, e <xref:System.Threading.Semaphore>, per sincronizzare i thread o proteggere le risorse.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Il metodo DangerousGetHandle rappresenta un rischio per la sicurezza perché può restituire un handle non valido. Per ulteriori <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> informazioni su <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> come utilizzare il metodo DangerousGetHandle in modo sicuro, vedere i metodi e.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Questi metodi possono caricare assembly da posizioni impreviste. Vedere, ad esempio, i post [di Blog sulle note CLR .NET di Suzanne Cook LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [scelta di un contesto di associazione](http://go.microsoft.com/fwlink/?LinkId=164451) per informazioni sui metodi che caricano assembly.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) Ole32<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32|Quando il codice utente inizia l'esecuzione in un processo gestito, è troppo tardi per chiamare in modo affidabile CoSetProxyBlanket. Il Common Language Runtime (CLR) esegue le azioni di inizializzazione che potrebbero impedire la riuscita del P/Invoke degli utenti.<br /><br /> Se è necessario chiamare CoSetProxyBlanket per un'applicazione gestita, è consigliabile avviare il processo usando un eseguibile di codice nativo (C++), chiamare CoSetProxyBlanket nel codice nativo, quindi avviare l'applicazione di codice gestito in corso. Assicurarsi di specificare un numero di versione di Runtime.|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere o sostituire la chiamata al metodo pericoloso o problematico.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È necessario eliminare i messaggi da questa regola solo quando non sono disponibili alternative al metodo problematico.

## <a name="see-also"></a>Vedere anche

- [Avvisi di affidabilità](../code-quality/reliability-warnings.md)