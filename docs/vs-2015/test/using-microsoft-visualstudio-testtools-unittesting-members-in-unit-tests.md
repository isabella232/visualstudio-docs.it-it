---
title: Uso di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: douge
ms.openlocfilehash: ef2c5f81f868f2b5d7eac68030b842bd1c45067c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527442"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Utilizzo di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [tramite i membri. UnitTesting in Unit test](https://docs.microsoft.com/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests).

Il framework di unit test supporta gli unit test in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Usare le classi e membri nello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> durante la codifica di unit test. È possibile usarli sia quando si scrive uno unit test da zero che per la modifica di uno unit test generato dal codice sottoposto a test.

## <a name="groups-of-elements"></a>Gruppi di elementi
 Per offrire una panoramica più accurata del framework di unit test, in questa sezione gli elementi dello spazio dei nomi UnitTesting vengono organizzati in gruppi di funzionalità correlate.

> [!NOTE]
> Gli elementi di attributo, i cui nomi terminano con la stringa Attribute, possono essere usati con o senza la stringa Attribute. I due esempi di codice seguenti presentano lo stesso funzionamento:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Elementi usati per i test basati sui dati
 Usare gli elementi seguenti per configurare unit test basati sui dati. Per altre informazioni, vedere [Procedura: Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md) e [Procedura dettagliata: Uso di un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Attributi usati per stabilire un ordine di chiamata
 Un elemento di codice decorato con uno degli attributi seguenti viene chiamato nel momento specificato. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Per gli assembly
 AssemblyInitialize e AssemblyCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento dell'assembly.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Per le classi
 ClassInitialize e ClassCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento della classe.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Per i metodi di test

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributi usati per identificare classi e metodi di test
 Ogni classe di test deve avere l'attributo TestClass e ogni metodo di test deve avere l'attributo TestMethod. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Classi Assert ed eccezioni correlate
 Gli unit test possono verificare il comportamento specifico dell'applicazione in base all'uso di vari tipi di istruzioni, eccezioni e attributi Assert. Per altre informazioni, vedere [Uso di classi Assert](../test/using-the-assert-classes.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Classe TestContext
 I seguenti attributi e i valori ad essi assegnati sono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per un determinato metodo di test. Questi attributi non sono pensati per essere accessibili tramite il codice dello unit test. Influiscono invece sui modi in cui lo unit test viene usato o eseguito, dallo sviluppatore tramite l'IDE di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oppure dal motore di test di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ad esempio, alcuni di questi attributi sono visualizzati come colonne nella finestra Gestione test e nella finestra Risultati del test, quindi è possibile usarli per raggruppare e ordinare i test e i risultati dei test. Uno di questi attributi è TestPropertyAttribute, che viene usato per aggiungere metadati arbitrari agli unit test. È ad esempio possibile usarlo per archiviare il nome del superamento di un test coperto da questo test, contrassegnando lo unit test con `[TestProperty("TestPass", "Accessibility")]`. In alternativa, è possibile usarlo per archiviare un indicatore del tipo di test: `[TestProperty("TestKind", "Localization")]`. La proprietà creata usando questo attributo e il valore di proprietà assegnato sono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], sotto l'intestazione **Specifico del test**.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Classi di configurazione di test

-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Attributi usati per la generazione di report
 Gli attributi in questa sezione correlano il metodo di test che decorano alle entità nella gerarchia del progetto di un progetto team di [!INCLUDE[esprtfs](../includes/esprtfs-md.md)].

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Classi usate con funzioni di accesso private
 Come descritto in [Utilizzo di Publicize per creare una funzione di accesso privata](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), è possibile generare uno unit test per un metodo privato. Questa generazione crea una classe di funzioni di accesso private, che crea un'istanza di un oggetto della classe PrivateObject. La classe PrivateObject è una classe wrapper che usa la reflection come parte del processo della funzione di accesso privata. La classe PrivateType è simile, ma viene usata per chiamare metodi statici privati anziché metodi di istanza privata.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>