---
title: 'CA1806: non ignorare i risultati del metodo | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543871"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Non ignorare i risultati dei metodi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Questo avviso può essere dovuto a diversi motivi:

- Viene creato un nuovo oggetto che non viene mai usato.

- Un metodo che crea e restituisce una nuova stringa viene chiamato e la nuova stringa non viene mai usata.

- Metodo COM o P/Invoke che restituisce un codice HRESULT o un codice di errore che non viene mai usato. Descrizione della regola

  La creazione di oggetti non necessari e il Garbage Collection associato dell'oggetto inutilizzato diminuiscono le prestazioni.

  Le stringhe non sono modificabili e i metodi, ad esempio String. ToUpper, restituiscono una nuova istanza di una stringa anziché modificare l'istanza della stringa nel metodo chiamante.

  Ignorando HRESULT o il codice di errore può verificarsi un comportamento imprevisto in condizioni di errore o in condizioni di risorse insufficienti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se il metodo A crea una nuova istanza dell'oggetto B che non viene mai utilizzata, passare l'istanza come argomento a un altro metodo o assegnare l'istanza a una variabile. Se la creazione dell'oggetto non è necessaria, rimuoverla.-o-

 Se il metodo A chiama il metodo B, ma non usa la nuova istanza di stringa restituita dal metodo B. Passare l'istanza come argomento a un altro metodo, assegnare l'istanza a una variabile. Oppure rimuovere la chiamata se non è necessaria.

 -oppure-

 Se il metodo A chiama il metodo B, ma non usa HRESULT o codice di errore restituito dal metodo. Usare il risultato in un'istruzione condizionale, assegnare il risultato a una variabile oppure passarlo come argomento a un altro metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola, a meno che l'operazione di creazione dell'oggetto non riservi alcuno scopo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che ignora il risultato della chiamata a String. Trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione precedente assegnando il risultato di String. Trim alla variabile su cui è stato chiamato.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che non utilizza un oggetto che crea.

> [!NOTE]
> Questa violazione non può essere riprodotta in Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione precedente rimuovendo la creazione non necessaria di un oggetto.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che ignora il codice di errore restituito dal metodo nativo GetShortPathName.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione precedente controllando il codice di errore e generando un'eccezione quando la chiamata ha esito negativo.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]