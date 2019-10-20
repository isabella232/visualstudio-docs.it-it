---
title: 'CA1060: spostare P-Invoke nella classe NativeMethods | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49a693224b6552340d2a01051318842749a84cc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663673"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Spostare i P/Invoke nella classe NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo usa i servizi di chiamata della piattaforma per accedere al codice non gestito e non è un membro di una delle classi **NativeMethods** .

## <a name="rule-description"></a>Descrizione della regola
 I metodi di chiamata della piattaforma, ad esempio quelli contrassegnati con l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>, o i metodi definiti usando la parola chiave `Declare` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], accedono al codice non gestito. Questi metodi devono essere in una delle classi seguenti:

- **NativeMethods** : questa classe non consente l'eliminazione di percorsi stack per l'autorizzazione per il codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> non deve essere applicato a questa classe). Questa classe è destinata a metodi che possono essere usati ovunque perché verrà eseguito un percorso stack.

- **SafeNativeMethods** : questa classe disattiva i percorsi dello stack per l'autorizzazione del codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe). Questa classe è destinata a metodi sicuri per chiunque chiami. I chiamanti di questi metodi non devono eseguire una revisione completa della sicurezza per assicurarsi che l'utilizzo sia sicuro perché i metodi sono innocui per qualsiasi chiamante.

- **UnsafeNativeMethods** : questa classe disattiva i percorsi dello stack per l'autorizzazione del codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe). Questa classe è destinata a metodi potenzialmente pericolosi. Qualsiasi chiamante di questi metodi deve eseguire una revisione completa della sicurezza per assicurarsi che l'utilizzo sia sicuro perché non verrà eseguito alcun percorso stack.

  Queste classi vengono dichiarate come `internal` (`Friend`, in Visual Basic) e dichiarano un costruttore privato per impedire la creazione di nuove istanze. I metodi di queste classi devono essere `static` e `internal` (`Shared` e `Friend` in Visual Basic).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, spostare il metodo nella classe **NativeMethods** appropriata. Per la maggior parte delle applicazioni, lo stato di P/Invoke viene spostato in una nuova classe denominata **NativeMethods** .

 Tuttavia, se si sviluppano librerie da utilizzare in altre applicazioni, è consigliabile definire altre due classi denominate **SafeNativeMethods** e **UnsafeNativeMethods**. Queste classi sono simili alla classe **NativeMethods** . Tuttavia, vengono contrassegnati con un attributo speciale denominato **SuppressUnmanagedCodeSecurityAttribute**. Quando viene applicato questo attributo, il runtime non esegue un percorso stack completo per assicurarsi che tutti i chiamanti dispongano dell'autorizzazione **UnmanagedCode** . Il runtime verifica in genere l'autorizzazione all'avvio. Poiché il controllo non viene eseguito, può migliorare significativamente le prestazioni per le chiamate a questi metodi non gestiti, ma consente anche il codice con autorizzazioni limitate per chiamare questi metodi.

 Tuttavia, è consigliabile usare questo attributo con particolare attenzione. Se è implementata in modo errato, può presentare gravi implicazioni sulla sicurezza.

 Per informazioni sull'implementazione dei metodi, vedere l'esempio **NativeMethods** , esempio **SafeNativeMethods** e **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene dichiarato un metodo che viola questa regola. Per correggere la violazione, il **RemoveDirectory** p/Invoke deve essere spostato in una classe appropriata progettata per contenere solo P/Invoke.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Esempio di NativeMethods

### <a name="description"></a>Descrizione
 Poiché la classe **NativeMethods** non deve essere contrassegnata con **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke che vengono inseriti in tale classe richiede l'autorizzazione **UnmanagedCode** . Poiché la maggior parte delle applicazioni viene eseguita dal computer locale e viene eseguita insieme a attendibilità totale, non si tratta in genere di un problema. Tuttavia, se si sviluppano librerie riutilizzabili, è consigliabile definire una classe **SafeNativeMethods** o **UnsafeNativeMethods** .

 Nell'esempio seguente viene illustrato un metodo **Interaction. Beep** che esegue il wrapping della funzione **MessageBeep** da User32. dll. Il **MessageBeep** P/Invoke viene inserito nella classe **NativeMethods** .

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Esempio di SafeNativeMethods

### <a name="description"></a>Descrizione
 I metodi P/Invoke che possono essere esposti in modo sicuro a qualsiasi applicazione e che non hanno effetti collaterali devono essere inseriti in una classe denominata **SafeNativeMethods**. Non è necessario richiedere le autorizzazioni e non è necessario prestare molta attenzione al punto in cui vengono chiamate.

 Nell'esempio seguente viene illustrata una proprietà **Environment. TickCount** che esegue il wrapping della funzione **GetTickCount** da Kernel32. dll.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Esempio di UnsafeNativeMethods

### <a name="description"></a>Descrizione
 I metodi P/Invoke che non possono essere chiamati in modo sicuro e che potrebbero causare effetti collaterali devono essere inseriti in una classe denominata **UnsafeNativeMethods**. Questi metodi devono essere controllati rigorosamente per assicurarsi che non siano esposti all'utente involontariamente. La regola [CA2118: esaminare l'utilizzo di SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) può essere utile per questa operazione. In alternativa, i metodi devono avere un'altra autorizzazione richiesta anziché **UnmanagedCode** quando li usano.

 Nell'esempio seguente viene illustrato un metodo **Cursor. Hide** che esegue il wrapping della funzione **ShowCursor** da User32. dll.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)
