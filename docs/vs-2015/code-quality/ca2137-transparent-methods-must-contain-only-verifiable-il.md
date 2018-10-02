---
title: 'CA2137: I metodi Transparent devono contenere solo IL verificabile | Microsoft Docs'
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
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 77ff02a0db733c3151f4faccd00e07518d61e600
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589141"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: I metodi Transparent devono contenere solo IL verificabile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2137: i metodi Transparent devono contenere solo IL verificabile](https://docs.microsoft.com/visualstudio/code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il).

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene codice non verificabile o restituisce un tipo tramite riferimento.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata sui tentativi tramite codice trasparente per la sicurezza per eseguire MSIL (Microsoft Intermediate Language) non verificabile. Tuttavia, la regola non contiene un verificatore di IL completo, ma usa invece regole euristiche per intercettare la maggior parte delle violazioni di verifica MSIL.

 Per essere certi che il codice contiene codice MSIL verificabile solo, eseguire [Peverify.exe (strumento PEVerify)](http://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) sull'assembly. Esecuzione di PEVerify con il **/ trasparente** opzione che limita l'output da solo non verificabili metodi trasparenti di cui verrebbe generato un errore. Se il / opzione trasparente non viene utilizzata, PEVerify verifica inoltre metodi critici che possono contenere codice non verificabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> o attributo, oppure rimuovere il codice non verificabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Il metodo in questo esempio Usa il codice non verificabile e devono essere contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]



