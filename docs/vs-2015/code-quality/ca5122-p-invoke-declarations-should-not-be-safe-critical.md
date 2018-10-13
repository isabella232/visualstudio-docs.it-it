---
title: P-Invoke ca5122 le dichiarazioni non devono essere critici | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6a3b9dc87abf80b951aace8a5e4bea09d9da3944
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267826"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 Le dichiarazioni P/Invoke non devono essere SafeCritical
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una dichiarazione P/Invoke è stata contrassegnata con <xref:System.Security.SecuritySafeCriticalAttribute>:

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
   }

```

 In questo esempio, `C.Beep(...)` è stato contrassegnato come metodo critico per la sicurezza e richiamabile da codice trasparente.

## <a name="rule-description"></a>Descrizione della regola
 I metodi sono contrassegnati come SecuritySafeCritical quando viene eseguita un'operazione sensibile di sicurezza, ma possono anche essere utilizzati in sicurezza dal codice trasparente. Una delle regole di base del modello di trasparenza per la sicurezza è che il codice trasparente non può mai direttamente chiamare il codice nativo tramite P/Invoke. Di conseguenza, contrassegnare P/Invoke come critico per la sicurezza e richiamabile da codice trasparente non consentirà al codice trasparente di chiamarlo ed è fuorviante per l'analisi di sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per rendere P/Invoke disponibile al codice trasparente, esporre per esso un wrapper del metodo critico per la sicurezza e richiamabile da codice trasparente:

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}

```

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.



