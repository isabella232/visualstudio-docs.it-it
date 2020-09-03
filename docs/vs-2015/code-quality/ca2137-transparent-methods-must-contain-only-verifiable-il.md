---
title: 'CA2137: i metodi Transparent devono contenere solo IL verificabile | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6219acde1f62c946e08325f4764dc49dde461d2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546575"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: I metodi Transparent devono contenere solo IL verificabile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene codice non verificabile o restituisce un tipo tramite riferimento.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata sui tentativi tramite codice trasparente per la sicurezza per eseguire MSIL (Microsoft Intermediate Language) non verificabile. Tuttavia, la regola non contiene un verificatore di IL completo, ma usa invece regole euristiche per intercettare la maggior parte delle violazioni di verifica MSIL.

 Per essere certi che il codice contenga solo codice MSIL verificabile, eseguire [Peverify.exe (strumento PEVerify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) nell'assembly. Eseguire PEVerify con l'opzione **/Transparent** che limita l'output ai soli metodi Transparent non verificabili che potrebbero causare un errore. Se non si usa l'opzione/transparent, PEVerify verifica anche i metodi critici che possono contenere codice non verificabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo con <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo o oppure rimuovere il codice non verificabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Il metodo in questo esempio usa codice non verificabile e deve essere contrassegnato con l' <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> attributo o.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
