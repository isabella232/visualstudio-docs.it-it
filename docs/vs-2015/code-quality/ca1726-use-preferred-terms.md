---
title: 'CA1726: usare i termini preferiti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547810"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usare termini preferiti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1726: usare i termini preferiti](/visualstudio/code-quality/ca1726-use-preferred-terms).

|Elemento|valore|
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Category|Microsoft. Naming|
|Modifica importante|Interruzioni durante l'attivazione degli assembly<br /><br /> Senza interruzioni-quando viene attivato sui parametri di tipo|

## <a name="cause"></a>Causa
 Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito. In alternativa, il nome include il termine flag o flag.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola analizza un identificatore in token. Ogni singolo token e ogni combinazione di token doppi contigui viene confrontato con i termini incorporati nella regola e nella sezione deprecata di qualsiasi dizionario personalizzato. La tabella seguente illustra i termini incorporati nella regola e le alternative preferite.

|Termine obsoleto|Termine preferito|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` o `Flags`|Non esiste alcun termine di sostituzione. Non usare.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il termine con il termine alternativo preferito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se il nome dell'identificatore è intenzionale e si riferisce in modo specifico al termine originale anziché al termine preferito.

## <a name="related-rules"></a>Regole correlate
 [Avvisi di denominazione](../code-quality/naming-warnings.md)
