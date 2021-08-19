---
title: API del test delle prestazioni Web
description: Informazioni sull'API test prestazioni Web, che supporta test delle prestazioni Web codificati, plug-in di test, plug-in di richiesta, richieste e regole di estrazione/convalida.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: ba9eccbfba9bd965969f426714eab51289c7e1fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139959"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Procedura: Usare l'API del test delle prestazioni Web

È possibile scrivere codice per i test Web. L'API del test delle prestazioni Web viene usata per creare test Web codificati, plug-in test Web, plug-in richiesta, richieste, regole di estrazione e regole di convalida. Le classi che compongono queste tipologie sono le classi di base in questa API. Gli altri tipi in questa API vengono utilizzati per supportare la creazione degli oggetti <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting> consente di creare test delle prestazioni Web personalizzati.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

È anche possibile usare l'API del test Web per creare e salvare test Web dichiarativi a livello di codice. A tale scopo, utilizzare le classi <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> Il visualizzatore oggetti consente di esaminare lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting>. Gli editor Visual C# e Visual Basic forniscono il supporto IntelliSense per la codifica delle classi nello spazio dei nomi.

È possibile creare anche plug-in per i test di carico. Per altre informazioni, vedere [Procedura: Usare l'API del test di carico](../test/how-to-use-the-load-test-api.md) e [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Per utilizzare lo spazio dei nomi WebTesting

1. Aprire un progetto di test di carico e prestazioni web che contenga un test delle prestazioni web.

2. Aggiungere un progetto Libreria di classi Visual C# o Visual Basic alla soluzione di test.

3. Aggiungere un riferimento al progetto di libreria di classi nel progetto di test di carico e prestazioni Web.

4. Aggiungere un riferimento alla DLL Microsoft.VisualStudio.QualityTools.WebTestFramework nel progetto di libreria di classi.

5. Nel file della classe contenuto nel progetto Libreria di classi aggiungere un'istruzione `using` per lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Compilare il progetto.

8. Aggiungere un nuovo plug-in del test delle prestazioni Web usando l'Editor test prestazioni Web:

    1. Scegliere **Aggiungi plug-in test Web** nella barra degli strumenti.

         Viene visualizzata la finestra di dialogo **Aggiungi plug-in test Web**.

    2. In **Selezionare un plug-in** selezionare la classe plug-in del test delle prestazioni Web.

    3. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

        > [!NOTE]
        > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni Web in un secondo momento usando la finestra Proprietà.

    4. Scegliere **OK**.

9. Eseguire il test delle prestazioni Web.

     Per un esempio di implementazione di <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, vedere [Procedura: Creare un plug-in di test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Usare l'API del test di carico](../test/how-to-use-the-load-test-api.md)
- [Procedura: Creare un plug-in di test delle prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md)
