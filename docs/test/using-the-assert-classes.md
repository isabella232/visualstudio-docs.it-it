---
title: Classi e metodi Assert MSTest
description: Informazioni su come usare le istruzioni Assert per testare la correttezza del comportamento del codice durante una unit test del codice dell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 09edc60284a8ff4d26a670123427cbf3a3ae1385
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635467"
---
# <a name="use-assert-classes-for-unit-testing"></a>Usare classi Assert per il testing unità

Usare le classi Assert dello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> per verificare funzionalità specifiche. Un metodo di unit test verifica il codice di un metodo nel codice dell'applicazione, ma segnala la correttezza del comportamento del codice soltanto se sono incluse istruzioni Assert.

## <a name="kinds-of-asserts"></a>Tipi di classi Assert

Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> rende disponibili diversi tipi di classi Assert.

Nel metodo di test è possibile chiamare tutti i metodi della classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>, ad esempio <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> offre numerosi metodi tra cui scegliere e molti dei metodi presentano vari overload.

### <a name="compare-strings-and-collections"></a>Confrontare stringhe e raccolte

Usare la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> per confrontare raccolte di oggetti o verificare lo stato di una raccolta.

Usare la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> per confrontare ed esaminare le stringhe. Questa classe contiene numerosi metodi utili, ad esempio <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> e <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Eccezioni

L'eccezione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> viene generata ogni volta che un test ha esito negativo. Un test ha esito negativo se raggiunge il timeout, genera un'eccezione imprevista o contiene un'istruzione Assert che produce un risultato **Non superato**.

L'eccezione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> viene generata ogni volta che un test produce un risultato **Senza risultati**. In genere, un'istruzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> viene aggiunta a un test su cui si sta lavorando per indicare che non è ancora pronto per l'esecuzione.

> [!NOTE]
> Una strategia alternativa è contrassegnare un test che non è pronto per l'esecuzione usando l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>. Questa strategia ha però lo svantaggio di non poter consentire la semplice generazione di un report sul numero di test rimasti da implementare.

Se si scrive una nuova classe di eccezione Assert, ereditare la classe di base <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> in modo da semplificare l'identificazione dell'eccezione come errore di asserzione, anziché come eccezione imprevista generata dal codice di test o di produzione.

Per verificare che un'eccezione di cui è prevista la generazione da parte di un metodo nel codice dell'applicazione sia effettivamente generata, usare il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
