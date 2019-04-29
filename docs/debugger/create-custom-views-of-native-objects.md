---
title: Creare viste personalizzate di oggetti di C++
description: Usare il framework Natvis per personalizzare il modo che Visual Studio visualizza i tipi nativi nel debugger
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f8ef28b453ba6c754c337c5d42581bd658be5f04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564416"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger"></a>Creare viste personalizzate di C++ oggetti nel debugger

Visual Studio *Natvis* framework consente di personalizzare la modalità di visualizzazione tipi nativi nelle finestre delle variabili del debugger, ad esempio le **variabili locali** e **Watch** windows e in **DataTips**. Visualizzazioni di Natvis consentono di rendere i tipi creati più evidente durante il debug.

Natvis sostituisce il *autoexp. dat* file nelle versioni precedenti di Visual Studio con la sintassi XML, funzionalità di diagnostica migliorate, controllo delle versioni e più file di supporto.

## <a name="BKMK_Why_create_visualizations_"></a>Visualizzazioni di Natvis

Utilizzare il framework Natvis per creare regole di visualizzazione per i tipi che si crea, in modo che gli sviluppatori possano vederli più facilmente durante il debug.

Ad esempio, la figura seguente mostra una variabile di tipo [TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) in una finestra del debugger senza applicata alcuna visualizzazione personalizzata.

![Visualizzazione predefinita di TextBox](../debugger/media/dbg_natvis_textbox_default.png "visualizzazione predefinita di TextBox")

La riga evidenziata mostra la proprietà `Text` della classe `TextBox` . La complessa gerarchia delle classi rende difficile trovare questa proprietà. Il debugger non riesce a interpretare il tipo di stringa personalizzato, è possibile visualizzare la stringa contenuta nella casella di testo.

Lo stesso `TextBox` sembra molto più semplice nella finestra delle variabili quando vengono applicate le regole di Natvis visualizzatore personalizzato. I membri importanti della classe di compaiono insieme e il debugger Mostra il valore di stringa sottostante del tipo di stringa personalizzato.

![Dati TextBox con uso del visualizzatore](../debugger/media/dbg_natvis_textbox_visualizer.png "dati TextBox con uso del Visualizzatore")

## <a name="BKMK_Using_Natvis_files"></a>Usare file natvis in progetti C++

Usa Natvis *natvis* file per specificare regole di visualizzazione. Oggetto *natvis* file è un file XML con un *natvis* estensione. Lo schema di Natvis è definito in *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

La struttura di base di un *natvis* file è uno o più `Type` gli elementi che rappresentano le voci di visualizzazione. Il nome completo della ognuno `Type` viene specificato nell'elemento relativo `Name` attributo.

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

Visual Studio fornisce alcuni *natvis* file con il *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* cartella. Questi file sono regole di visualizzazione per molti tipi comuni e possono essere usati come esempio per scrivere visualizzazioni per nuovi tipi.

### <a name="add-a-natvis-file-to-a-c-project"></a>Aggiungere un file natvis a un progetto C++

È possibile aggiungere un *natvis* file a qualsiasi progetto C++.

**Per aggiungere una nuova *natvis* file:**

1. Selezionare il nodo del progetto C++ in **Esplora soluzioni**e selezionare **Project** > **Aggiungi nuovo elemento**, o il progetto e scegliere **Add**   >  **Nuovo elemento**.

1. Nel **Aggiungi nuovo elemento** finestra di dialogo, seleziona **Visual C++** > **utilità** > **file di visualizzazione Debugger (. natvis)**.

1. Denominare il file e selezionare **Add**.

   Il nuovo file viene aggiunto a **Esplora soluzioni**e viene aperto nel riquadro di documento di Visual Studio.

Il debugger di Visual Studio carica *natvis* i file nei progetti C++ automaticamente e per impostazione predefinita, include anche nel *PDB* file quando si compila il progetto. Se si esegue il debug dell'app predefinito, il debugger carica le *natvis* del file dal *PDB* file, anche se non è presente il progetto aperto. Se non si vuole la *natvis* file incluso nel *PDB*, è possibile escluderlo dall'incorporato *PDB* file.

**Per escludere un *natvis* del file da un *PDB*:**

1. Selezionare il *natvis* del file in **Esplora soluzioni**e selezionare il **proprietà** icona, o il file e scegliere **proprietà**.

