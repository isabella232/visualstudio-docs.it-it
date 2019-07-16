---
title: 'CA2151: I campi con tipi critici devono essere SecurityCritical | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6c707efcc4c945e80ea0206cc5f30a647e83d231
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142581"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: I campi con tipi critici devono essere critici per la sicurezza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo trasparente per la sicurezza o un campo critico sicuro è dichiarato. Il tipo è specificato come critico per la sicurezza. Ad esempio:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

 In questo esempio, `m_field` è un campo trasparente per la sicurezza di un tipo che è critico per la sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Per usare i tipi critici per la sicurezza, il codice che fa riferimento al tipo deve essere critico per la sicurezza critico per la sicurezza e richiamabile da codice trasparente. Questo vale anche se il riferimento è indiretto. Ad esempio, quando si fa riferimento a un campo trasparente che dispone di un tipo critico, il codice deve essere critico per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente. Pertanto, un campo trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente è fuorviante perché il codice trasparente non potrà comunque accedere al campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la violazione di questa regola, contrassegnare il campo con l'attributo <xref:System.Security.SecurityCriticalAttribute> oppure rendere il tipo a cui il campo fa riferimento trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Commenti
