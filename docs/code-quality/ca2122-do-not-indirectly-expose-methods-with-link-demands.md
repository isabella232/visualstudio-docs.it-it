---
title: 'CA2122: Non esporre in modo indiretto metodi con richieste di collegamento | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 836fca663baaa5a5c62c720eac9f7408732f95d5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Non esporre in modo indiretto metodi con richieste di collegamento
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Category|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un membro pubblico o protetto presenta un [le richieste di collegamento](/dotnet/framework/misc/link-demands) e viene chiamato da un membro che non esegue alcun controllo della sicurezza.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato. Se un membro `X` non rende richieste di sicurezza dei relativi chiamanti e chiamate di codice protetto da una richiesta di collegamento, un chiamante senza l'autorizzazione necessaria è possibile utilizzare `X` per accedere al membro protetto.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Aggiungere una protezione [dati e modellazione](/dotnet/framework/data/index) o richiesta di collegamento per il membro in modo che non fornisca accesso non protetto non è più al membro protetto dalla richiesta di collegamento.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non concede i chiamanti accesso a operazioni o risorse che possono essere utilizzate in modo distruttivo.  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti mostrano una libreria che viola la regola e un'applicazione che illustra i punti deboli della libreria. La libreria di esempio fornisce due metodi che insieme violano la regola. Il `EnvironmentSetting` metodo è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente. Il `DomainInformation` metodo non effettua protezione richieste dai relativi chiamanti prima di chiamare `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Esempio  
 La seguente applicazione chiama il membro della libreria non protetto.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Questo esempio produce il seguente output:  
  
 **Valore da membro non protetto: Seattle**   
## <a name="see-also"></a>Vedere anche  
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)   
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)   
 [Dati e modellazione](/dotnet/framework/data/index)