1. Elenco a discesa sulla freccia accanto a **escluso dalla compilazione** e selezionare **Yes**, quindi selezionare **OK**.

>[!NOTE]
>Per il debug di progetti eseguibili, usare gli elementi di soluzione per aggiungere uno qualsiasi *natvis* i file che non sono presenti il *PDB*, dal momento che non è disponibile alcun progetto C++.

>[!NOTE]
>Natvis regole caricate da un *PDB* si applicano solo ai tipi nei moduli che la *PDB* fa riferimento a. Ad esempio, se *Module1.pdb* ha una voce di Natvis per un tipo denominato `Test`, si applica solo al `Test` classe *Module1.dll*. Se un altro modulo definisce anche una classe denominata `Test`, il *Module1.pdb* la voce Natvis non si applica a esso.

### <a name="BKMK_natvis_location"></a> Percorsi dei file Natvis

È possibile aggiungere *natvis* file alla directory dell'utente o in una directory di sistema, se si vuole che vengano applicati a più progetti.

Il *natvis* i file vengono valutati nell'ordine seguente:

1. Eventuali *natvis* dei file incorporati in un *PDB* debug, a meno che non esiste un file con lo stesso nome del progetto caricato.

2. Eventuali *natvis* i file che si trovano in un progetto C++ caricato o una soluzione di primo livello. Questo gruppo include caricati tutti i progetti di C++, incluse le librerie di classi, ma non per i progetti in altri linguaggi.

::: moniker range="vs-2017"

3. La directory Natvis specifica dell'utente (ad esempio, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

3. La directory Natvis specifica dell'utente (ad esempio, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

