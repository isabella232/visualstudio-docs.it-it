---
title: 'CA1060: Spostare i P-Invoke nella classe NativeMethods | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f47fa4326da9914171e5014decbd6d6923c2f02e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967784"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Spostare P/Invoke nella classe NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo viene utilizzato Platform Invocation Services per accedere al codice non gestito e non è un membro di uno dei **NativeMethods** classi.

## <a name="rule-description"></a>Descrizione della regola
 I metodi di chiamata al sistema operativo, ad esempio quelli contrassegnati utilizzando il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributi o i metodi che vengono definiti usando il `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], accedere a codice non gestito. Questi metodi dovrebbero essere in una delle classi seguenti:

- **NativeMethods** -questa classe non elimina i percorsi stack per l'autorizzazione al codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> non deve essere applicata a questa classe.) Questa classe è per i metodi che possono essere utilizzati ovunque, perché verrà eseguita un'analisi dello stack.

- **SafeNativeMethods** -questa classe Elimina percorsi stack per l'autorizzazione al codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicata a questa classe.) Questa classe è per i metodi che sono sicuri per tutti gli utenti da chiamare. Ai chiamanti di questi metodi non sono necessarie per eseguire una revisione completa della sicurezza per assicurarsi che l'utilizzo è sicuro perché i metodi sono innocui per qualsiasi chiamante.

- **UnsafeNativeMethods** -questa classe Elimina percorsi stack per l'autorizzazione al codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicata a questa classe.) Questa classe è per i metodi che sono potenzialmente pericolosi. Un chiamante qualsiasi di questi metodi è necessario eseguire una revisione completa della sicurezza per assicurarsi che l'utilizzo è sicuro perché non verrà eseguita alcuna analisi dello stack.

  Queste classi vengono dichiarate come `internal` (`Friend`, in Visual Basic) e si dichiara un costruttore privato per impedire la creazione di nuove istanze. I metodi delle classi devono essere `static` e `internal` (`Shared` e `Friend` in Visual Basic).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, spostare il metodo appropriato **NativeMethods** classe. Per la maggior parte delle applicazioni, lo spostamento di P/Invoke a una nuova classe denominata **NativeMethods** è sufficiente.

 Se si sviluppano librerie per l'uso in altre applicazioni, tuttavia, si consiglia di definire due altre classi che vengono chiamati **SafeNativeMethods** e **UnsafeNativeMethods**. Queste classi sono simili al **NativeMethods** classe; tuttavia, sono contrassegnati con un attributo speciale chiamato **SuppressUnmanagedCodeSecurityAttribute**. Quando viene applicato questo attributo, il runtime non esegue un percorso stack completo per assicurarsi che tutti i chiamanti abbiano il **UnmanagedCode** l'autorizzazione. Il runtime controlla in genere per questa autorizzazione all'avvio. Poiché il controllo non viene eseguito, è possibile migliorare notevolmente le prestazioni per le chiamate a questi metodi non gestiti, consente inoltre il codice che ha autorizzazioni limitate per chiamare questi metodi.

 Tuttavia, si deve utilizzare questo attributo con estrema attenzione. Se viene implementato in modo non corretto può avere implicazioni di sicurezza seri...

 Per informazioni su come implementare i metodi, vedere la **NativeMethods** esempio **SafeNativeMethods** esempio, e **UnsafeNativeMethods** esempio.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente dichiara un metodo che violano questa regola. Per correggere la violazione, il **RemoveDirectory** P/Invoke devono essere spostati in una classe appropriata che è progettata per contenere solo P/Invoke.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Esempio di NativeMethods

### <a name="description"></a>Descrizione
 Poiché il **NativeMethods** classe non deve essere contrassegnata utilizzando **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke che vengono inseriti in essa richiederà **UnmanagedCode** autorizzazione. Poiché la maggior parte delle applicazioni eseguite dal computer locale ed eseguiti con attendibilità totale, ciò non costituisce generalmente un problema. Se si sviluppano librerie riutilizzabili, tuttavia, si consiglia di definire un **SafeNativeMethods** oppure **UnsafeNativeMethods** classe.

 L'esempio seguente mostra un' **Interaction. Beep** metodo che esegue il wrapping il **MessageBeep** funzione da user32.dll. Il **MessageBeep** P/Invoke viene inserito **NativeMethods** classe.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Esempio di SafeNativeMethods

### <a name="description"></a>Descrizione
 I metodi P/Invoke, che possono essere esposti in modo sicuro a tutte le applicazioni e che non hanno effetti collaterali devono essere inseriti in una classe denominata **SafeNativeMethods**. Non è necessario richiedere autorizzazioni e non è necessario prestare molta attenzione in cui vengono chiamati da.

 L'esempio seguente mostra un' **Environment. TickCount** proprietà che esegue il wrapping il **GetTickCount** funzione da kernel32.dll.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Esempio di UnsafeNativeMethods

### <a name="description"></a>Descrizione
 I metodi P/Invoke che non può essere chiamato in modo sicuro e che potrebbe causare effetti collaterali devono essere inseriti in una classe denominata **UnsafeNativeMethods**. Questi metodi devono essere controllati rigorosamente per assicurarsi che non sono esposti all'utente involontariamente. La regola [CA2118: Esaminare la sintassi di SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) possono essere d'aiuto. In alternativa, è necessario un'altra autorizzazione richiesta anziché i metodi **UnmanagedCode** quando li usano.

 L'esempio seguente mostra una **Cursor. hide** metodo che esegue il wrapping il **ShowCursor** funzione da user32.dll.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)
