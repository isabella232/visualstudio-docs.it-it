---
title: 'CA1301: Evitare tasti di scelta rapida duplicati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 04a6c105f2452392af5c7246508232df18385b5e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018384"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitare tasti di scelta rapida duplicati

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Estende un tipo <xref:System.Windows.Forms.Control?displayProperty=fullName> e contiene due o più controlli di primo livello che dispongono di chiavi di accesso identico che vengono archiviate in un file di risorse.

## <a name="rule-description"></a>Descrizione della regola

Una chiave di accesso, noto anche come un tasto di scelta rapida, consente l'accesso da tastiera a un controllo usando il **Alt** chiave. Quando più controlli presentano la stessa chiave di accesso, il comportamento della chiave di accesso non è ben definito. L'utente potrebbe non essere in grado di accedere al controllo desiderato usando la chiave di accesso e un controllo diverso da quello che serve potrebbe essere abilitato.

L'implementazione corrente di questa regola ignora le voci di menu. Tuttavia, le voci di menu nel sottomenu stesso non devono avere le chiavi di accesso identico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, definire le chiavi di accesso univoci per tutti i controlli.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un form minimo che contiene due controlli che dispongono di chiavi di accesso identico. Le chiavi vengono archiviate in un file di risorse, non viene visualizzato. Tuttavia, i relativi valori visualizzati in impostati come commento out `checkBox.Text` righe. Il comportamento dei tasti di scelta rapida duplicati può essere esaminato mediante lo scambio di `checkBox.Text` righe con le controparti impostate come commentate. Tuttavia, in questo caso, l'esempio non genererà un avviso in base alla regola.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)