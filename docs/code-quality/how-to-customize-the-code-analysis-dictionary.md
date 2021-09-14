---
title: 'Procedura: Personalizzare il dizionario di analisi del codice'
ms.date: 11/04/2016
description: Informazioni sul dizionario di analisi del codice che identifica gli errori di ortografia e convenzione di denominazione. Vedere come creare un dizionario personalizzato e applicarlo a un progetto.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: f22d14e5cfeff8bc79327d62a10abd9a54c8bf2b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631973"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procedura: Personalizzare il dizionario di analisi del codice

Code Analysis usa un dizionario predefinito per verificare la presenza di errori di ortografia, di distinzione tra maiuscole e minuscole nel codice e altre convenzioni di denominazione delle linee guida per la progettazione di .NET. È possibile creare un file Xml del dizionario personalizzato per aggiungere, rimuovere o modificare termini, abbreviazioni e acronimi al dizionario predefinito.

Si supponga, ad esempio, che il codice contiene una **classe denominata DoorKnokker**. Code Analysis il nome viene identificato come composto da due parole: **door** e **knokker.** Viene quindi generato un avviso che indica che l'ortografia del **fazzoletto** non è corretta. Per forzare l'analisi del codice a riconoscere l'ortografia, è possibile aggiungere il termine **knokker** al dizionario personalizzato.

## <a name="to-create-a-custom-dictionary"></a>Per creare un dizionario personalizzato

Creare un file denominato **CustomDictionary.xml**.

Definire le parole personalizzate usando la struttura XML seguente:

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Elementi del dizionario personalizzati

È possibile modificare il comportamento del dizionario Code Analysis aggiungendo termini come testo interno degli elementi seguenti nel dizionario personalizzato:

- [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dizionario/Parole/Non riconosciuto/Parola](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/Deprecated/Term[ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/Words/Compound/Term[ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary/Words/Recognized/Word

Per includere un termine nell'elenco di termini identificati correttamente dall'analisi del codice, aggiungere il termine come testo interno di un elemento Dictionary/Words/Recognized/Word. Per i termini negli elementi Dictionary/Words/Recognized/Word non viene fatto distinzione tra maiuscole e minuscole.

**Esempio**

```xml
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

I termini nei nodi Dictionary/Words/Recognized vengono applicati alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionary/Words/Unrecognized/Word

Per escludere un termine dall'elenco di termini identificati correttamente dall'analisi del codice, aggiungere il termine da escludere come testo interno di un elemento Dictionary/Words/Unrecognized/Word. Per i termini negli elementi Dictionary/Words/Unrecognized/Word non viene fatto distinzione tra maiuscole e minuscole.

**Esempio**

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

I termini nel nodo Dictionary/Words/Unrecognized vengono applicati alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary/Words/Deprecated/Term[ @PreferredAlternate ]

Per includere un termine nell'elenco di termini identificati dall'analisi del codice come deprecati, aggiungere il termine come testo interno di un elemento Dictionary/Words/Deprecated/Term. Un termine deprecato è una parola digitata correttamente ma che non deve essere usata.

Per includere un termine alternativo suggerito nell'avviso, specificare l'alternativa nell'attributo PreferredAlternate dell'elemento Term. È possibile lasciare vuoto il valore dell'attributo se non si vuole suggerire un'alternativa.

- Il termine deprecato nell'elemento Dictionary/Words/Deprecated/Term non fa distinzione tra maiuscole e minuscole.

- Il valore dell'attributo PreferredAlternate fa distinzione tra maiuscole e minuscole. Usare il caso Pascal per le alternative composte.

**Esempio**

```xml
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

I termini nel nodo Dictionary/Words/Deprecated vengono applicati alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/Words/Compound/Term[ @CompoundAlternate ]

Il dizionario predefinito identifica alcuni termini come termini singoli e discreti anziché come termini composti. Per includere un termine nell'elenco di termini identificati dall'analisi codice come parola composta e per specificare le maiuscole e minuscole corrette del termine, aggiungere il termine come testo interno di un elemento Dictionary/Words/Compound/Term. Nell'attributo CompoundAlternate dell'elemento Term specificare le singole parole che costituiscono il termine composto in maiuscolo per la prima lettera delle singole parole (case Pascal). Si noti che il termine specificato nel testo interno viene aggiunto automaticamente all'elenco Dictionary/Words/DiscreteExceptions.

- Il termine composto nell'elemento Dictionary/Words/Compound/Term non fa distinzione tra maiuscole e minuscole.

- Il valore dell'attributo CompoundAlternate fa distinzione tra maiuscole e minuscole. Usare il caso Pascal per le alternative composte.

**Esempio**

```xml
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

I termini nel nodo Dictionary/Words/Compound vengono applicati alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term

Per escludere un termine nell'elenco di termini identificati dall'analisi del codice come singola parola discreta quando il termine viene controllato dalle regole di distinzione tra maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento Dictionary/Words/DiscreteExceptions/Term. Il termine nell'elemento Dictionary/Words/DiscreteExceptions/Term non fa distinzione tra maiuscole e minuscole.

**Esempio**

```xml
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

I termini nel nodo Dictionary/Words/DiscreteExceptions vengono applicati alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary/Acronyms/CasingExceptions/Acronym

Per includere un acronimo nell'elenco di termini identificati dall'analisi del codice come digitati correttamente e per indicare come l'acronimo quando il termine viene controllato dalle regole di distinzione tra maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento Dictionary/Acronyms/CasingExceptions/Acronym. L'acronimo nell'elemento Dictionary/Acronyms/CasingExceptions/Acronym fa distinzione tra maiuscole e minuscole.

**Esempio**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

I termini nel nodo Dictionary/Acronyms/CasingExceptions vengono applicati alle regole di analisi del codice seguenti:

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Per applicare un dizionario personalizzato a un progetto

1. In **Esplora soluzioni** usare una delle procedure seguenti:

    - Per aggiungere un dizionario a un singolo progetto, fare clic con il pulsante destro del mouse sul nome del progetto e quindi scegliere **Aggiungi elemento esistente**. Specificare il file nella **finestra di dialogo Aggiungi elemento** esistente .
  
    - Per aggiungere un dizionario condiviso tra due o più progetti,  individuare il file da condividere nella  finestra di dialogo Aggiungi elemento esistente , fare clic sulla freccia giù sul pulsante Aggiungi e quindi su Aggiungi come **collegamento**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **sul nome** CustomDictionary.xmlfile e scegliere **Proprietà**.

3. **Nell'elenco Azione di** compilazione selezionare **CodeAnalysisDictionary**.

4. **Nell'elenco Copia nella directory di output** selezionare Non **copiare**.
