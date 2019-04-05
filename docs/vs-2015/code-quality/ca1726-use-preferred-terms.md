---
title: 'CA1726: Utilizzare termini preferiti | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001842"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usare termini preferiti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [CA1726: Utilizzare termini Preferiti](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) su docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Category|Microsoft.Naming|  
|Modifica importante|Rilievo - quando viene attivato su assembly<br /><br /> Non sostanziale - Quando viene attivato su parametri di tipo|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito. In alternativa, il nome include il termine contrassegni o Flag.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola analizza un identificatore in token. Ogni singolo token e ogni combinazione di token duale contigui viene confrontato con termini che vengono compilati nella regola e nella sezione dei dizionari personalizzati obsoleto. La tabella seguente illustra le condizioni che vengono compilate nella regola e le alternative preferite.  
  
|Termine obsoleto|Termine preferito|  
|-------------------|--------------------|  
|non sono|AreNot|  
|Annullato|Annullato|  
|Impossibile|Non è possibile|  
|ComPlus|EnterpriseServices|  
|Non è stato possibile|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag o flag|Non vi è alcun termine sostitutivo. Non usare.|  
|non veniva|HadNot|  
|Non è ancora|HasNot|  
|non hai|HaveNot|  
|Indici|Indexes|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|Disconnessione|  
|Wasnt|WasNot|  
|non sono stati|WereNot|  
|Non riuscita|WillNot|  
|Wouldnt|WouldNot|  
|Scrivibile|Scrivibile|  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il termine con il termine alternativo preferito.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Eliminare un avviso da questa regola solo se il nome dell'identificatore è intenzionale e riguarda in modo specifico per il termine originale anziché il termine preferito.  
  
## <a name="related-rules"></a>Regole correlate  
 [Avvisi di denominazione](../code-quality/naming-warnings.md)