4. La directory Natvis a livello di sistema (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Questa directory contiene il *natvis* file che vengono installati con Visual Studio. Se si dispone delle autorizzazioni di amministratore, è possibile aggiungere file a questa directory.

## <a name="modify-natvis-files-while-debugging"></a>Modificare i file natvis durante il debug

È possibile modificare un *natvis* file nell'IDE durante il debug di un progetto. Aprire il file nella stessa istanza di debug con Visual Studio, modificarlo e salvarlo. Non appena il file viene salvato, la **Watch** e **variabili locali** windows vengono aggiornati per riflettere la modifica.

È anche possibile aggiungere o eliminare *natvis* file in una soluzione che sta eseguendo il debug e Visual Studio aggiunge o rimuove le visualizzazioni pertinenti.

Non è possibile aggiornare *natvis* dei file incorporati nelle *PDB* file durante il debug.

Se si modifica il *natvis* file all'esterno di Visual Studio, le modifiche non diventano effettive automaticamente. Per aggiornare le finestre del debugger, è possibile riesaminare il **natvisreload** comando le **Watch** finestra. Quindi le modifiche diventano effettive senza riavviare la sessione di debug.

Usare anche il **natvisreload** comando per aggiornare il *natvis* file da una versione più recente. Ad esempio, il *natvis* file può essere verificato nel controllo del codice sorgente e si desidera visualizzare le modifiche recenti apportate da altri utenti.

## <a name="BKMK_Expressions_and_formatting"></a> Espressioni e formattazione
Nelle visualizzazioni Natvis si usano espressioni C++ per specificare gli elementi di dati da visualizzare. Oltre ai miglioramenti e alle limitazioni delle espressioni C++ nel debugger, che sono descritte nel [operatore di contesto (C++)](../debugger/context-operator-cpp.md), tenere presente quanto segue:

- Le espressioni di Natvis vengono valutate nel contesto dell'oggetto da visualizzare, non nello stack frame corrente. Ad esempio, `x` in un Natvis espressione fa riferimento a un campo denominato **x** nell'oggetto visualizzato, non a una variabile locale denominata **x** nella funzione corrente. È possibile accedere alle variabili locali nelle espressioni Natvis, anche se è possibile accedere a variabili globali.

- Le espressioni Natvis non consentono la valutazione di funzioni o effetti collaterali. Chiamate di funzioni e operatori di assegnazione vengono ignorati. Dal momento che le [funzioni intrinseche del debugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) non hanno effetti collaterali, possono essere chiamate liberamente da qualsiasi espressione Natvis, anche se non sono consentite altre chiamate di funzione.

- Per controllare la modalità di visualizzazione di un'espressione, è possibile usare uno qualsiasi degli identificatori di formato descritto nella [Format specifiers in C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Identificatori di formato vengono ignorati quando la voce viene usata internamente da Natvis, ad esempio la `Size` espressione in un [espansione di ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Visualizzazioni di Natvis

È possibile definire diverse visualizzazioni di Natvis per visualizzare i tipi in modi diversi. Ad esempio, ecco una visualizzazione dei `std::vector` che definisce una visualizzazione semplificata denominata `simple`. Il `DisplayString` e il `ArrayItems` elementi visualizzati nella vista predefinita e il `simple` visualizzazione, mentre il `[size]` e `[capacity]` gli elementi non vengono visualizzate nella `simple` visualizzazione.

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

Nel **Watch** finestra, utilizzare il **, visualizzazione** identificatore per specificare una visualizzazione alternativa di formato. Viene visualizzata la vista semplice come **vec,view(simple)**:

![Finestra Espressioni di controllo con visualizzazione semplice](../debugger/media/watch-simpleview.png "finestra Espressioni di controllo con visualizzazione semplice")

## <a name="BKMK_Diagnosing_Natvis_errors"></a> Errori di Natvis

Quando il debugger rileva errori in una voce di visualizzazione, li ignora. Visualizza il tipo nel relativo formato non elaborato o seleziona un'altra visualizzazione appropriata. È possibile usare la diagnostica di Natvis per capire il motivo per cui il debugger ignorata una voce di visualizzazione e per visualizzare la sintassi sottostante e gli errori di analisi.

**Per attivare la diagnostica di Natvis:**

- Sotto **degli strumenti** > **opzioni** (o **Debug** > **opzioni**) > **debug**  >  **Finestra di output**, impostare **messaggi di diagnostica Natvis (C++ solo)** al **errore**, **avviso** , oppure **Verbose**, quindi selezionare **OK**.

Gli errori vengono visualizzati nei **Output** finestra.

## <a name="BKMK_Syntax_reference"></a> Riferimento per la sintassi di Natvis

### <a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
L'elemento `AutoVisualizer` è il nodo radice del file *NATVIS* e contiene l'attributo `xmlns:` dello spazio dei nomi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Il `AutoVisualizer` elemento può avere [tipo](#BKMK_Type), [HResult](#BKMK_HResult), [elemento UIVisualizer](#BKMK_UIVisualizer), e [CustomVisualizer](#BKMK_CustomVisualizer) elementi figlio.

### <a name="BKMK_Type"></a> Elemento Type

Base `Type` simile in questo esempio:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Il `Type` elemento specifica:

1. Il tipo di visualizzazione deve essere utilizzato per (i `Name` attributo).

2. A quale valore di un oggetto di tale tipo deve essere simile (elemento `DisplayString` ).

3. I membri del tipo di aspetto quando l'utente espande il tipo in una finestra delle variabili (le `Expand` nodo).

#### <a name="templated-classes"></a>Classi basate su modelli
Il `Name` attributo del `Type` elemento accetta un asterisco `*` come un carattere jolly che può essere usato per i nomi delle classi basate su modelli.

Nell'esempio seguente viene utilizzata la stessa visualizzazione se l'oggetto è un `CAtlArray<int>` o un `CAtlArray<float>`. Se è presente una voce di visualizzazione specifici per un `CAtlArray<float>`, ha la precedenza su quella generica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

È possibile fare riferimento a parametri del modello nella voce di visualizzazione usando le macro $T1, $T2 e così via. Per esempi di queste macro, vedere i file *NATVIS* forniti con Visual Studio.

#### <a name="BKMK_Visualizer_type_matching"></a> Corrispondenza del tipo di visualizzatore
Se non è stato possibile convalidare una voce di visualizzazione, viene usata la successiva visualizzazione disponibile.

#### <a name="inheritable-attribute"></a>Attributo Inheritable
L'opzione facoltativa `Inheritable` attributo specifica se una visualizzazione si applica solo a un tipo di base o a un tipo di base e tutti i tipi derivati. Il valore predefinito di `Inheritable` è `true`.

Nell'esempio seguente, la visualizzazione si applica solo al `BaseClass` tipo:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attributo Priority

L'opzione facoltativa `Priority` attributo specifica l'ordine in cui si desidera usare le definizioni alternative, se una definizione non può essere analizzata. I possibili valori della `Priority` sono: `Low`, `MediumLow`,`Medium`, `MediumHigh`, e `High`. Il valore predefinito è `Medium`. Il `Priority` attributo consente di distinguere solo tra le priorità all'interno della stessa *natvis* file.

Nell'esempio seguente analizza innanzitutto la voce che corrisponde a STL 2015. Se il problema persiste analizzare, Usa la voce alternativa per la versione 2013 di STL:

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
È possibile inserire un `Optional` attributi su qualsiasi nodo. Se una sottoespressione all'interno di un nodo facoltativo non viene analizzata, il debugger ignora tale nodo, ma si applica il resto del `Type` regole. Nel tipo seguente `[State]` non è facoltativo, mentre `[Exception]` lo è.  Se `MyNamespace::MyClass` dispone di un campo denominato _`M_exceptionHolder`, entrambi i `[State]` nodo e il `[Exception]` sono visualizzati, ma se è non `_M_exceptionHolder` campo, solo il `[State]` nodo viene visualizzato.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> Attributo Condition

L'opzione facoltativa `Condition` attributo è disponibile per molti elementi di visualizzazione e consente di specificare quando utilizzare una regola di visualizzazione. Se l'espressione all'interno dell'attributo condition si risolve in `false`, non si applica la regola di visualizzazione. Se viene restituito `true`, o non è presente alcun `Condition` attributo, la visualizzazione si applica. È possibile usare questo attributo per la logica if-else nelle voci di visualizzazione.

Ad esempio, la visualizzazione seguente presenta due `DisplayString` elementi per un tipo di puntatore intelligente. Quando la `_Myptr` membro è vuoto, la condizione del primo `DisplayString` elemento si risolve in `true`, pertanto tale form è visualizzata. Quando la `_Myptr` membro non vuoto, la condizione viene valutata `false`, mentre la seconda `DisplayString` Visualizza elemento.

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

Il `IncludeView` e `ExcludeView` attributi specificano gli elementi da visualizzare o non visualizzare nelle visualizzazioni specifiche. Ad esempio, nella seguente Natvis specifica del `std::vector`, il `simple` vista non viene visualizzato il `[size]` e `[capacity]` elementi.

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

È possibile usare la `IncludeView` e `ExcludeView` attributi sui tipi e sui singoli membri.

### <a name="BKMK_Versioning"></a> Elemento Version
Il `Version` elemento definisce l'ambito di una voce di visualizzazione per un modulo specifico e una versione. Il `Version` elemento consente di evitare conflitti di nomi, riduce mancate corrispondenze indesiderate e consente di visualizzazioni diverse per le versioni di tipo diverso.

Se un file di intestazione comune usato da moduli diversi definisce un tipo, la visualizzazione con versione viene visualizzato solo quando il tipo è nella versione del modulo specificato.

Nell'esempio seguente, la visualizzazione è valida solo per i `DirectUI::Border` trovare il tipo nel `Windows.UI.Xaml.dll` dalla versione 1.0 alla 1.5 del file.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

### <a name="BKMK_DisplayString"></a> Elemento DisplayString
Il `DisplayString` elemento specifica una stringa da visualizzare come valore di una variabile. Accetta stringhe arbitrarie combinate con espressioni. Tutto ciò che è racchiuso tra parentesi graffe viene interpretato come un'espressione. Ad esempio, quanto segue `DisplayString` voce:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Indica che le variabili di tipo `CPoint` visualizzato come in questa illustrazione:

 ![Usare un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "usare un elemento DisplayString")

Nel `DisplayString` espressione `x` e `y`, che sono membri di `CPoint`, sono racchiusi tra parentesi graffe, pertanto i relativi valori vengono valutati. Nell'esempio viene inoltre illustrato come è possibile una parentesi graffa usando doppie parentesi graffe ( `{{` o `}}` ).

> [!NOTE]
> L'elemento `DisplayString` è l'unico elemento che accetta stringhe arbitrarie e la sintassi con parentesi graffe. Tutti gli altri elementi di visualizzazioni accettano solo espressioni può valutare il debugger.

### <a name="BKMK_StringView"></a> Elemento StringView

Il `StringView` elemento definisce un valore che il debugger può inviare al Visualizzatore di testo incorporato. Si consideri ad esempio la visualizzazione seguente per il `ATL::CStringT` tipo:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Il `CStringT` oggetto venga visualizzato in una finestra delle variabili simile all'esempio:

![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "elemento CStringT DisplayString")

Aggiunta di un `StringView` elemento indica al debugger può visualizzare il valore come una visualizzazione di testo.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante il debug, è possibile selezionare l'icona della lente di ingrandimento accanto alla variabile e quindi selezionare **Visualizzatore di testo** per visualizzare la stringa che **m_pszData** punta a.

 ![Dati CStringT con Visualizzatore StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "dati CStringT con Visualizzatore StringView")

L'espressione `{m_pszData,su}` include un identificatore di formato C++ **unità di streaming**, per visualizzare il valore come stringa Unicode. Per altre informazioni, vedere [Format specifiers in C++](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a> Espandere l'elemento

L'opzione facoltativa `Expand` nodo consente di personalizzare gli elementi figlio di un tipo visualizzato quando si espande il tipo in una finestra delle variabili. Il `Expand` nodo accetta un elenco di nodi figlio che definiscono gli elementi figlio.

- Se un `Expand` nodo non è specificato in una voce di visualizzazione, gli elementi figlio usano le regole di espansione predefinite.

- Se un `Expand` nodo viene specificato senza nodi figlio sotto di esso, il tipo non è espandibile nelle finestre del debugger.

#### <a name="BKMK_Item_expansion"></a> Espansione di Item

 Il `Item` elemento più comuni e di base in un `Expand` nodo. `Item` definisce un singolo elemento figlio. Ad esempio, un `CRect` classe con campi `top`, `left`, `right`, e `bottom` ha la seguente voce di visualizzazione:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Nella finestra del debugger, il `CRect` tipo è simile a questo esempio:

![CRect con espansione dell'elemento Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con espansione dell'elemento Item")

Il debugger valuta le espressioni specificate nel `Width` e `Height` gli elementi che mostra i valori nel **valore** colonna della finestra delle variabili.

Il debugger crea automaticamente il **[visualizzazione non elaborata]** nodo per ogni espansione personalizzata. Lo screenshot precedente consente di visualizzare il **[visualizzazione non elaborata]** nodo è espanso per mostrare come la visualizzazione non elaborata predefinito dell'oggetto è diverso dalla relativa visualizzazione Natvis. L'espansione predefinita crea un sottoalbero per la classe di base ed elenca tutti i membri dati della classe di base come elementi figlio.

> [!NOTE]
> Se l'espressione dell'elemento item punta a un tipo complesso, il **elemento** stesso nodo è espandibile.

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
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

![std:: Vector con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: Vector con espansione ArrayItems")

Il `ArrayItems` nodo deve avere:

- Un'espressione `Size` (che deve restituire un numero intero) per consentire al debugger di riconoscere la lunghezza della matrice.
- Oggetto `ValuePointer` espressione che punta al primo elemento (che deve essere un puntatore di un tipo di elemento non `void*`).

Il valore predefinito del limite inferiore della matrice è 0. Per sostituire il valore, usare un `LowerBound` elemento. Il *natvis* file forniti con Visual Studio sono esempi.

>[!NOTE]
>È possibile usare la `[]` operatore, ad esempio `vector[i]`, con qualsiasi visualizzazione matrice unidimensionale che usa `ArrayItems`, anche se il tipo stesso (ad esempio `CATLArray`) non supporta questo operatore.

È anche possibile specificare matrici multidimensionali. In tal caso, il debugger richiede leggermente più informazioni per visualizzare correttamente gli elementi figlio:

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

- `Direction` Specifica se la matrice è nell'ordine di riga o colonna ordinata.
- `Rank` specifica l'ordine di priorità della matrice.
- L'elemento `Size` accetta il parametro `$i` implicito che sostituisce con l'indice delle dimensioni per individuare la lunghezza della matrice in quella dimensione. Nell'esempio precedente, l'espressione `_M_extent.M_base[0]` deve fornire la lunghezza della dimensione 0, `_M_extent._M_base[1]` il 1 ° e così via.

Ecco come un oggetto bidimensionale `Concurrency::array` oggetto esegue la ricerca nella finestra del debugger:

![Matrice bidimensionale con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "matrice bidimensionale con espansione ArrayItems")

#### <a name="BKMK_IndexListItems_expansion"></a> Espansione di IndexListItems

È possibile usare `ArrayItems` espansione solo se gli elementi della matrice vengono disposti in modo contiguo nella memoria. Il debugger ottiene l'elemento successivo semplicemente incrementando il relativo puntatore. Se è necessario modificare l'indice per il nodo di valore, usare `IndexListItems` nodi. Ecco una visualizzazione con un `IndexListItems` nodo:

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

L'unica differenza tra `ArrayItems` e `IndexListItems` è la `ValueNode`, che prevede l'espressione completa del<sup>th</sup> elemento con l'oggetto implicito `$i` parametro.

>[!NOTE]
>È possibile usare la `[]` operatore, ad esempio `vector[i]`, con qualsiasi visualizzazione matrice unidimensionale che usa `IndexListItems`, anche se il tipo stesso (ad esempio `CATLArray`) non supporta questo operatore.

#### <a name="BKMK_LinkedListItems_expansion"></a> Espansione di LinkedListItems

Se il tipo visualizzato rappresenta un elenco collegato, il debugger può visualizzarne i figli tramite un nodo `LinkedListItems` . La visualizzazione seguente per il `CAtlList` digitare Usa `LinkedListItems`:

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

Il debugger valuterà la `NextPointer` e `ValueNode` espressioni nel contesto del `LinkedListItems` nodo elemento, non il tipo di elenco padre. Nell'esempio precedente, `CAtlList` ha un `CNode` classe (trovato nel `atlcoll.h`) che rappresenta un nodo dell'elenco collegato. `m_pNext` e `m_element` sono campi di questa `CNode` (classe), non del `CAtlList` classe.

`ValueNode` può essere lasciato vuoto oppure usare `this` per fare riferimento al `LinkedListItems` stesso nodo.

#### <a name="customlistitems-expansion"></a>Espansione CustomListItems
L'espansione `CustomListItems` consente di scrivere una logica personalizzata per attraversare una struttura dei dati, ad esempio una tabella hash. Usare `CustomListItems` rientrano nel modello per visualizzare strutture di dati che è possono usare le espressioni C++ per tutto il necessario per valutare, ma non abbastanza `ArrayItems`, `IndexListItems`, o `LinkedListItems`.

Il Visualizzatore seguente per `CAtlMap` è un ottimo esempio in cui `CustomListItems` appropriato.

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

È possibile usare `Exec` per eseguire il codice all'interno di un `CustomListItems` espansione, usando le variabili e gli oggetti definiti nell'espansione. È possibile usare gli operatori logici, operatori aritmetici e gli operatori di assegnazione con `Exec`. Non è possibile usare `Exec` per valutare le funzioni.

`CustomListItems` supporta le funzioni intrinseche seguenti:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a> Espansione di TreeItems
 Se il tipo visualizzato rappresenta un albero, il debugger può esaminare l'albero e visualizzarne i figli tramite un nodo `TreeItems` . Di seguito è illustrata la visualizzazione per il `std::map` il tipo usando un `TreeItems` nodo:

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

La sintassi è simile al `LinkedListItems` nodo. `LeftPointer`, `RightPointer`, e `ValueNode` vengono valutate nel contesto della classe di nodo dell'albero. `ValueNode` può essere lasciato vuoto o usare `this` per fare riferimento al `TreeItems` stesso nodo.

#### <a name="BKMK_ExpandedItem_expansion"></a> Espansione di ExpandedItem
 Il `ExpandedItem` elemento genera una visualizzazione figlio aggregata visualizzando le proprietà dei membri di classi o dati di base come se fossero figli del tipo visualizzato. Il debugger valuta l'espressione specificata e aggiunge i nodi figlio del risultato all'elenco figlio del tipo visualizzato.

Ad esempio, il tipo di puntatore intelligente `auto_ptr<vector<int>>` generalmente vengono visualizzati come:

 ![automatico&#95;ptr&#60;vector&#60;int&#62; &#62; espansione predefinita](../debugger/media/dbg_natvis_expand_expandeditem_default.png "espansione predefinita")

 Per visualizzare i valori del vettore, è necessario eseguire il drill-down di due livelli nella finestra delle variabili, che attraversa il `_Myptr` membro. Aggiungendo un elemento `ExpandedItem`, è possibile eliminare la variabile `_Myptr` dalla gerarchia e visualizzare direttamente gli elementi del vettore:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![automatico&#95;ptr&#60;vector&#60;int&#62; &#62; espansione di ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "espansione di ExpandedItem")

Nell'esempio seguente mostra come aggregare proprietà dalla classe di base in una classe derivata. Si supponga che la classe `CPanel` derivi da `CFrameworkElement`. Anziché ripetere le proprietà che provengono dalla base `CFrameworkElement` (classe), il `ExpandedItem` visualizzazione nodo aggiunge tali proprietà all'elenco figlio del `CPanel` classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

In questo caso è necessario l'identificatore di formato **nd** che disattiva la corrispondenza della visualizzazione per la classe derivata. In caso contrario, l'espressione `*(CFrameworkElement*)this` provocherebbe il `CPanel` visualizzazione verrà applicato anche in questo caso, perché le regole di corrispondenza di tipo di visualizzazione predefinita considerarlo come quello più appropriato. Usare la **nd** per indicare al debugger di usare la visualizzazione della classe di base, o l'espansione predefinita se la classe di base non dispone di alcuna visualizzazione identificatore di formato.

#### <a name="BKMK_Synthetic_Item_expansion"></a> Espansione di elementi Synthetic
 Il nodo `ExpandedItem` esegue la funzione opposta rispetto all'elemento `Synthetic`, che fornisce una visualizzazione dei dati più semplice eliminando le gerarchie. Consente di creare un elemento figlio artificiale che non è un risultato di un'espressione. L'elemento artificiale può avere elementi figlio propri. Nell'esempio seguente nella visualizzazione del tipo `Concurrency::array` viene usato un nodo `Synthetic` per mostrare un messaggio di diagnostica all'utente:

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

 ![Concurrency:: array con espansione dell'elemento Synthetic](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: array con espansione dell'elemento Synthetic")

### <a name="BKMK_HResult"></a> Elemento HResult
 Il `HResult` elemento consente di personalizzare le informazioni visualizzate per un **HRESULT** nelle finestre del debugger. L'elemento `HRValue` deve contenere il valore a 32 bit di **HRESULT** da personalizzare. Il `HRDescription` elemento contiene le informazioni da visualizzare nella finestra del debugger.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a> Elemento UIVisualizer
Un elemento `UIVisualizer` consente di registrare un plug-in del visualizzatore grafico con il debugger. Un visualizzatore grafico consente di creare una finestra di dialogo o un'altra interfaccia che viene illustrata una variabile o un oggetto in modo coerente con il tipo di dati. Il visualizzatore plug-in deve essere creato come un [VSPackage](../extensibility/internals/vspackages.md)e deve esporre un servizio di cui è possibile utilizzare il debugger. Il *natvis* file contiene informazioni di registrazione per il plug-in, ad esempio il nome, il GUID del servizio esposto e i tipi che è possibile visualizzare.

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

- Oggetto `ServiceId`  -  `Id` coppia attributo identifica un `UIVisualizer`. Il `ServiceId` è il GUID del servizio del Visualizzatore espone pacchetto. `Id` è un identificatore univoco che distingue i visualizzatori, se un servizio fornisce più di uno. Nell'esempio precedente, lo stesso servizio Visualizzatore fornisce due visualizzatori.

- Il `MenuName` attributo definisce un nome di Visualizzatore per visualizzare nell'elenco a discesa accanto all'icona della lente di ingrandimento nel debugger. Ad esempio:

  ![Menu di scelta rapida UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "menu di scelta rapida UIVisualizer")

Ogni tipo definito nel *natvis* file deve elencare esplicitamente qualsiasi visualizzatori dell'interfaccia utente possono visualizzarlo. Il debugger abbina i riferimenti del Visualizzatore nelle voci dei tipi con i visualizzatori registrati. Ad esempio, seguente tipo di voce per `std::vector` riferimenti di `UIVisualizer` nell'esempio precedente.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 È possibile vedere un esempio di un `UIVisualizer` nella [espressioni di controllo immagine](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) estensione utilizzata per visualizzare le bitmap in memoria.

### <a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer` è un punto di estendibilità che specifica un'estensione VSIX che è scrivere per controllare visualizzazioni in Visual Studio code. Per altre informazioni sulla scrittura di estensioni VSIX, vedere la [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

È molto maggiore impegno per scrivere un visualizzatore personalizzato rispetto a una definizione Natvis XML, ma è possibile attribuire vincoli su ciò che Natvis o non supporta. I visualizzatori personalizzati hanno accesso al set completo di estendibilità del debugger API, che possono eseguire query e modificare il processo oggetto del debug o comunicare con altre parti di Visual Studio.

 È possibile usare la `Condition`, `IncludeView`, e `ExcludeView` gli attributi `CustomVisualizer` elementi.