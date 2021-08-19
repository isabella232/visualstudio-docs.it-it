---
title: Creare viste personalizzate di oggetti di C++
description: Usare il framework Natvis per personalizzare il modo in cui Visual Studio tipi nativi nel debugger
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 484d29f0c1976181007afee4d3da2f2e2e659d23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121786"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Creare visualizzazioni personalizzate di oggetti C++ nel debugger usando il framework Natvis

Il Visual Studio *framework Natvis* personalizza il modo in cui i tipi  nativi vengono visualizzati nelle finestre delle variabili del debugger, ad esempio le finestre Variabili locali e **Espressioni** di controllo e in **Suggerimenti dati**. Le visualizzazioni Natvis consentono di rendere più visibili i tipi creati durante il debug.

Natvis sostituisce il file *autoexp.dat* nelle versioni precedenti di Visual Studio con sintassi XML, diagnostica migliore, controllo delle versioni e supporto di più file.

> [!NOTE]
> Le personalizzazioni natvis funzionano con classi e struct, ma non con typedef.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualizzazioni natvis

Il framework Natvis consente di creare regole di visualizzazione per i tipi creati, in modo che gli sviluppatori possano vederle più facilmente durante il debug.

Ad esempio, la figura seguente mostra una variabile di tipo [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in una finestra del debugger senza alcuna visualizzazione personalizzata applicata.

![Visualizzazione predefinita di TextBox](../debugger/media/dbg_natvis_textbox_default.png "Visualizzazione predefinita di TextBox")

La riga evidenziata mostra la proprietà `Text` della classe `TextBox` . La gerarchia di classi complesse rende difficile trovare questa proprietà. Il debugger non sa come interpretare il tipo di stringa personalizzata, quindi non è possibile visualizzare la stringa mantenuta all'interno della casella di testo.

Lo stesso aspetto è molto più semplice nella finestra delle variabili quando vengono applicate le `TextBox` regole del visualizzatore personalizzato natvis. I membri importanti della classe vengono visualizzati insieme e il debugger mostra il valore di stringa sottostante del tipo di stringa personalizzato.

![Dati TextBox con uso di visualizzatore](../debugger/media/dbg_natvis_textbox_visualizer.png "Dati TextBox con uso di visualizzatore")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Usare i file natvis nei progetti C++

Natvis usa *i file natvis* per specificare le regole di visualizzazione. Un file *natvis* è un file XML con estensione *natvis.* Lo schema Natvis è definito in *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

La struttura di base di un file *natvis* è uno o più `Type` elementi che rappresentano le voci di visualizzazione. Il nome completo di ogni `Type` elemento viene specificato nel relativo attributo `Name` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio alcuni *file natvis* nella cartella *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers.* Questi file hanno regole di visualizzazione per molti tipi comuni e possono fungere da esempi per la scrittura di visualizzazioni per nuovi tipi.

### <a name="add-a-natvis-file-to-a-c-project"></a>Aggiungere un file natvis a un progetto C++

È possibile aggiungere un file *natvis* a qualsiasi progetto C++.

**Per aggiungere un nuovo file *natvis:***

1. Selezionare il nodo del progetto C++ in **Esplora soluzioni** e selezionare Project Aggiungi nuovo elemento oppure **fare** clic con il pulsante destro del mouse sul progetto e scegliere  >   **Aggiungi**  >  **nuovo elemento**.

1. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Visual C++ file di visualizzazione del debugger dell'utilità   >    >  **(con estensione natvis).**

1. Assegnare un nome al file e selezionare **Aggiungi**.

   Il nuovo file viene aggiunto a **Esplora soluzioni** e viene aperto nel riquadro Visual Studio documento.

Il debugger Visual Studio carica automaticamente i file *natvis* nei progetti C++ e, per impostazione predefinita, li include anche nel file *con estensione pdb* quando il progetto viene compilato. Se si esegue il debug dell'app compilata, il debugger carica il file *natvis* dal file *con estensione pdb,* anche se il progetto non è aperto. Se non si vuole che il file *natvis* sia incluso nel file con estensione *pdb,* è possibile escluderlo dal file *con estensione pdb* compilato.

**Per escludere un file *natvis* da un *file con estensione pdb:***

1. Selezionare il file *natvis* in **Esplora soluzioni** e  selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul file e scegliere **Proprietà**.

1. Fare clic sulla freccia accanto a **Escluso dalla compilazione** e selezionare **Sì** e quindi **selezionare OK.**

>[!NOTE]
>Per il debug di progetti eseguibili, usare gli elementi della soluzione per aggiungere tutti i file *natvis* non presenti nel file con estensione *pdb,* poiché non è disponibile alcun progetto C++.

>[!NOTE]
>Le regole Natvis caricate da *un file con estensione pdb* si applicano solo ai tipi nei moduli a cui fa riferimento il file con estensione *pdb.* Ad esempio, se *Module1.pdb* ha una voce Natvis per un tipo denominato , si applica solo alla classe `Test` `Test` in *Module1.dll*. Se un altro modulo definisce anche una classe denominata `Test` , la *voce Natvis Module1.pdb* non si applica a essa.

**Per installare e registrare un file *natvis* tramite un pacchetto VSIX:**

Un pacchetto VSIX può installare e registrare *i file natvis.* Indipendentemente dalla posizione in cui vengono installati, tutti i file *natvis* registrati vengono prelevati automaticamente durante il debug.

1. Includere il file *natvis* nel pacchetto VSIX. Ad esempio, per il file di progetto seguente:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registrare il file *natvis* nel file *source.extension.vsixmanifest:*

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Percorsi dei file Natvis

È possibile aggiungere *file natvis* alla directory utente o a una directory di sistema, se si vuole che si appliino a più progetti.

I *file natvis* vengono valutati nell'ordine seguente:

1. Tutti *i file natvis* incorporati in un file con estensione *pdb* di cui si esegue il debug, a meno che non esista un file con lo stesso nome nel progetto caricato.

2. Tutti *i file natvis* presenti in un progetto C++ caricato o in una soluzione di primo livello. Questo gruppo include tutti i progetti C++ caricati, incluse le librerie di classi, ma non i progetti in altri linguaggi.

3. Tutti *i file natvis* installati e registrati tramite un pacchetto VSIX.

::: moniker range="vs-2017"

4. Directory Natvis specifica dell'utente(ad *esempio% USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Directory Natvis specifica dell'utente (ad *esempio% USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. La directory Natvis a livello di sistema (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Questa directory contiene *i file natvis* installati con Visual Studio. Se si dispone delle autorizzazioni di amministratore, è possibile aggiungere file a questa directory.

## <a name="modify-natvis-files-while-debugging"></a>Modificare i file natvis durante il debug

È possibile modificare un file *natvis* nell'IDE durante il debug del relativo progetto. Aprire il file nella stessa istanza di Visual Studio con cui si esegue il debug, modificarlo e salvarlo. Non appena il file viene salvato, le finestre **Espressioni di** **controllo** e Variabili locali vengono aggiornate per riflettere la modifica.

È anche possibile aggiungere o eliminare *file natvis* in una soluzione di cui si esegue il debug Visual Studio aggiunge o rimuove le visualizzazioni pertinenti.

Non è possibile aggiornare *i file natvis* incorporati nei *file con estensione pdb* durante il debug.

Se si modifica il file *natvis* all'esterno Visual Studio, le modifiche non vengono applicate automaticamente. Per aggiornare le finestre del debugger, è possibile rivalutare il comando **natvisreload** nella **finestra Controllo** immediato. Le modifiche vengono quindi applicate senza riavviare la sessione di debug.

Usare anche **il comando natvisreload** per aggiornare il file *natvis* a una versione più recente. Ad esempio, il file *natvis* può essere archiviato nel controllo del codice sorgente e si vogliono raccogliere le modifiche recenti apportate da altri utenti.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Espressioni e formattazione
Nelle visualizzazioni Natvis si usano espressioni C++ per specificare gli elementi di dati da visualizzare. Oltre ai miglioramenti e alle limitazioni delle espressioni C++ nel debugger, descritti in Operatore di contesto [(C++),](../debugger/context-operator-cpp.md)tenere presente quanto segue:

- Le espressioni di Natvis vengono valutate nel contesto dell'oggetto da visualizzare, non nello stack frame corrente. Ad esempio, in un'espressione Natvis si fa riferimento al campo denominato x nell'oggetto visualizzato, non a una variabile locale denominata `x` **x** nella funzione corrente.  Non è possibile accedere alle variabili locali nelle espressioni Natvis, anche se è possibile accedere alle variabili globali.

- Le espressioni Natvis non consentono la valutazione della funzione o gli effetti collaterali. Le chiamate di funzione e gli operatori di assegnazione vengono ignorati. Dal momento che le [funzioni intrinseche del debugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) non hanno effetti collaterali, possono essere chiamate liberamente da qualsiasi espressione Natvis, anche se non sono consentite altre chiamate di funzione.

- Per controllare la modalità di visualizzazione di un'espressione, è possibile usare uno degli identificatori di formato descritti in Identificatori di [formato in C++.](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) Gli identificatori di formato vengono ignorati quando la voce viene utilizzata internamente da Natvis, ad esempio l'espressione `Size` in [un'espansione ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

>[!NOTE]
> Poiché il documento natvis è XML, le espressioni non possono usare direttamente gli operatori e commerciale, maggiore di, minore di o MAIUSC. È necessario eseguire l'escape di questi caratteri sia nel corpo dell'elemento che nelle istruzioni della condizione. Esempio:<br>
> \<Item Name="HiByte"\>(byte) (_flags \& gt; \& > 24),x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>"None"\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>"Some"\</Item\>

## <a name="natvis-views"></a>Visualizzazioni di Natvis

È possibile definire visualizzazioni Natvis diverse per visualizzare i tipi in modi diversi. Ad esempio, ecco una visualizzazione di `std::vector` che definisce una visualizzazione semplificata denominata `simple` . Gli elementi e vengono visualizzati nella visualizzazione predefinita e nella visualizzazione, mentre gli elementi e non vengono `DisplayString` `ArrayItems` visualizzati nella `simple` `[size]` `[capacity]` `simple` visualizzazione.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Nella finestra **Espressione di** controllo usare l'identificatore di formato **,view** per specificare una visualizzazione alternativa. La visualizzazione semplice viene visualizzata come **vec,view(simple)**:

![Finestra Espressioni di controllo con visualizzazione semplice](../debugger/media/watch-simpleview.png "Finestra Espressioni di controllo con visualizzazione semplice")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Errori natvis

Quando il debugger rileva errori in una voce di visualizzazione, li ignora. Visualizza il tipo nel formato non elaborato o seleziona un'altra visualizzazione appropriata. È possibile usare la diagnostica Natvis per comprendere il motivo per cui il debugger ha ignorato una voce di visualizzazione e per visualizzare la sintassi sottostante e gli errori di analisi.

**Per attivare la diagnostica natvis:**

- In Opzioni degli strumenti (o Opzioni di debug) > Debug Finestra di output impostare Messaggi di diagnostica  >     >     >   **Natvis (solo C++)** su **Errore**,   Avviso o Dettagliato e quindi selezionare OK .

Gli errori vengono visualizzati nella **finestra Output.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Riferimento per la sintassi di Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
L'elemento `AutoVisualizer` è il nodo radice del file *NATVIS* e contiene l'attributo `xmlns:` dello spazio dei nomi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer`L'elemento può avere elementi figlio [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)e [CustomVisualizer.](#BKMK_CustomVisualizer)

### <a name="type-element"></a><a name="BKMK_Type"></a> Elemento Type

Un elemento di `Type` base è simile all'esempio seguente:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type`L'elemento specifica:

1. Tipo per cui deve essere usata la visualizzazione `Name` (attributo ).

2. A quale valore di un oggetto di tale tipo deve essere simile (elemento `DisplayString` ).

3. Aspetto dei membri del tipo quando l'utente espande il tipo in una finestra variabile `Expand` (nodo).

#### <a name="templated-classes"></a>Classi modello
`Name`L'attributo dell'elemento accetta un asterisco come carattere jolly che può essere usato per i nomi di classe `Type` `*` modello.

Nell'esempio seguente viene usata la stessa visualizzazione se l'oggetto è o `CAtlArray<int>` `CAtlArray<float>` . Se è presente una voce di visualizzazione specifica per `CAtlArray<float>` un oggetto , ha la precedenza su quella generica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

È possibile fare riferimento ai parametri del modello nella voce di visualizzazione usando le macro $T 1, $T 2 e così via. Per esempi di queste macro, vedere i file *NATVIS* forniti con Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Corrispondenza del tipo di visualizzatore
Se la convalida di una voce di visualizzazione non riesce, viene usata la successiva visualizzazione disponibile.

#### <a name="inheritable-attribute"></a>Attributo Inheritable
L'attributo facoltativo specifica se una visualizzazione si applica solo a un tipo `Inheritable` di base o a un tipo di base e a tutti i tipi derivati. Il valore predefinito di `Inheritable` è `true`.

Nell'esempio seguente la visualizzazione si applica solo al `BaseClass` tipo :

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attributo Priority

`Priority`L'attributo facoltativo specifica l'ordine in cui usare le definizioni alternative, se l'analisi di una definizione non riesce. I valori possibili di `Priority` sono: `Low` , , , e `MediumLow` `Medium` `MediumHigh` `High` . Il valore predefinito è `Medium`. `Priority`L'attributo distingue solo tra le priorità all'interno dello stesso file *natvis.*

Nell'esempio seguente viene innanzitutto analizzata la voce corrispondente al valore STL 2015. Se l'analisi non riesce, usa la voce alternativa per la versione 2013 della STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Attributo Optional
È possibile inserire un `Optional` attributo in qualsiasi nodo. Se l'analisi di una sottoespressione all'interno di un nodo facoltativo non riesce, il debugger lo ignora, ma applica le altre `Type` regole. Nel tipo seguente `[State]` non è facoltativo, mentre `[Exception]` lo è.  Se ha un campo denominato _ , vengono visualizzati sia il nodo che il nodo, ma se non è presente alcun campo, viene visualizzato `MyNamespace::MyClass` `M_exceptionHolder` solo il `[State]` `[Exception]` `_M_exceptionHolder` `[State]` nodo.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Attributo Condition

`Condition`L'attributo facoltativo è disponibile per molti elementi di visualizzazione e specifica quando usare una regola di visualizzazione. Se l'espressione all'interno dell'attributo della condizione viene risolta in `false` , la regola di visualizzazione non viene applicata. Se restituisce o non è presente alcun attributo, viene `true` applicata la `Condition` visualizzazione. È possibile usare questo attributo per la logica if-else nelle voci di visualizzazione.

Ad esempio, la visualizzazione seguente include due `DisplayString` elementi per un tipo di puntatore intelligente. Quando il membro è vuoto, la condizione del primo elemento viene risolta `_Myptr` in , in modo che il form sia `DisplayString` `true` visualizzato. Quando il `_Myptr` membro non è vuoto, la condizione restituisce `false` e viene visualizzato il secondo `DisplayString` elemento.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Attributi IncludeView e ExcludeView

Gli `IncludeView` attributi `ExcludeView` e specificano gli elementi da visualizzare o meno in visualizzazioni specifiche. Ad esempio, nella specifica Natvis seguente di `std::vector` , la visualizzazione non visualizza gli elementi e `simple` `[size]` `[capacity]` .

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

È possibile usare gli `IncludeView` attributi e sui tipi e sui singoli `ExcludeView` membri.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Elemento Version
`Version`L'elemento ha come ambito una voce di visualizzazione per un modulo e una versione specifici. L'elemento consente di evitare conflitti di nomi, riduce le mancate corrispondenze accidentali e consente visualizzazioni diverse `Version` per versioni di tipo diverse.

Se un file di intestazione comune usato da moduli diversi definisce un tipo, la visualizzazione con controllo delle versioni viene visualizzata solo quando il tipo si trova nella versione del modulo specificata.

Nell'esempio seguente la visualizzazione è applicabile solo per il tipo `DirectUI::Border` trovato in dalla versione `Windows.UI.Xaml.dll` 1.0 alla 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Non sono necessari sia `Min` che `Max` . Si tratta di attributi facoltativi. Non sono supportati caratteri jolly.

`Name`L'attributo è nel formato *filename.ext,* ad esempio *hello.exe* *osome.dll*. Non sono consentiti nomi di percorso.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> Elemento DisplayString
`DisplayString`L'elemento specifica una stringa da visualizzare come valore di una variabile. Accetta stringhe arbitrarie combinate con espressioni. Tutto ciò che è racchiuso tra parentesi graffe viene interpretato come un'espressione. Ad esempio, la voce `DisplayString` seguente:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa che le variabili di tipo `CPoint` vengono visualizzate come in questa figura:

 ![Usare un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Usare un elemento DisplayString")

Nell'espressione e , che sono membri di , si trova all'interno di parentesi `DisplayString` `x` `y` `CPoint` graffe, quindi i relativi valori vengono valutati. L'esempio mostra anche come è possibile usare caratteri di escape per una parentesi graffa usando doppie parentesi graffe ( `{{` o `}}` ).

> [!NOTE]
> L'elemento `DisplayString` è l'unico elemento che accetta stringhe arbitrarie e la sintassi con parentesi graffe. Tutti gli altri elementi di visualizzazione accettano solo espressioni che il debugger può valutare.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> Elemento StringView

`StringView`L'elemento definisce un valore che il debugger può inviare al visualizzatore di testo predefinito. Ad esempio, data la visualizzazione seguente per il `ATL::CStringT` tipo :

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT`L'oggetto viene visualizzato in una finestra variabile come nell'esempio seguente:

![Elemento DisplayString CStringT](../debugger/media/dbg_natvis_displaystring_cstringt.png "Elemento DisplayString CStringT")

L'aggiunta di un elemento indica al debugger che può `StringView` visualizzare il valore come visualizzazione di testo.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante il debug, è possibile selezionare l'icona a forma di lente di ingrandimento accanto alla variabile e quindi selezionare **Visualizzatore** di testo per visualizzare la stringa **a** cui m_pszData punta.

 ![Dati CStringT con visualizzatore StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Dati CStringT con visualizzatore StringView")

L'espressione include un identificatore di `{m_pszData,su}` formato C++ **su** per visualizzare il valore come stringa Unicode. Per altre informazioni, vedere [Identificatori di formato in C++.](../debugger/format-specifiers-in-cpp.md)

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Elemento Expand

Il nodo `Expand` facoltativo personalizza gli elementi figlio di un tipo visualizzato quando si espande il tipo in una finestra variabile. Il `Expand` nodo accetta un elenco di nodi figlio che definiscono gli elementi figlio.

- Se non `Expand` viene specificato un nodo in una voce di visualizzazione, gli elementi figlio usano le regole di espansione predefinite.

- Se viene specificato un nodo senza nodi figlio, il tipo non è espandibile `Expand` nelle finestre del debugger.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Espansione di Item

 `Item`L'elemento è l'elemento più semplice e comune in un `Expand` nodo. `Item` definisce un singolo elemento figlio. Ad esempio, una `CRect` classe con i campi , , e ha la voce di visualizzazione `top` `left` `right` `bottom` seguente:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Nella finestra del debugger il `CRect` tipo è simile all'esempio seguente:

![CRect con espansione dell'elemento Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con espansione dell'elemento Item")

Il debugger valuta le espressioni specificate negli elementi e e mostra i valori nella colonna `Width` Valore della finestra delle `Height` variabili. 

Il debugger crea automaticamente il **nodo [Visualizzazione non elaborata]** per ogni espansione personalizzata. Lo screenshot precedente mostra il **nodo [Visualizzazione** non elaborata] espanso, per mostrare come la visualizzazione non elaborata predefinita dell'oggetto differisce dalla relativa visualizzazione Natvis. L'espansione predefinita crea un sottoalbero per la classe di base ed elenca tutti i membri dati della classe di base come elementi figlio.

> [!NOTE]
> Se l'espressione dell'elemento item punta a un tipo complesso, il **nodo Item** stesso è espandibile.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Usare il nodo `ArrayItems` per consentire al debugger di Visual Studio di interpretare il tipo come una matrice e visualizzarne i singoli elementi. La visualizzazione per `std::vector` costituisce un ottimo esempio:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Un elemento `std::vector` visualizza i singoli elementi quando viene espanso nella finestra delle variabili:

![std::vector con uso dell'espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector con uso dell'espansione ArrayItems")

Il `ArrayItems` nodo deve avere:

- Un'espressione `Size` (che deve restituire un numero intero) per consentire al debugger di riconoscere la lunghezza della matrice.
- Espressione `ValuePointer` che punta al primo elemento (che deve essere un puntatore di un tipo di elemento che non è `void*` ).

Il valore predefinito del limite inferiore della matrice è 0. Per eseguire l'override del valore, usare un `LowerBound` elemento . I *file natvis* forniti con Visual Studio esempi.

>[!NOTE]
>È possibile usare l'operatore , ad esempio , con qualsiasi visualizzazione di matrice unidimensionale che usa , anche se il tipo stesso (ad esempio ) non `[]` `vector[i]` consente questo `ArrayItems` `CATLArray` operatore.

È anche possibile specificare matrici multidimensionali. In tal caso, il debugger necessita di altre informazioni per visualizzare correttamente gli elementi figlio:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` specifica se la matrice è in ordine row-major o column-major.
- `Rank` specifica l'ordine di priorità della matrice.
- L'elemento `Size` accetta il parametro `$i` implicito che sostituisce con l'indice delle dimensioni per individuare la lunghezza della matrice in quella dimensione. Nell'esempio precedente l'espressione deve fornire la lunghezza della `_M_extent.M_base[0]` dimensione 0, `_M_extent._M_base[1]` la prima e così via.

Ecco l'aspetto di un oggetto `Concurrency::array` bidimensionale nella finestra del debugger:

![Matrice bidimensionale con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matrice bidimensionale con espansione ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Espansione di IndexListItems

È possibile usare `ArrayItems` l'espansione solo se gli elementi della matrice sono disposti in modo contiguo in memoria. Il debugger ottiene l'elemento successivo semplicemente incrementando il puntatore. Se è necessario modificare l'indice nel nodo valore, usare `IndexListItems` nodi. Ecco una visualizzazione con un `IndexListItems` nodo:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

L'unica differenza `ArrayItems` tra e è , che prevede l'espressione completa per `IndexListItems` `ValueNode` <sup>l'elemento</sup> i con il parametro `$i` implicito .

>[!NOTE]
>È possibile usare l'operatore , ad esempio , con qualsiasi visualizzazione di matrice unidimensionale che usa , anche se il tipo stesso (ad esempio ) non `[]` `vector[i]` consente questo `IndexListItems` `CATLArray` operatore.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Espansione di LinkedListItems

Se il tipo visualizzato rappresenta un elenco collegato, il debugger può visualizzarne i figli tramite un nodo `LinkedListItems` . La visualizzazione seguente per il `CAtlList` tipo usa `LinkedListItems` :

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

L'elemento `Size` si riferisce alla lunghezza dell'elenco. `HeadPointer` punta al primo elemento, `NextPointer` fa riferimento all'elemento successivo e `ValueNode` fa riferimento al valore dell'elemento.

Il debugger valuta le espressioni `NextPointer` `ValueNode` e nel contesto dell'elemento `LinkedListItems` nodo, non il tipo di elenco padre. Nell'esempio precedente ha `CAtlList` una `CNode` classe (disponibile in ) che è un `atlcoll.h` nodo dell'elenco collegato. `m_pNext` e `m_element` sono campi di tale `CNode` classe, non della classe `CAtlList` .

`ValueNode` può essere lasciato vuoto o usare `this` per fare riferimento al nodo `LinkedListItems` stesso.

#### <a name="customlistitems-expansion"></a>Espansione CustomListItems

L'espansione `CustomListItems` consente di scrivere una logica personalizzata per attraversare una struttura dei dati, ad esempio una tabella hash. Usare per visualizzare le strutture di dati che possono usare espressioni C++ per tutto ciò che è necessario valutare, ma non si adattano perfettamente `CustomListItems` all'ambiente per `ArrayItems` , o `IndexListItems` `LinkedListItems` .

È possibile usare `Exec` per eseguire codice all'interno di `CustomListItems` un'espansione, usando le variabili e gli oggetti definiti nell'espansione. È possibile usare operatori logici, operatori aritmetici e operatori di assegnazione con `Exec` . Non è possibile usare per valutare `Exec` le funzioni, ad eccezione delle funzioni [intrinseche del debugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) supportate dall'analizzatore di espressioni C++.

Il visualizzatore seguente per `CAtlMap` è un ottimo esempio in cui è `CustomListItems` appropriato.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Espansione di TreeItems
 Se il tipo visualizzato rappresenta un albero, il debugger può esaminare l'albero e visualizzarne i figli tramite un nodo `TreeItems` . Ecco la visualizzazione per il tipo `std::map` che usa un `TreeItems` nodo:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

La sintassi è simile al `LinkedListItems` nodo . `LeftPointer`, `RightPointer` e vengono `ValueNode` valutati nel contesto della classe del nodo della struttura ad albero. `ValueNode` può essere lasciato vuoto o `this` usare per fare riferimento al nodo `TreeItems` stesso.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Espansione di ExpandedItem
 L'elemento genera una visualizzazione figlio aggregata visualizzando le proprietà delle classi base o dei membri dati come se fossero `ExpandedItem` elementi figlio del tipo visualizzato. Il debugger valuta l'espressione specificata e aggiunge i nodi figlio del risultato all'elenco figlio del tipo visualizzato.

Ad esempio, il tipo di puntatore intelligente `auto_ptr<vector<int>>` viene in genere visualizzato come:

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; 'espansione predefinita](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Espansione predefinita")

 Per visualizzare i valori del vettore, è necessario eseguire il drill-down di due livelli nella finestra delle variabili, passando attraverso il `_Myptr` membro . Aggiungendo un elemento `ExpandedItem`, è possibile eliminare la variabile `_Myptr` dalla gerarchia e visualizzare direttamente gli elementi del vettore:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; ExpandedItem expansion](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Espansione di ExpandedItem")

Nell'esempio seguente viene illustrato come aggregare le proprietà dalla classe di base in una classe derivata. Si supponga che la classe `CPanel` derivi da `CFrameworkElement`. Invece di ripetere le proprietà che provengono dalla classe di base, la visualizzazione del nodo accoda tali proprietà `CFrameworkElement` `ExpandedItem` all'elenco figlio della `CPanel` classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

In questo caso è necessario l'identificatore di formato **nd** che disattiva la corrispondenza della visualizzazione per la classe derivata. In caso contrario, l'espressione causerebbe di nuovo l'applicazione della visualizzazione, perché le regole di corrispondenza del tipo di visualizzazione predefinite la considerano `*(CFrameworkElement*)this` `CPanel` la più appropriata. Usare **l'identificatore di** formato nd per indicare al debugger di usare la visualizzazione della classe di base o l'espansione predefinita se la classe di base non ha alcuna visualizzazione.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Espansione di elementi sintetici
 Il nodo `ExpandedItem` esegue la funzione opposta rispetto all'elemento `Synthetic`, che fornisce una visualizzazione dei dati più semplice eliminando le gerarchie. Consente di creare un elemento figlio artificiale che non è il risultato di un'espressione. L'elemento artificiale può avere elementi figlio propri. Nell'esempio seguente nella visualizzazione del tipo `Concurrency::array` viene usato un nodo `Synthetic` per mostrare un messaggio di diagnostica all'utente:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency::Array con espansione di elementi sintetici](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array con espansione di elementi sintetici")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> Elemento HResult
 `HResult`L'elemento consente di personalizzare le informazioni visualizzate per un **HRESULT nelle** finestre del debugger. L'elemento `HRValue` deve contenere il valore a 32 bit di **HRESULT** da personalizzare. `HRDescription`L'elemento contiene le informazioni da visualizzare nella finestra del debugger.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> Elemento UIVisualizer
Un elemento `UIVisualizer` consente di registrare un plug-in del visualizzatore grafico con il debugger. Un visualizzatore grafico crea una finestra di dialogo o un'altra interfaccia che mostra una variabile o un oggetto in modo coerente con il tipo di dati. Il plug-in del visualizzatore deve essere creato come [VSPackage](../extensibility/internals/vspackages.md)ed esporre un servizio che il debugger può utilizzare. Il file *natvis* contiene informazioni di registrazione per il plug-in, ad esempio il nome, il GUID del servizio esposto e i tipi che può visualizzare.

Il seguente è un esempio di elemento UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- Una `ServiceId`  -  `Id` coppia di attributi identifica un oggetto `UIVisualizer` . è `ServiceId` il GUID del servizio esposto dal pacchetto del visualizzatore. `Id` è un identificatore univoco che distingue i visualizzatori, se un servizio ne fornisce più di uno. Nell'esempio precedente lo stesso servizio visualizzatore fornisce due visualizzatori.

- L'attributo definisce il nome di un visualizzatore da visualizzare nell'elenco a discesa accanto all'icona della lente di `MenuName` ingrandimento nel debugger. Esempio:

  ![Menu di scelta rapida UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu di scelta rapida UIVisualizer")

Ogni tipo definito nel file *natvis* deve elencare in modo esplicito tutti i visualizzatori dell'interfaccia utente che possono visualizzarlo. Il debugger trova la corrispondenza tra i riferimenti del visualizzatore nelle voci di tipo e i visualizzatori registrati. Ad esempio, la voce di tipo seguente per `std::vector` fa `UIVisualizer` riferimento a nell'esempio precedente.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 È possibile visualizzare un esempio di `UIVisualizer` nell'estensione [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) usata per visualizzare le bitmap in memoria.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer`è un punto di estendibilità che specifica un'estensione VSIX da scrivere per controllare le visualizzazioni Visual Studio codice. Per altre informazioni sulla scrittura di estensioni VSIX, vedere Visual Studio [SDK.](../extensibility/visual-studio-sdk.md)

È molto più importante scrivere un visualizzatore personalizzato rispetto a una definizione NATVIS XML, ma non sono vincoli su ciò che Natvis fa o non supporta. I visualizzatori personalizzati hanno accesso al set completo di API di estendibilità del debugger, che possono eseguire query e modificare il processo dell'oggetto del debug o comunicare con altre parti del Visual Studio.

 È possibile usare `Condition` gli attributi , e sugli elementi `IncludeView` `ExcludeView` `CustomVisualizer` .

## <a name="limitations"></a>Limitazioni

Le personalizzazioni natvis funzionano con classi e struct, ma non con typedef.

Natvis non supporta i visualizzatori per i tipi primitivi (ad esempio , ) o per i `int` `bool` puntatori a tipi primitivi. In questo scenario, un'opzione consiste nell'usare [l'identificatore di formato](../debugger/format-specifiers-in-cpp.md) appropriato per il caso d'uso. Ad esempio, se si usa nel codice, è possibile usare un identificatore di formato di matrice nella finestra Espressione di controllo del debugger, ad esempio l'espressione , che mostra i primi `double* mydoublearray`  `mydoublearray, [100]` 100 elementi.
