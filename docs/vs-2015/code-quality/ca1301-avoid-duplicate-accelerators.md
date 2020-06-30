---
title: 'CA1301: evitare acceleratori duplicati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 772c9bee3f43c42701bfa460c622f4a225ec59cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539178"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitare tasti di scelta rapida duplicati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo estende <xref:System.Windows.Forms.Control?displayProperty=fullName> e contiene due o più controlli di primo livello con chiavi di accesso identiche archiviate in un file di risorse.

## <a name="rule-description"></a>Descrizione della regola
 Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT. Quando più controlli presentano tasti di scelta duplicati, il comportamento del tasto di scelta non è ben definito. L'utente potrebbe non essere in grado di accedere al controllo previsto usando la chiave di accesso e un controllo diverso da quello che dovrebbe essere abilitato.

 L'implementazione corrente di questa regola ignora le voci di menu. Tuttavia, le voci di menu nello stesso sottomenu non devono avere chiavi di accesso identiche.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, definire chiavi di accesso univoche per tutti i controlli.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un form minimo contenente due controlli con chiavi di accesso identiche. Le chiavi vengono archiviate in un file di risorse, che non viene visualizzato; Tuttavia, i relativi valori vengono visualizzati nelle righe impostate come commento `checkBox.Text` . Il comportamento degli acceleratori duplicati può essere esaminato scambiando le `checkBox.Text` righe con le relative controparti commentate. Tuttavia, in questo caso, l'esempio non genererà un avviso dalla regola.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[Risorse nelle applicazioni desktop](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
