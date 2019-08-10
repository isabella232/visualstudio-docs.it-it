---
title: 'CA1301: Evitare tasti di scelta rapida duplicati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16cd44f00db13027d737b6a6b496877075ac6fa9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922268"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitare tasti di scelta rapida duplicati

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo estende <xref:System.Windows.Forms.Control?displayProperty=fullName> e contiene due o più controlli di primo livello con chiavi di accesso identiche archiviate in un file di risorse.

## <a name="rule-description"></a>Descrizione della regola

Una chiave di accesso, nota anche come acceleratore, consente l'accesso da tastiera a un controllo tramite il tasto **ALT** . Quando più controlli hanno la stessa chiave di accesso, il comportamento della chiave di accesso non è ben definito. L'utente potrebbe non essere in grado di accedere al controllo previsto usando la chiave di accesso e un controllo diverso da quello previsto potrebbe essere abilitato.

L'implementazione corrente di questa regola ignora le voci di menu. Tuttavia, le voci di menu nello stesso sottomenu non devono avere chiavi di accesso identiche.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, definire chiavi di accesso univoche per tutti i controlli.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un form minimo contenente due controlli con chiavi di accesso identiche. Le chiavi vengono archiviate in un file di risorse, che non viene visualizzato. Tuttavia, i relativi valori vengono visualizzati nelle `checkBox.Text` righe impostate come commento. Il comportamento degli acceleratori duplicati può essere esaminato scambiando le `checkBox.Text` righe con le relative controparti commentate. Tuttavia, in questo caso, l'esempio non genererà un avviso dalla regola.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)