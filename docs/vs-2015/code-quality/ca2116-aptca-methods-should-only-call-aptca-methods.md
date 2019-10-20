---
title: 'CA2116: i metodi APTCA devono chiamare solo metodi APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9de5178b585275ef410ad3179ba320b663536bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658688"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: I metodi APTCA devono chiamare solo metodi APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un assembly con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> chiama un metodo in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Per impostazione predefinita, i metodi pubblici o protetti negli assembly con nomi sicuri vengono protetti in modo implicito da [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) per l'attendibilità totale. solo i chiamanti completamente attendibili possono accedere a un assembly con nome sicuro. Gli assembly con nome sicuro contrassegnati con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) non dispongono di questa protezione. L'attributo Disabilita la richiesta di collegamento, rendendo l'assembly accessibile ai chiamanti privi di attendibilità totale, ad esempio il codice eseguito da una rete Intranet o Internet.

 Quando l'attributo APTCA è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile che si sia verificata una violazione della sicurezza. Se due metodi `M1` e `M2` soddisfano le condizioni seguenti, i chiamanti malintenzionati possono usare il metodo `M1` per ignorare la richiesta di collegamento di attendibilità totale implicita che protegge `M2`:

- `M1` è un metodo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

- `M1` chiama un metodo `M2` all'esterno dell'assembly di `M1`.

- l'assembly `M2` non dispone dell'attributo APTCA e, pertanto, non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.

  Un chiamante parzialmente attendibile `X` può chiamare il metodo `M1`, causando `M1` per chiamare `M2`. Poiché `M2` non dispone dell'attributo APTCA, il chiamante immediato (`M1`) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` ha attendibilità totale e pertanto soddisfa questa verifica. Il rischio per la sicurezza è dovuto al fatto che `X` non partecipa alla soddisfazione della richiesta di collegamento che protegge `M2` da chiamanti non attendibili. Pertanto, i metodi con l'attributo APTCA non devono chiamare metodi che non dispongono dell'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se l'attributo APCTA è obbligatorio, usare una richiesta per proteggere il metodo che chiama nell'assembly con attendibilità totale. Le autorizzazioni richieste dipenderanno dalle funzionalità esposte dal metodo. Se possibile, proteggere il metodo con una richiesta di attendibilità totale per assicurarsi che la funzionalità sottostante non venga esposta a chiamanti parzialmente attendibili. Se ciò non è possibile, selezionare un set di autorizzazioni che protegga efficacemente la funzionalità esposta. Per ulteriori informazioni sulle richieste, vedere la pagina relativa alle [richieste](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che la funzionalità esposta dal metodo non consenta direttamente o indirettamente ai chiamanti di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non dispone dell'attributo APTCA e non deve essere accessibile ai chiamanti parzialmente attendibili (rappresentati da `M2` nella discussione precedente).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Esempio
 Il secondo assembly è completamente attendibile e consente chiamanti parzialmente attendibili (rappresentati da `M1` nella discussione precedente).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione di test (rappresentata da `X` nella discussione precedente) è parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Questo esempio produce il seguente output:

 Richiesta **di attendibilità totale: la richiesta non è riuscita.** 
**ClassRequiringFullTrust. DoWork è stato chiamato.**
## <a name="related-rules"></a>Regole correlate
 [CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [per la codifica .NET Framework assembly richiamabili da codice parzialmente attendibile](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [usando le librerie del codice parzialmente attendibile](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [richieste](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [collegamento richieste](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) di [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
