---
title: 'CA1806: Non ignorare i risultati dei metodi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 117e26fca367c8cf00604bebe01a00f4df58a0ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437390"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Non ignorare i risultati dei metodi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Category|Microsoft.Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Esistono diversi motivi possibili per questo avviso:  
  
- Un nuovo oggetto viene creato ma mai usato.  
  
- Viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai usata.  
  
- Un metodo COM o P/Invoke che restituisce un codice di errore o HRESULT che non viene mai usato. Descrizione della regola  
  
  La creazione di oggetti non necessari e la garbage collection associata dell'oggetto inutilizzato influiscono negativamente sulle prestazioni.  
  
  Le stringhe sono modificabili e metodi, ad esempio String. ToUpper restituisce una nuova istanza di una stringa invece di modificare l'istanza della stringa nel metodo chiamante.  
  
  Ignorando HRESULT o codice di errore può causare un comportamento imprevisto in condizioni di errore o alle condizioni di risorse insufficienti.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Se il metodo crea una nuova istanza dell'oggetto B che non viene mai usato, passare l'istanza come argomento a un altro metodo oppure assegnare l'istanza a una variabile. Se la creazione dell'oggetto non è necessaria, rimuoverla- o -  
  
 Se il metodo chiama il metodo B, ma non usa la nuova istanza di stringa restituita dal metodo B. Passare l'istanza come argomento a un altro metodo, assegnare l'istanza a una variabile. Oppure rimuovere la chiamata se non è necessaria.  
  
 -oppure-  
  
 Se il metodo chiama il metodo B, ma non usa il valore HRESULT o codice di errore che il metodo restituisce. Usare il risultato in un'istruzione condizionale, assegnare il risultato a una variabile oppure passarlo come argomento a un altro metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola, a meno che l'atto di creare l'oggetto viene usato per scopi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una classe che ignora il risultato della chiamata String. Trim.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di correggere la violazione precedente assegnando il risultato di String. Trim nella variabile di che cui è stato chiamato.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che non usa un oggetto creato.  
  
> [!NOTE]
> Questa violazione non può essere riprodotta in Visual Basic.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di correggere la violazione precedente rimuovendo la creazione di un oggetto non necessaria.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che consente di ignorare il codice di errore restituito dal metodo GetShortPathName nativo.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di correggere la violazione precedente controllando il codice di errore e generando un'eccezione quando la chiamata ha esito negativo.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]