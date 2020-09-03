---
title: 'CA1901: le dichiarazioni P-Invoke devono essere portabili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e669d87ad5ecc53c1523db16ab77578c6a703a33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545262"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Le dichiarazioni P/Invoke devono essere portabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft. portabilità|
|Modifica importante|Interruzioni: se il P/Invoke è visibile all'esterno dell'assembly. Senza interruzioni: se il P/Invoke non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Questa regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che le relative dimensioni, quando viene eseguito il marshalling a codice non gestito su piattaforme a 32 e 64 bit, siano corrette. La violazione più comune di questa regola consiste nel passare un valore integer a dimensione fissa in cui è richiesta una variabile di tipo puntatore dipendente dalla piattaforma.

## <a name="rule-description"></a>Descrizione della regola
 Uno degli scenari seguenti viola questa regola:

- Il valore restituito o il parametro viene tipizzato come intero a dimensione fissa quando deve essere digitato come `IntPtr` .

- Il valore restituito o il parametro viene tipizzato come un oggetto `IntPtr` quando deve essere digitato come Integer a dimensione fissa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È possibile correggere questa violazione utilizzando `IntPtr` o `UIntPtr` per rappresentare gli handle anziché `Int32` o `UInt32` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
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

 In questo esempio, il `nIconIndex` parametro viene dichiarato come un `IntPtr` , che ha una larghezza di 4 byte in una piattaforma a 32 bit e 8 byte in una piattaforma a 64 bit. Nella dichiarazione non gestita riportata di seguito è possibile vedere che `nIconIndex` si tratta di un Unsigned Integer a 4 byte in tutte le piattaforme.

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
 [Avvisi di portabilità](../code-quality/portability-warnings.md)
