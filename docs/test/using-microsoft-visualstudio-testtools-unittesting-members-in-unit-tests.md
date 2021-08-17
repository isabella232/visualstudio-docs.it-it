---
title: Usare MSTest negli unit test
description: Informazioni sul framework MSTest, che supporta gli unit test in Visual Studio. Usare queste classi e membri per codificare unit test.
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c73edda39e77b0744eec6abb494ee93ba592f5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092228"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Usare il framework MSTest negli unit test

Il framework [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) supporta unit test in Visual Studio. Usare le classi e membri nello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> durante la codifica di unit test. È possibile usarli anche durante la messa a punto di uno unit test generato dal codice.

## <a name="framework-members"></a>Membri del framework

Per offrire una panoramica più accurata del framework di testing unità, in questa sezione i membri dello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> vengono organizzati in gruppi di funzionalità correlate.

> [!NOTE]
> Gli elementi attributo, i cui nomi terminano con "Attribute", possono essere usati con o senza "Attribute" alla fine. I due esempi di codice seguenti presentano lo stesso funzionamento:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Membri usati per i test basati sui dati

Usare gli elementi seguenti per configurare unit test basati sui dati. Per altre informazioni, vedere [Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md) e [Usare un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Attributi usati per stabilire un ordine di chiamata

Un elemento di codice decorato con uno degli attributi seguenti viene chiamato nel momento specificato. Per altre informazioni, vedere [Anatomia di un unit test](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Attributi per gli assembly

AssemblyInitialize e AssemblyCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento dell'assembly.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Attributi per classi

ClassInitialize e ClassCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento della classe.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Attributi per i metodi di test

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributi usati per identificare classi e metodi di test

Ogni classe di test deve avere l'attributo `TestClass` e ogni metodo di test deve avere l'attributo `TestMethod`. Per altre informazioni, vedere [Anatomia di un unit test](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Classi Assert ed eccezioni correlate

Gli unit test possono verificare il comportamento specifico dell'applicazione in base all'uso di vari tipi di asserzioni, eccezioni e attributi. Per altre informazioni, vedere [Uso delle classi di asserzione](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Classe TestContext

I seguenti attributi e i valori ad essi assegnati sono visualizzati nella finestra Proprietà di Visual Studio per un determinato metodo di test. Questi attributi non sono pensati per essere accessibili tramite il codice dello unit test. Influiscono invece sui modi in cui viene usato o eseguito lo unit test, ovvero manualmente tramite l'IDE di Visual Studio o dal motore di test di Visual Studio. Ad esempio, alcuni di questi attributi sono visualizzati come colonne nella finestra **Gestione test** e nella finestra **Risultati del test**, quindi è possibile usarli per raggruppare e ordinare i test e i risultati dei test. Uno di questi attributi è <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, che viene usato per aggiungere metadati arbitrari agli unit test. È ad esempio possibile usarlo per archiviare il nome del superamento di un test coperto da questo test, contrassegnando lo unit test con `[TestProperty("TestPass", "Accessibility")]`. In alternativa, è possibile usarlo per archiviare un indicatore del tipo di test con `[TestProperty("TestKind", "Localization")]`. La proprietà creata usando questo attributo e il valore di proprietà assegnato vengono entrambi visualizzati nella finestra **Proprietà** di Visual Studio, sotto l'intestazione **Specifico del test**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Classi di configurazione di test

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Attributi usati per generare report

Gli attributi in questa sezione correlano il metodo di test che decorano alle entità nella gerarchia del progetto di un progetto team di Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Classi usate con funzioni di accesso private

È possibile generare uno unit test per un metodo privato. Questa generazione crea una classe di funzione di accesso privata, che crea un'istanza di un oggetto della classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> è una classe wrapper che usa la reflection come parte del processo della funzione di accesso privata. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> è simile, ma viene usata per chiamare metodi statici privati anziché metodi di istanza privata.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Vedi anche

- Documentazione di riferimento per <xref:Microsoft.VisualStudio.TestTools.UnitTesting>