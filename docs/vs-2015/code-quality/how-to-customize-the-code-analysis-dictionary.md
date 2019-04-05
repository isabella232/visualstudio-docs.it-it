---
title: 'Procedura: Personalizzare il dizionario di analisi del codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e90b92418d9416139e814bd16dc0d655977c0b27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967699"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procedura: Personalizzare il dizionario di analisi codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analisi del codice Usa un dizionario predefinito per verificare gli identificatori nel codice per gli errori di ortografia, grammaticale case e altre convenzioni di denominazione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] linee guida. È possibile creare un file Xml del dizionario personalizzato per aggiungere, rimuovere o modificare i termini e abbreviazioni acronimi al dizionario predefinito.  
  
 Ad esempio, si supponga che il codice contiene una classe denominata **contraccolpo**. Analisi del codice identifica il nome come un insieme di due parole: **sportello** e **colpo**. Verrà generato un avviso che **colpo** non sia stato digitato correttamente. Per forzare l'analisi del codice per riconoscere il controllo ortografico, è possibile aggiungere il termine **colpo** al dizionario personalizzato.  
  
## <a name="to-create-a-custom-dictionary"></a>Per creare un dizionario personalizzato  
 Creare un file denominato **DizionarioPersonale**.  
  
 Definire le parole personalizzate usando la struttura XML seguente:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
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
  
## <a name="custom-dictionary-elements"></a>Elementi del dizionario personalizzato  
 È possibile modificare il comportamento nel dizionario di analisi del codice mediante l'aggiunta di condizioni come testo interno degli elementi seguenti nel dizionario personalizzato:  
  
- [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
- [Dictionary/Words/Unrecognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
- [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
- [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary/Words/Recognized/Word  
 Per includere un termine nell'elenco dei termini che identifica l'analisi del codice come digitati correttamente, aggiungere il termine come testo interno di un elemento del dizionario e parole/Recognized/di parole. Le condizioni negli elementi di dizionario e parole/Recognized/di parole non sono tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
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
  
 Le condizioni in nodi di dizionario/parole/Recognized vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionary/Words/Unrecognized/Word  
 Per escludere un termine nell'elenco dei termini che identifica l'analisi del codice come digitati correttamente, aggiungere il termine da escludere come testo interno di un elemento del dizionario/parole/non riconosciuto o Word. Le condizioni negli elementi dizionario/parole/non riconosciuto/Word non sono tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
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
  
 Le condizioni nel nodo dizionario/parole/non riconosciuto vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary/Words/Deprecated/Term[@PreferredAlternate]  
 Per includere un termine nell'elenco dei termini che l'analisi del codice identifica come deprecati, aggiungere il termine come testo interno di un elemento del dizionario/parole/deprecate/termine. Un termine obsoleto è una parola che sia stata digitata correttamente, ma non deve essere utilizzata.  
  
 Per includere un termine alternativo suggerito nel messaggio di avviso, specificare alternativo nell'attributo dell'elemento termine PreferredAlternate. Se non si desidera suggerire un'alternativa, è possibile lasciare vuoto il valore dell'attributo.  
  
- Il termine deprecato nel dizionario o parole/elemento deprecato/termine non distinzione maiuscole/minuscole.  
  
- Il valore dell'attributo PreferredAlternate è tra maiuscole e minuscole. La convenzione Pascal caso di utilizzo per le alternative composte.  
  
  **Esempio**  
  
```  
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
  
 Le condizioni nel nodo dizionario/parole/deprecate vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/Words/Compound/Term[@CompoundAlternate]  
 Il dizionario predefinito identifica alcuni termini come termini discreti, single, anziché un termine composto. Per includere un termine nell'elenco dei termini che identifica l'analisi del codice come una parola composta e specificare le maiuscole e minuscole corrette del periodo di validità, aggiungere il termine come testo interno di un elemento del dizionario/parole/composta/termine. Nell'attributo dell'elemento Term CompoundAlternate, specificare le singole parole che compongono il termine composto sfruttando la prima lettera delle parole singole (maiuscole minuscole Pascal). Si noti che il termine specificato nel testo interno viene automaticamente aggiunto all'elenco di parole/Dictionary/DiscreteExceptions.  
  
- Il termine deprecato nel dizionario o parole/elemento deprecato/termine non distinzione maiuscole/minuscole.  
  
- Il valore dell'attributo PreferredAlternate è tra maiuscole e minuscole. La convenzione Pascal caso di utilizzo per le alternative composte.  
  
  **Esempio**  
  
```  
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
  
 Le condizioni nel nodo dizionario/parole/composti vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term  
 Per escludere un termine nell'elenco dei termini che identifica l'analisi del codice come un singolo, word discreti quando il termine è controllato dalle regole di maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento del dizionario/parole/DiscreteExceptions/termine. Il termine nell'elemento dizionario/parole/DiscreteExceptions/termine non distinzione maiuscole/minuscole.  
  
 **Esempio**  
  
```  
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
  
 Le condizioni nel nodo dizionario/parole/DiscreteExceptions vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary/Acronyms/CasingExceptions/Acronym  
 Per includere un acronimo nell'elenco dei termini che identifica l'analisi del codice come sia stata digitata correttamente e indicare come l'acronimo quando il termine è selezionato per le maiuscole e minuscole delle regole per le parole composte, aggiungere il termine come testo interno di un dizionario/acronimi/CasingExceptions / Elemento Acronym. L'acronimo nell'elemento dizionario/acronimi/CasingExceptions/Acronym è tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Le condizioni nel nodo dizionario/acronimi/CasingExceptions vengono applicate le regole di analisi di codice seguente:  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Per applicare un dizionario personalizzato a un progetto  
  
1.  Nelle **Esplora soluzioni**, usare una delle procedure riportate di seguito:  
  
2.  Per aggiungere un dizionario per un singolo progetto, il pulsante destro del mouse e quindi fare clic su **Aggiungi elemento esistente**. Specificare il file nei **Aggiungi elemento esistente** nella finestra di dialogo.  
  
3.  Per aggiungere un dizionario che viene condiviso tra due o più progetti, individuare il file da condividere nel **Aggiungi elemento esistente** finestra di dialogo fare clic sulla freccia in giù nel **Add** pulsante e quindi fare clic su **Aggiungi come collegamento** .  
  
4.  Nella **Esplora soluzioni**, fare doppio clic il **DizionarioPersonale** nome file e fare clic su **proprietà**.  
  
5.  Dal **Build Action** elenco, selezionare **CodeAnalysisDictionary**.  
  
6.  Dal **copia in Directory di Output** elenco, selezionare **non copiare**.
