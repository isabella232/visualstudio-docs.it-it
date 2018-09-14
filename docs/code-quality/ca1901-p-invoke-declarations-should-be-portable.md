---
title: 'CA1901: Le dichiarazioni P-Invoke devono essere portabili'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58a7df06d3707e0ed8c9bed9a04b79c3ea99dd04
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550635"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Le dichiarazioni P/Invoke devono essere portabili
|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft.Portability|
|Modifica importante|Rilievo - se i P/Invoke è visibile all'esterno dell'assembly. Non importante: se i P/Invoke non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Questa regola restituisce le dimensioni di ogni parametro e il valore restituito di P/Invoke e verifica che la dimensione, durante il marshalling nel codice non gestito nelle piattaforme a 32 e 64 bit, sia corretta. La violazione di questa regola più comune consiste nel passare un numero intero a dimensione fissa in cui è necessaria una variabile dipendente dalla piattaforma, della dimensione del puntatore.

## <a name="rule-description"></a>Descrizione della regola
 Uno dei seguenti scenari viola questa regola si verifica:

- Il valore restituito o parametro è tipizzato come un intero di dimensioni fisse quando deve essere digitato come un `IntPtr`.

- Il valore restituito o parametro è tipizzato come un `IntPtr` quando deve essere digitato come intero a dimensione fissa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È possibile correggere questa violazione utilizzando `IntPtr` oppure `UIntPtr` per rappresentare gli handle anziché `Int32` o `UInt32`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non si deve eliminare l'avviso.

## <a name="example"></a>Esempio
 L'esempio seguente illustra una violazione della regola.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 In questo esempio, il `nIconIndex` parametro viene dichiarato come un `IntPtr`, ovvero larghezza su una piattaforma a 32 bit e 8 byte in una piattaforma a 64 bit di 4 byte. Nella dichiarazione di non gestita che segue, è possibile osservare che `nIconIndex` è un intero senza segno a 4 byte in tutte le piattaforme.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Esempio
 Per correggere la violazione, modificare la dichiarazione per il seguente:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Vedere anche
 [Portability Warnings](../code-quality/portability-warnings.md)