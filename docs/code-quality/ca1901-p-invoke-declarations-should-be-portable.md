---
title: 'CA1901: Le dichiarazioni P/Invoke devono essere portabili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d878572c4391805773a9a711ee88e7b58f507c65
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233300"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Le dichiarazioni P/Invoke devono essere portabili

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft. portabilità|
|Modifica|Interruzioni: se il P/Invoke è visibile all'esterno dell'assembly. Senza interruzioni: se il P/Invoke non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Questa regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che le relative dimensioni, quando viene eseguito il marshalling a codice non gestito su piattaforme a 32 e 64 bit, siano corrette. La violazione più comune di questa regola consiste nel passare un valore integer a dimensione fissa in cui è richiesta una variabile di tipo puntatore dipendente dalla piattaforma.

## <a name="rule-description"></a>Descrizione della regola
Uno degli scenari seguenti viola questa regola:

- Il valore restituito o il parametro viene tipizzato come intero a dimensione fissa quando deve essere digitato `IntPtr`come.

- Il valore restituito o il parametro viene tipizzato `IntPtr` come un oggetto quando deve essere digitato come Integer a dimensione fissa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
È possibile correggere questa violazione `IntPtr` utilizzando o `UIntPtr` `Int32` per rappresentare gli handle anziché o `UInt32`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non visualizzare questo avviso.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata una violazione di questa regola.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

In questo esempio, il `nIconIndex` parametro viene dichiarato come un `IntPtr`, che ha una larghezza di 4 byte in una piattaforma a 32 bit e 8 byte in una piattaforma a 64 bit. Nella dichiarazione non gestita riportata di seguito è possibile vedere che `nIconIndex` si tratta di un Unsigned Integer a 4 byte in tutte le piattaforme.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Esempio
Per correggere la violazione, modificare la dichiarazione nel modo seguente:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Vedere anche
[Portability Warnings](../code-quality/portability-warnings.md)